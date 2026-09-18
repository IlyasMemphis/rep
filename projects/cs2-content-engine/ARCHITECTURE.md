# Target Architecture

## Principle

Do not make an LLM operate a video editor by visually clicking the UI for every edit.

Prefer:

**event -> analysis -> structured edit plan -> deterministic renderer -> QC -> publish**

## Current cost constraint

Phase 1 must run without separate OpenAI API billing.

Use the ChatGPT Plus subscription and ChatGPT-authenticated Codex local tooling wherever possible. Do not require an OpenAI API key, API credit balance, or separate card-funded token billing for the initial system.

The architecture therefore has two layers:

1. **Plus-only local mode (current target)** — local orchestrator + Codex App Server/SDK authenticated with the user's ChatGPT account, deterministic local tools, synced folders and project files.
2. **API/cloud mode (optional future upgrade)** — Agents API or other paid API services only if/when their extra autonomy clearly justifies the cost.

The project must remain useful even if API/cloud mode is never enabled.

## Target pipeline

```text
RAW MATCH
   |
   v
Google Drive / ingest inbox
   |
   v
Trigger + job creation
   |
   +--> media probe / checksum / proxy generation
   +--> transcript + timestamps + speaker/source data
   +--> FACEIT match identification + stats
   |
   v
Video intelligence
   |
   v
Editorial reasoning
   |
   v
edit_plan.json
   |
   v
Codex / local execution agent
   |
   +--> FFmpeg / Remotion / timeline tooling
   +--> subtitles
   +--> audio mix
   +--> long-form render
   +--> short-form candidates
   |
   v
Automated technical QC
   |
   v
Editorial AI review
   |
   +--> patch plan if needed --> re-render
   |
   v
Approved assets
   |
   +--> thumbnail candidates
   +--> title / description / metadata
   +--> publish queue
   |
   v
YouTube / TikTok / other supported distribution
   |
   v
Analytics + creator feedback
   |
   v
Style / decision system improves
```

## Plus-only orchestration path

For the first implementation, avoid requiring Agents API.

Preferred local path:

```text
Google Drive Desktop / local ingest folder
        |
        v
filesystem watcher
        |
        v
local Node.js/Python orchestrator
        |
        +--> Codex App Server / SDK
        |      authenticated with ChatGPT Plus
        |
        +--> persistent Director thread
        +--> persistent Worker thread
        +--> deterministic scripts/tools
        |
        v
job state + artifacts on disk / Git
```

The local orchestrator may start/resume Codex threads programmatically. The ordinary ChatGPT UI is not treated as a programmable daemon and should not be automated through fragile UI clicking.

Deep human-in-the-loop editorial work can still happen in ChatGPT Chat/Work during calibration, but unattended Plus-only execution should be centered on Codex local tooling.

## Roles

### Ilyas

- creates authentic gameplay;
- speaks naturally and plays normally;
- uploads/marks worthwhile matches;
- provides taste feedback during calibration.

### ChatGPT / editorial reasoning layer

- maintains project intent;
- reasons about narrative and context;
- evaluates whether a scene is useful, funny, educational, tense or redundant;
- produces or reviews structured editorial decisions;
- performs high-level QC;
- updates project rules from creator feedback.

In Plus-only mode, the unattended implementation of this role may be represented by a dedicated persistent Codex thread with Director instructions, while ChatGPT Chat/Work remains available for higher-level calibration and review.

### Video-understanding layer

Acts as eyes/ears over long recordings.

It should help locate and describe:

- rounds/events;
- speech;
- strategic explanations;
- kills/clutches;
- reactions;
- humour;
- dead time;
- candidate hooks and short-form segments.

### Codex / local execution agent

Acts as the hands/engineer.

Responsibilities should include:

- installing/configuring approved tools;
- inspecting local media/device state;
- executing deterministic edit/render pipelines;
- validating outputs;
- maintaining scripts/configuration;
- avoiding unnecessary expensive reasoning over raw media when a structured plan already exists.

### Deterministic media layer

Likely tools:

- FFmpeg for probing, cutting, encoding and audio processing;
- Remotion for programmatic graphics/compositions where useful;
- OpenTimelineIO or an equivalent neutral timeline representation if it improves portability;
- optional DaVinci Resolve integration later where a professional NLE adds real value.

No tool choice is final until tested.

## Job state model

Candidate lifecycle:

```text
DISCOVERED
INGESTING
INGESTED
ANALYZING
EDIT_PLANNED
PROXY_RENDERED
QC_REVIEW
REVISION_REQUIRED
MASTER_RENDERED
APPROVED
SCHEDULED
PUBLISHED
ARCHIVED
```

Failures must be explicit and recoverable, not silently skipped.

## Editing semantics

A highlight is not only a kill.

Candidate dimensions include:

- mechanical value;
- strategic value;
- teaching value;
- personality;
- humour;
- tension;
- payoff;
- context required;
- narrative dependency;
- short-form potential.

The system should preserve causal sequences such as:

```text
call / prediction -> setup -> execution -> payoff -> reaction
```

when they are more valuable than the isolated action.

## Quality loop

Full autonomy is not the first milestone.

Early videos should be generated automatically but reviewed by Ilyas. Every correction should become structured feedback.

The goal is to reduce manual intervention as the style model becomes better calibrated.

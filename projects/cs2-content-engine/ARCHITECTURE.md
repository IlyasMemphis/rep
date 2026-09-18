# Target Architecture

## Principle

Do not make an LLM operate a video editor by visually clicking the UI for every edit.

Prefer:

**event -> analysis -> structured edit plan -> deterministic renderer -> QC -> publish**

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

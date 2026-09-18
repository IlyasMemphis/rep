# Decisions and Open Questions

## Accepted directions

### D-001 — The project is an autonomous content system, not merely an AI clipper

The project covers capture, analysis, editorial planning, rendering, QC, metadata, publication workflow, retention and feedback.

### D-002 — Source authenticity is the product

The system must preserve real gameplay, live decisions, communication and personality. It should not manufacture generic montage energy that was not present.

### D-003 — Capture audio sources separately whenever technically possible

Required logical sources:
- CS2/game audio;
- Ilyas microphone;
- FACEIT party voice from Chrome.

### D-004 — Structured edit plans before rendering

The reasoning layer should create machine-readable editorial decisions. Rendering should be deterministic and reproducible.

### D-005 — Git/project files are the durable source of truth

Important project context must not depend on one ChatGPT conversation. Project docs, schemas, decisions and feedback are versioned.

### D-006 — Calibrate taste before enabling unattended publishing

The first objective is to prove that the system can consistently make a video Ilyas would willingly upload.

### D-007 — Keep derived project data even if large raw recordings are later removed

At minimum preserve:
- final exports;
- transcript/timestamps;
- FACEIT match data;
- analysis;
- edit plan;
- subtitles;
- thumbnail source/metadata;
- QC result;
- publication metadata;
- feedback.

### D-008 — Phase 1 must not require separate OpenAI API billing

Date: 2026-09-18.

Current hard constraint: use the existing ChatGPT Plus subscription and do not require a separately billed OpenAI API account, token balance, or additional card-funded usage.

Implications:
- Codex should authenticate through the ChatGPT account where supported.
- Prefer Codex App Server/SDK and local orchestration over Agents API for Phase 1.
- ChatGPT Work/Codex included usage is a finite shared allowance, so tasks must be token/turn efficient.
- Agents API remains an optional future architecture upgrade rather than a dependency.
- Avoid browser/UI automation of ChatGPT as the core bridge; it is fragile and unnecessary for local Codex automation.
- The project must retain a useful manual/semiautomated fallback when included plan limits are temporarily exhausted.

## Open questions

### OQ-001 — Exact OBS/capture configuration

Needs current research + local inspection + performance A/B test.

### OQ-002 — Best way to isolate FACEIT party voice in Chrome

Need to validate Windows/OBS per-application audio routing and confirm FACEIT voice behaviour. Avoid unnecessary virtual-audio complexity if native application capture works.

### OQ-003 — Recording quality vs competitive overhead

Need empirical OFF/ON frametime measurements on Ilyas's actual CS2 machine.

### OQ-004 — Exact long-form editorial style

Will be learned through reference research plus calibration on real matches, not guessed before seeing footage.

### OQ-005 — Raw retention window

Do not delete after a fixed number of days until successful render, upload verification and backup/retention policy are implemented.

### OQ-006 — Publishing autonomy

Start with draft/private/scheduled output or explicit approval during calibration. Increase autonomy only after the error rate is low enough.

### OQ-007 — How far can Plus-only unattended orchestration go before plan allowance becomes the bottleneck?

Measure real usage per match before considering any paid API path. Optimize with deterministic preprocessing, cheap/local analysis, compact state files, and limited agent iterations.

## Change rule

When a meaningful project assumption changes, add a dated decision here instead of silently replacing the old reasoning.

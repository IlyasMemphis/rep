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

## Change rule

When a meaningful project assumption changes, add a dated decision here instead of silently replacing the old reasoning.

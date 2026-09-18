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

### D-009 — Codex is a bounded execution resource, not the primary reasoning budget

Date: 2026-09-18.

ChatGPT/editorial reasoning should prepare explicit instructions and durable project state. Codex should primarily execute well-specified technical work.

The local orchestrator must read live ChatGPT/Codex rate-limit state before expensive jobs where supported and stop at recoverable boundaries when the included allowance becomes constrained.

The default worker model is selected by measured reliability per unit of included allowance, not by prestige. GPT-5.5 low reasoning is an allowed temporary baseline while available, but the system must not depend on it because ChatGPT-authenticated GPT-5.5 is scheduled for retirement on 2026-10-14.

### D-010 — New chats bootstrap from a deterministic repository entry point

Date: 2026-09-18.

A new ChatGPT/Work/Codex session is not assumed to automatically read GitHub.

`START_HERE.md` is the canonical bootstrap entry point. A new session should be told to open it; that file defines the minimum authoritative read order.

This avoids giant master prompts and avoids depending on implicit chat-memory behaviour.

### D-011 — General personal context requires a separate private store

Date: 2026-09-18.

The current `IlyasMemphis/rep` repository is public and must not become a life-log or personal database.

Cross-topic durable context should live in a separate private repository with an inbox + curated-domain structure. Secrets and highly sensitive material remain excluded by default even from a private Git repository.

See `PERSONAL_KB_PLAN.md`.

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

### OQ-008 — Which low-cost worker model gives the best reliability/allowance ratio?

Benchmark representative tasks instead of guessing. Include GPT-5.5 low reasoning while available and GPT-5.6 Luna/Terra candidates.

## Change rule

When a meaningful project assumption changes, add a dated decision here instead of silently replacing the old reasoning.

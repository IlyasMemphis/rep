# Backlog

## Phase 1 — Capture baseline (NEXT)

- [ ] Inspect current Windows build, GPU driver, CS2 capture environment and audio endpoints.
- [ ] Research current stable OBS build and known CS2/FACEIT capture constraints.
- [ ] Install OBS Studio from an official source if not already installed.
- [ ] Create a dedicated CS2 recording profile/scene collection.
- [ ] Capture CS2 video reliably.
- [ ] Separate CS2/game audio.
- [ ] Separate HyperX Cloud III Wired microphone.
- [ ] Separate Chrome/FACEIT party voice.
- [ ] Choose recording container/codec/quality after testing rather than guessing.
- [ ] Configure file naming and destination.
- [ ] Run short recording validation.
- [ ] Verify tracks with ffprobe.
- [ ] Check A/V sync.
- [ ] Measure gameplay impact: recording OFF vs ON.
- [ ] Save/export capture configuration into the project.
- [ ] Record one full test match.

### Phase 1 exit condition

One complete match exists with:
- good video quality;
- independent logical audio sources;
- stable sync;
- no meaningful competitive-performance regression;
- repeatable recording procedure.

## Phase 1.5 — Plus-only agent bridge

Build only after the capture baseline is proven.

- [ ] Install/configure Codex App Server locally using ChatGPT account authentication, not API billing.
- [ ] Implement `account/read` sanity check and confirm plan/auth mode.
- [ ] Implement `account/rateLimits/read` and persist current quota-window state.
- [ ] Subscribe to rate-limit updates if useful.
- [ ] Implement job budget guardrails from `MODEL_BUDGET.md`.
- [ ] Create persistent Director and Worker thread IDs.
- [ ] Implement thread resume after restart.
- [ ] Implement structured Director -> Worker -> Director handoff.
- [ ] Implement job checkpoints so a usage-limit reset never corrupts work.
- [ ] A/B representative worker tasks on GPT-5.5 low reasoning vs GPT-5.6 Luna; measure reliability and allowance consumption.
- [ ] Select cheapest sufficient default worker model from evidence.
- [ ] Remove any durable dependency on GPT-5.5 before 2026-10-14.
- [ ] Build a minimal test: drop `TEST.mp4` into inbox -> watcher -> worker -> `report.json`, with zero manual clicks after file placement.

### Phase 1.5 exit condition

A local Plus-authenticated automation can detect one test file, inspect current Codex allowance, execute a bounded worker task, persist the result, and recover cleanly from interruption without an OpenAI API key.

## Phase 2 — One-match intelligence prototype

- [ ] Ingest one full match.
- [ ] Generate proxy/media manifest.
- [ ] Transcribe speech with timestamps.
- [ ] Associate recording with FACEIT match/stats.
- [ ] Produce structured scene/round/event index.
- [ ] Generate first editorial analysis.
- [ ] Create `edit_plan.json`.
- [ ] Review whether the plan understands context, not only kills.

## Phase 3 — Deterministic renderer

- [ ] Define edit-plan JSON schema.
- [ ] Implement cut/assembly pipeline.
- [ ] Implement audio mix rules.
- [ ] Implement subtitles.
- [ ] Render long-form proxy.
- [ ] Produce technical QC report.
- [ ] Render master.

## Phase 4 — Editorial calibration

- [ ] Review multiple real matches with Ilyas.
- [ ] Capture every correction as structured feedback.
- [ ] Build style bible.
- [ ] Build keep/remove examples.
- [ ] Define cold-open and pacing rules from evidence.
- [ ] Establish long-form vs Shorts selection logic.

## Phase 5 — Short-form / packaging

- [ ] Generate Shorts/TikTok/Reels candidates with self-contained narrative.
- [ ] Build native-looking thumbnail system based primarily on real match imagery.
- [ ] Ground titles in real match statistics.
- [ ] Generate descriptions/metadata.
- [ ] Create candidate packaging variants for testing.

## Phase 6 — Event-driven automation

- [ ] Drive ingest folder.
- [ ] File-complete detection.
- [ ] Job database/state machine.
- [ ] Idempotency and retry rules.
- [ ] Local worker/Codex execution bridge.
- [ ] QC loop.
- [ ] Render/archive folders.
- [ ] Notifications.

## Phase 7 — Publishing / analytics

- [ ] YouTube integration.
- [ ] TikTok integration subject to platform/API requirements.
- [ ] Scheduling queue.
- [ ] Publication verification.
- [ ] Channel analytics ingestion.
- [ ] Feedback loop from CTR, retention and viewer behaviour.
- [ ] Safe raw-retention cleanup.

## Parallel infrastructure — Private personal context

This is separate from the public CS2 project repository.

- [ ] Create a private GitHub repository for cross-topic durable personal context.
- [ ] Add private-repo `START_HERE.md` and `INDEX.md`.
- [ ] Add domain files only as needed.
- [ ] Keep secrets and highly sensitive material out by default.
- [ ] Establish an inbox -> curated-state consolidation workflow.
- [ ] Define a minimal new-chat bootstrap phrase for reading only relevant domain context.

## Principle

Do not jump ahead merely because later phases are exciting. Validate the highest-uncertainty component before investing heavily in automation around it.

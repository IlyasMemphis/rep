# Model and Allowance Budget Policy

## Objective

Codex is primarily the execution layer. Expensive reasoning should not be spent on work that can be specified by ChatGPT, deterministic code or structured project state.

The system must remain usable on the existing ChatGPT Plus subscription without separate OpenAI API billing.

## Current constraint — 2026-09-18

ChatGPT Work and Codex share included plan allowance with a five-hour usage window and a weekly limit. Consumption depends on model, task complexity and reasoning effort.

The orchestrator must treat included allowance as a scarce runtime resource.

## Live limit awareness

When using Codex App Server with ChatGPT authentication, read account limits before expensive jobs:

- `account/rateLimits/read`;
- observe each returned bucket;
- record `usedPercent`, `windowDurationMins` and `resetsAt`;
- subscribe to `account/rateLimits/updated` where useful;
- handle `UsageLimitExceeded` as a recoverable paused state, never as job corruption.

The exact bucket names/windows returned by the service are authoritative. Do not hardcode assumptions that every account exposes identical buckets.

## Initial budget guardrails

These thresholds are project defaults, not OpenAI limits, and should be tuned from real measurements:

- < 60% used: normal work allowed;
- 60–75%: avoid unnecessary re-analysis and optional iterations;
- 75–90%: finish active jobs only; do not begin a heavy new match-analysis/render-orchestration cycle;
- >= 90%: deterministic/local work only unless a tiny Codex action is required to safely checkpoint;
- limit reached: persist state and resume after reset; do not loop/retry wastefully.

Always consider both the short window and weekly allowance if both are exposed.

## Worker model strategy

### Current familiar baseline

Ilyas has historically used GPT-5.5 with low/light reasoning as a low-cost executor and has found this practical.

Do not increase reasoning effort by default.

### Important migration fact

GPT-5.5 with ChatGPT authentication is scheduled for retirement from ChatGPT/Work/Codex on 2026-10-14. Therefore no durable automation may depend exclusively on `gpt-5.5`.

### Candidate hierarchy

Use empirical reliability + allowance consumption, not model prestige.

1. **GPT-5.6 Luna** — first candidate for simple, explicit, deterministic execution and short tool tasks.
2. **GPT-5.5 low reasoning** — temporary familiar baseline while still available; useful for A/B comparison before retirement.
3. **GPT-5.6 Terra** — escalate for multi-step coding/tool tasks where Luna is unreliable.
4. **GPT-5.6 Sol** — reserve for genuinely difficult engineering/reasoning.
5. **GPT-6 Astra** — never default for worker execution; use only when the expected value clearly exceeds the allowance cost.

Run a small A/B benchmark on representative project tasks before permanently choosing the default worker model.

## Fast mode

Do not use accelerated/fast model mode for ordinary project automation unless explicitly justified. It consumes substantially more included usage for supported models.

## Turn discipline

A worker request should contain:

- the exact goal;
- exact files/paths;
- allowed tools/actions;
- constraints;
- acceptance tests;
- expected structured result.

The worker should not rediscover the project, brainstorm broad architecture or restate long context when the Director already made the decision.

Prefer one high-quality execution turn plus deterministic validation over many conversational turns.

## State discipline

Before any long task:

1. persist job state;
2. persist inputs/plan;
3. read rate limits;
4. estimate whether the task can safely start;
5. execute;
6. checkpoint after meaningful milestones;
7. if allowance becomes constrained, stop at a recoverable boundary.

No job should depend on one uninterrupted Codex session to remain valid.

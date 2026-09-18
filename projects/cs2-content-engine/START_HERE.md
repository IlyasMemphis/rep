# START HERE — CS2 Autonomous Content Engine

This file is the deterministic entry point for any new ChatGPT, Work or Codex session.

## New-session rule

Do not rely on chat history alone.

Before making project-level decisions, read these files in order:

1. `PROJECT.md` — goal, product identity and current phase.
2. `DECISIONS.md` — accepted architectural/product decisions and open questions.
3. `MODEL_BUDGET.md` — Codex/Work allowance policy and model escalation rules.
4. `CAPTURE.md` — current capture requirements.
5. `ARCHITECTURE.md` — system architecture and responsibility boundaries.
6. `BACKLOG.md` — current next actions.
7. `AGENTS.md` — execution rules for agents.
8. Relevant dated notes under `ideas/` only when historical reasoning is needed.

Repository state is the durable project source of truth. If remembered chat context conflicts with repository state, surface the conflict instead of silently choosing one.

## Minimal prompt for a new ChatGPT chat

Use:

> Open the connected GitHub repository `IlyasMemphis/rep`, read `projects/cs2-content-engine/START_HERE.md` and the files it requires, then continue the CS2 Autonomous Content Engine from its current state. Treat the repository as the durable source of truth and update it when we make durable decisions.

This is intentionally short so a new chat does not require a giant pasted master prompt.

## Documentation contract

When a conversation produces a durable project change, record it in the appropriate file:

- new product/architecture decision -> `DECISIONS.md`;
- new workflow rule -> relevant workflow file;
- new agent behaviour -> `AGENTS.md`;
- next work item -> `BACKLOG.md`;
- creator taste feedback -> future `feedback/`;
- unprocessed but potentially important idea -> `ideas/YYYY-MM-DD-*.md`.

Do not turn the repository into a verbatim transcript dump. Preserve high-signal ideas, decisions, hypotheses, constraints, experiments, results and unresolved questions.

## Privacy boundary

This repository is currently public.

Do not store general personal-life context, secrets, credentials, identity documents, private account data, sensitive health information or other private material here.

A separate private personal knowledge repository should be used for cross-topic life context. See `PERSONAL_KB_PLAN.md`.

# Private Personal Knowledge Base Plan

## Why this is separate

The CS2 content-engine repository is project-specific and currently public.

Ilyas also wants durable cross-chat context for broader life and work: PC/CS2 tuning, networking, career, vehicles, purchases, administrative processes, projects, ideas and other recurring topics.

That context must not be mixed into a public repository.

## Target

Create a separate **private GitHub repository** dedicated to durable personal context.

Working name:

`ilyas-context`

The exact name is not important; privacy is.

## Proposed structure

```text
START_HERE.md
INDEX.md
inbox/
  YYYY-MM-DD.md
domains/
  pc-gaming.md
  network-internet.md
  career-learning.md
  vehicles.md
  purchases.md
  admin-germany.md
projects/
  <project-name>/
decisions/
experiments/
archive/
```

## Capture model

Do not archive every sentence of every chat.

Capture durable information in two stages:

1. **Inbox** — timestamped high-signal ideas, observations, hypotheses and changes with minimal interpretation.
2. **Curated domain state** — periodically consolidate confirmed facts, current configuration, decisions, outcomes and unresolved questions into the appropriate domain file.

This preserves ideas without letting the knowledge base become an unusable transcript dump.

## Suggested record types

Each durable note should identify its type where practical:

- FACT — directly confirmed current state;
- SOURCE_CLAIM — statement from an external/person source;
- OBSERVATION — something Ilyas directly observed;
- HYPOTHESIS — plausible explanation not yet verified;
- DECISION — chosen direction;
- EXPERIMENT — test + before/after result;
- TODO — actionable unresolved item;
- IDEA — potentially useful concept not yet validated.

## Privacy policy

Never commit:

- passwords, recovery codes or authentication tokens;
- payment-card/bank credentials;
- government-document scans;
- raw identity-verification material;
- private third-party secrets;
- highly sensitive personal data unless Ilyas explicitly decides it belongs there and understands the implications.

For especially sensitive categories, prefer a more appropriate private store rather than Git even if the repository itself is private.

## New-chat bootstrap

The private repository should have its own `START_HERE.md`.

When a new chat concerns a specific topic, ChatGPT should read only the relevant domain/project files rather than ingesting the entire personal knowledge base. This keeps context precise and cheap.

Example:

> Read my connected private context repository's START_HERE.md and the PC/gaming domain state, then continue this issue from the documented current state.

## Automation goal

Long term, a documentation pass should run whenever a conversation produces durable new information.

Current ChatGPT conversations do not automatically commit every message to GitHub by default. Until a safe event-driven bridge exists, the assistant should update connected project/context repositories during the conversation when the user has asked for this and the information is appropriate to store.

## Status

Plan only. A private repository is required before personal-life records are written.

The currently connected GitHub tool in this session can edit existing repositories but does not expose repository creation/visibility management, so creation of the private repository must happen through GitHub itself or later through a local authenticated GitHub CLI/Codex step.

# Night-session follow-up — budget and durable context

Date: 2026-09-18

## Raw idea distilled

Ilyas wants ChatGPT to remain the high-reasoning/project brain and Codex to function primarily as low-cost hands.

Reasoning:
- Codex/Work has a fast-consuming five-hour allowance plus a weekly allowance.
- Heavy models can consume the short window before meaningful execution finishes.
- Ilyas historically uses GPT-5.5 with low/light reasoning because he prepares detailed prompts in ChatGPT first.
- The desired architecture should therefore minimize Codex thinking, make worker prompts explicit, and protect the short usage window so a job does not start and then stall halfway through.
- New durable ideas from project conversations should be committed to the project source of truth instead of remaining only in chat context.

## New cross-topic idea

Ilyas also wants a broader personal knowledge system so recurring context does not have to be re-explained across unrelated chats.

Examples of desired domains:
- PC / CS2 / Fortnite state and experiments;
- network / ISP / routing;
- career and learning;
- vehicles;
- purchases / equipment;
- administrative processes;
- ongoing projects;
- ideas and hypotheses.

This must not be implemented by dumping private life data into the current public repository.

Target direction:
- separate private repository;
- timestamped inbox for high-signal ideas/changes;
- curated domain files for current state;
- deterministic START_HERE entry point for new chats;
- only relevant domain context loaded for each conversation.

## Important current facts

- The current project repository `IlyasMemphis/rep` is public.
- The connected GitHub integration in this session can edit existing repositories but does not expose repository creation/visibility management.
- A separate private repository should be created before storing general personal context.
- GPT-5.5 is transitional and should not become a permanent dependency; benchmark against currently supported low-cost models.
- Codex App Server exposes ChatGPT rate-limit state, enabling the future orchestrator to gate work based on remaining allowance.

# Agent Instructions — CS2 Autonomous Content Engine

## Authority

Read `PROJECT.md`, `DECISIONS.md`, `CAPTURE.md` and `BACKLOG.md` before making project-level changes.

These files are the durable project source of truth. Do not rely on remembered chat context when repository state conflicts with it.

## Working model

- Ilyas is the creator and final taste authority.
- ChatGPT/editorial reasoning is the project/editorial brain.
- Codex/local automation is the execution/engineering layer.
- Deterministic scripts and media tooling should execute decisions reproducibly.

## Engineering behaviour

For technical changes use:

observation -> hypothesis -> mechanism -> measurement -> change -> repeated measurement -> conclusion.

Do not apply gaming-PC tweaks without a mechanism and evidence.

Respect these constraints:
- do not change sensitivity/DPI;
- do not make HID/USB tweaks;
- do not restart or disable the NIC without permission;
- do not automatically close CS2/FACEIT/Discord;
- do not reboot Windows automatically;
- prefer diagnostics before modification;
- avoid broad tweak packs;
- preserve rollback information for meaningful changes.

## Token / compute discipline

- Do not repeatedly send full raw-video context to expensive reasoning models.
- Preprocess locally where possible.
- Use transcripts, manifests, proxies, scene indexes and structured plans.
- Separate expensive editorial reasoning from deterministic execution.
- Do not use computer-vision/UI clicking where an API, CLI, config file or script is more reliable.
- Avoid status chatter during long automated work; persist logs and return concise actionable results.

## Media quality

Never optimize solely for number of cuts, number of kills, visual effects or short-term spectacle.

Preserve:
- causal context;
- live calls and predictions;
- useful explanation;
- natural humour;
- teammate interaction;
- tension and payoff;
- creator personality.

Avoid obvious "AI slop" behaviours:
- invented drama;
- fake statistics;
- excessive subtitles/effects;
- random zooms;
- meaningless cuts;
- synthetic-looking thumbnails when real imagery is stronger;
- clickbait unsupported by the actual match.

## Safety for automation

Automation must be:
- idempotent where possible;
- restartable;
- observable;
- versioned;
- explicit about failed states;
- conservative about deletion;
- unable to publish/delete valuable assets silently during early calibration.

## Documentation rule

Any substantial new idea, decision, constraint, failure mode, workflow improvement or creator preference discovered during the project should be written back into the appropriate project file rather than existing only in a chat.

Do not store irrelevant personal information in the repository.

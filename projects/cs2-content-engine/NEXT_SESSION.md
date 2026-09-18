# Next Session Checkpoint

Date created: 2026-09-18

## Current project state

The project concept, architecture, Plus-only constraint, Codex budget policy, new-chat bootstrap, privacy boundary and future personal knowledge-base plan are documented.

No OBS/Capture changes have been applied yet.

No OpenAI API billing is required or enabled by this project plan.

## Tomorrow's exact order

### 1. Capture v1 — inspect before changing

First collect the current machine state relevant to recording:

- Windows build;
- NVIDIA driver;
- OBS installed/not installed;
- available audio input/output endpoints;
- exact HyperX Cloud III Wired microphone endpoint;
- Chrome/FACEIT party-voice playback path;
- CS2 display mode/resolution/refresh;
- current GPU encoder availability;
- recording destination free space.

Do not change sensitivity/DPI, HID/USB, NIC state, or gaming tweaks.

### 2. Research only what is needed

Confirm the current stable OBS release and any current CS2/FACEIT capture-specific constraints before installing/configuring.

Avoid generic tweak guides.

### 3. Install/configure OBS

Create a dedicated project profile/scene collection.

Required logical tracks:

- Track A: CS2/game audio;
- Track B: Ilyas microphone;
- Track C: FACEIT party voice from Chrome.

Prefer native per-application audio capture if it works reliably. Do not introduce virtual audio cables unless necessary.

### 4. Short validation recording

Before recording a full match, make a short controlled test containing:

- CS2 gameplay;
- Ilyas speaking;
- teammate/FACEIT voice;
- several seconds of overlapping speech/game audio.

Validate with ffprobe and playback.

### 5. Competitive impact A/B

Compare recording OFF vs ON with objective frametime/performance data.

Do not accept the setup merely because the video looks good.

### 6. Freeze Capture v1

If the test passes:

- export/save OBS config;
- document exact settings;
- save rollback info;
- record one complete match.

## After Capture v1 passes

Build the Plus-only Agent Bridge:

1. Codex App Server with ChatGPT authentication;
2. rate-limit monitor;
3. persistent Director/Worker threads;
4. cheap-model A/B benchmark;
5. bounded job state/checkpoints;
6. test file -> automatic worker -> report.json.

## Codex budget rule

Codex is execution capacity, not the primary reasoning budget.

Before heavy work:
- read current rate-limit state when available;
- avoid expensive models by default;
- use the cheapest sufficient worker model;
- keep reasoning low for explicit execution tasks;
- never start a long task when remaining allowance is too low to reach a safe checkpoint.

## New-chat bootstrap

If tomorrow starts in a different ChatGPT chat, use:

> Open the connected GitHub repository `IlyasMemphis/rep`, read `projects/cs2-content-engine/START_HERE.md` and the files it requires, then continue from `NEXT_SESSION.md`.

## Important privacy note

`IlyasMemphis/rep` is public.

Do not add general personal-life context or sensitive information here. The separate private personal knowledge repository remains planned but not created yet.

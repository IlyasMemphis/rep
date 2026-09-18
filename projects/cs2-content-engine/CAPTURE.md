# Capture Baseline

## Goal

Create a repeatable recording setup for competitive CS2 that gives the later AI/editorial pipeline maximum information while adding minimal gameplay overhead.

## Known source layout

The recording needs to preserve at least these logical sources separately:

1. **CS2 gameplay video**
2. **CS2/game audio**
3. **Ilyas microphone**
   - HyperX Cloud III Wired
4. **Teammate / party voice**
   - FACEIT party voice running in Chrome

The teammate audio should not be permanently baked together with game audio or Ilyas's microphone if Windows/OBS routing allows clean separation.

## Why separation matters

Separate sources allow later automation to:

- clean/compress/EQ the microphone without touching the game;
- duck game audio only under speech;
- adjust teammate voice independently;
- transcribe and diarize more reliably;
- generate speaker-aware subtitles;
- preserve clean clutch/gameplay moments;
- change the mix for long-form vs short-form exports;
- recover from one source being too loud without damaging the others.

## Capture tool direction

Initial candidate: **OBS Studio**, configured by the local agent only after current-version research and a machine inspection.

Do not pin an OBS version yet. The setup phase must first verify:

- current stable OBS version and relevant regressions;
- available capture method for CS2 under the user's current Windows/anti-cheat environment;
- GPU encoder support and recording overhead;
- whether per-application audio capture works reliably for:
  - CS2
  - Chrome/FACEIT party voice
- actual Windows audio device names and endpoints;
- microphone format/sample rate;
- monitor/game resolution and FPS;
- storage write performance and free space;
- whether any capture mode conflicts with FACEIT Anti-Cheat.

## Non-negotiable PC constraints

Capture setup must respect the user's existing competitive-PC rules:

- do not change sensitivity or DPI;
- do not make HID/USB tweaks;
- do not restart or disable the NIC without permission;
- do not close CS2, FACEIT or Discord automatically;
- do not reboot Windows automatically;
- diagnose and measure before changing important system behaviour;
- change one substantial variable at a time where performance impact is being evaluated.

## Desired recording characteristics

The raw should prioritize editing headroom and clarity, not tiny file size.

Exact values are **TBD after measurement**, not guessed now.

We need to determine:

- resolution;
- capture FPS;
- codec/encoder;
- rate control;
- quality target;
- keyframe strategy;
- audio sample rate;
- container;
- track mapping;
- file naming;
- automatic remux/recovery strategy;
- hotkey/start-stop workflow;
- storage location.

## Important reliability rule

Do not use a fragile configuration simply because it is theoretically higher quality.

For competitive recording, the capture baseline is accepted only if it passes:

1. full-match-length recording test;
2. no meaningful CS2 frametime degradation;
3. no missing/duplicated audio sources;
4. no audio drift;
5. no corrupted final file after normal stop;
6. intelligible microphone and teammate speech;
7. sufficient image quality for crop/reframe/Shorts;
8. reproducible start/stop procedure.

## Planned validation

Before the first real content session:

- record a short controlled test;
- inspect the resulting file with ffprobe;
- verify every audio track independently;
- inspect sync at beginning and end;
- compare CS2 performance/frametime with recording OFF vs ON;
- verify FACEIT/anti-cheat compatibility;
- save the OBS profile/scene configuration as versioned project data.

Only after this passes do we record a full candidate match.

# CS2 Autonomous Content Engine

## Status

Project seed created from Ilyas's night-session concept on 2026-09-18.

This is the durable source of truth for the project. Chat history is not the authority. When project decisions change, update these files.

## Core idea

Ilyas creates the scarce input: authentic competitive CS2/FACEIT matches, live decision-making, mechanics, personality, voice comms, and the progression story.

The system should automate as much of the downstream media workflow as is realistically safe and high-quality:

1. record full matches;
2. ingest a completed recording;
3. identify the corresponding FACEIT match and statistics;
4. understand gameplay, speech, context, humour, teaching moments, IGL/captain calls, tension and payoff;
5. create a structured editorial plan;
6. render long-form YouTube content;
7. create meaningful Shorts/TikTok/Reels candidates;
8. perform technical and editorial QC;
9. prepare thumbnails and metadata;
10. schedule/publish through supported official integrations;
11. preserve project data and archive/delete large raw files only under explicit retention rules;
12. learn from Ilyas's feedback and channel analytics over time.

## Creator role

The intended steady-state workflow is deliberately narrow:

> Play -> record -> decide the match is worth keeping -> upload it.

The user should not become a full-time editor, uploader, metadata operator or automation maintainer.

## Editorial identity

The content is not meant to be a generic kill montage or hyper-edited AI compilation.

The differentiator is the combination of:

- high-level competitive CS2 gameplay;
- natural live communication with a teammate;
- Ilyas often acting as the more experienced player / captain / IGL;
- calls, explanations and predictions that later pay off in gameplay;
- authentic humour and reactions;
- visible Elo/progression;
- strong matches, good KD, notable kills and meaningful plays;
- the feeling of documenting a real climb rather than manufacturing isolated clips.

The system must preserve setup -> decision -> execution -> reaction when that sequence carries the value. A mechanically strong kill without context can be less valuable than a lower-action scene that reveals why a round was won.

## Business / career upside

Primary outcome: build an entertaining CS2 content channel and distribution loop around gameplay Ilyas already wants to play.

Possible secondary outcome after proving the pipeline on the creator's own channel: productize the infrastructure for FACEIT grinders, competitive players, coaches or streamers.

This repository can also become a portfolio asset demonstrating full-stack, AI orchestration, media processing, automation, API integration and product thinking.

## Design principles

- Human authenticity is the source; AI is infrastructure.
- Automate repetitive work, not taste blindly.
- Prefer deterministic rendering from structured edit plans over UI automation.
- Separate observation, decision and execution.
- Use cheap preprocessing before expensive multimodal reasoning.
- Keep original facts and statistics grounded in platform/API data.
- Preserve reversibility: keep transcripts, match metadata, edit plans and QC reports.
- Optimize for reliability and quality before full autonomy.
- Do not publish automatically until the editorial system is calibrated on real matches.
- Treat every manual correction from Ilyas as training data for the style system.

## Current phase

**Phase 1 — Capture baseline**

Goal: produce one technically excellent raw recording that preserves all information needed by the future pipeline.

The first milestone is not publishing. It is proving that a full match can be recorded reliably with clean, separable audio sources and acceptable performance overhead.

See `CAPTURE.md` and `BACKLOG.md`.

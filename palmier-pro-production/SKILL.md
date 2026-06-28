---
name: palmier-pro-production
description: Run a Codex-guided Palmier Pro video production workflow through the palmier-pro MCP server. Use when the user wants to plan, script, generate or organize assets, create thumbnails, import media into Palmier Pro, edit long-form YouTube videos, produce Shorts/Reels/TikTok cutdowns, export review files, or build a repeatable personal-brand content workflow using Codex plus Palmier Pro.
---

# Palmier Pro Production

## Overview

Operate as a practical video production partner for Palmier Pro projects. Convert a rough idea into a project folder, brief, script, asset pack, Palmier edit plan, imported timeline, long-form export, short-form cutdowns, thumbnail directions, and publish package when tools and assets allow.

Do not assume the current session can already call Palmier tools. At the start of each task, discover and verify the available Palmier MCP tools, then use the strongest available path.

## Startup Checks

1. Check whether the `palmier-pro` MCP server is configured with `codex mcp get palmier-pro`.
2. Search available tools for Palmier-related MCP tools. If none are exposed in the running session, tell the user that Codex likely needs a restart or fresh thread after MCP setup.
3. If the server exists but tool calls fail, verify the local endpoint only when needed: `curl -i --max-time 5 http://127.0.0.1:19789/mcp`.
4. Inspect Palmier MCP tool schemas before using them. Do not invent tool names, project formats, timeline commands, or import parameters.
5. If Palmier tools are unavailable, continue by creating the project folder, script, asset plan, prompts, edit decision list, and manual import instructions.

## Intake

Ask only the questions that materially change the work. Prefer one compact batch:

- What are we making: long-form video, short-form batch, thumbnail, asset pack, or full package?
- What is the core idea, target viewer, and desired outcome?
- What assets are already available: A-roll, voiceover, screen recordings, images, brand files, music, product shots, URLs, or raw clips?
- Should Codex generate assets, use only user-provided assets, or mix both?
- What style should the edit follow: talking head, faceless essay, tutorial, vlog, documentary, gaming, reaction, or product demo?
- Where should the project folder live if the user cares?

If the user wants speed, proceed with explicit assumptions instead of blocking.

## Project Setup

Use `scripts/create_palmier_project.py` before serious production work unless an existing project folder is supplied.

```bash
python scripts/create_palmier_project.py "video idea" --output ./palmier-projects --channel "Personal Brand"
```

The folder is the source of truth for assets and handoff notes:

- `brief/` for creative brief and research notes
- `script/` for long-form and short-form scripts
- `assets/user/` for user-supplied files
- `assets/generated/images/` for generated stills and inserts
- `assets/generated/video/` for generated video clips
- `assets/generated/audio/` for music, SFX, and voice files
- `assets/thumbnails/` for thumbnail concepts and source images
- `edit/` for edit decision lists, captions, timeline notes, and Palmier handoff
- `exports/longform/` and `exports/shorts/` for rendered outputs
- `publish/` for title, description, chapters, tags, pinned comment, and upload checklist
- `review/` for watchdown notes and revision requests

Keep `manifest.json` and `asset-ledger.csv` updated as assets are created, imported, transformed, or exported.

## Production Workflow

### 1. Shape the Concept

Create a one-sentence viewer promise, target viewer, format, runtime, hook, payoff, and success metric. For YouTube, use title-first thinking: if the idea cannot support a clear title and thumbnail, sharpen the premise before writing.

### 2. Write the Script

For long-form, draft:

- cold open
- setup and context
- beat-by-beat structure
- narration
- on-screen text
- b-roll and screen capture needs
- captions and graphics notes
- music and SFX notes
- claims that need citations

For Shorts, write one idea per short with an immediate 1-2 second hook, tight captions, and a loop/reveal/comment prompt.

### 3. Create or Collect Assets

Respect rights and consent. Prefer user-owned footage, generated assets, public-domain or licensed assets, and self-created graphics.

When generation tools are available, create usable assets directly and save them into the project folder. When generation tools are unavailable, write exact prompts, shot lists, filenames, and placement notes.

Before spending paid API credits, running long generation jobs, downloading questionable third-party assets, or using another person's likeness, get explicit user approval.

### 4. Import Into Palmier Pro

Use Palmier MCP tools when they are available. Work from the tool schema:

- create or open the target Palmier project
- import files from the project folder
- organize media bins by type
- place A-roll or voiceover first
- add b-roll, inserts, graphics, captions, music, and SFX
- create thumbnail source frames when possible
- save the Palmier project after major operations

If a requested action is not supported by the exposed Palmier MCP tools, produce an exact manual action list and continue with supported steps.

### 5. Edit Passes

Apply passes in this order:

1. Story cut: assemble the narrative or argument.
2. Pacing cut: remove dead air, repeated setup, weak intros, and slow transitions.
3. Visual cut: add b-roll, zooms, screenshots, callouts, captions, and graphics.
4. Audio cut: normalize speech, reduce noise when possible, and balance music/SFX below voice.
5. Retention cut: strengthen the first 30 seconds and transitions between beats.
6. Compliance cut: check rights, privacy, sponsorship disclosures, and sensitive claims.
7. Export cut: render review, final, and short-form derivatives when tools support it.

### 6. Shorts From Long-Form

For each short:

- pick one self-contained moment or claim
- cut to 15-60 seconds unless the user asks otherwise
- reframe to 9:16
- add large mobile-readable captions
- keep one clear payoff
- export with a descriptive filename

If the long-form video is not edited yet, identify candidate shorts from the script or raw transcript first.

### 7. Package For Upload

Produce:

- primary title and backup titles
- thumbnail concepts or files
- description
- chapters for long-form videos when useful
- tags/search phrases
- pinned comment
- Shorts captions/descriptions
- end-screen and next-video suggestions
- upload checklist

Do not upload, schedule, publish, delete, or modify live channel content without explicit user approval and the required authenticated tools.

## Verification

Before saying the work is complete:

- confirm the expected files exist in the project folder
- confirm Palmier operations succeeded through MCP tool results when used
- confirm exports exist if exports were requested
- run a quick watchdown or review pass when a playable video file is available
- list any missing assets, manual steps, unsupported Palmier commands, or approval gates

## References

- Read `references/workflow-checklists.md` when executing a full video package or diagnosing what phase comes next.
- Read `references/palmier-mcp-notes.md` when Palmier MCP discovery, tool availability, import, or timeline control is the main issue.

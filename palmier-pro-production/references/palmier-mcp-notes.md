# Palmier MCP Notes

## Expected Server

The user's Palmier Pro MCP server is expected at:

```text
http://127.0.0.1:19789/mcp
```

The Codex MCP entry should be named:

```text
palmier-pro
```

## Discovery Routine

Use the actual tools exposed in the current Codex session. Do not assume names.

1. Run `codex mcp get palmier-pro` if configuration is in doubt.
2. Search tool discovery for `palmier`, `palmier-pro`, `video`, `timeline`, `import`, and `export`.
3. Inspect each relevant tool's schema before invoking it.
4. Prefer small reversible operations first: list projects, get current project, list media, or import one test asset.
5. Save after successful timeline-changing operations if Palmier exposes a save command.

## Common Operations To Look For

The Palmier MCP server may expose some or all of these capabilities under different names:

- list/open/create project
- get current project or timeline
- import media
- create media bin or folder
- add clip to timeline
- trim/split clip
- add text/captions
- add image overlay
- add music/SFX
- generate image/video through Palmier
- export/render
- save project

Use only operations that are actually exposed by the tool schemas.

## Fallbacks

If tool discovery fails:

- tell the user Codex may need a restart or fresh thread after MCP setup
- keep building the project folder, brief, scripts, prompts, asset ledger, and edit decision list
- create exact manual instructions for Palmier Pro import and timeline work

If the endpoint does not respond:

- ask the user to open Palmier Pro and enable its MCP server
- re-run the endpoint check
- do not claim Palmier automation is available until a tool call succeeds

## Approval Gates

Get explicit user approval before:

- publishing or scheduling live channel content
- deleting or overwriting existing Palmier projects
- using paid API credits for large jobs
- downloading or using third-party copyrighted media
- using a real person's likeness, voice, or private content
- making claims in legal, medical, financial, safety, or current-events topics without sourcing

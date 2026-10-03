# dcs-ai

An MCP server for DCS World mission files. Lets Claude read and write `.miz` missions in plain language, built on [pydcs](https://github.com/pydcs/dcs).

Personal tool, Windows, Python, runs locally over stdio.

## Status

Nothing works yet. The first step is the round-trip test: load a stock mission with pydcs, save it unchanged, and check nothing was lost. Until that passes there is no reason to build anything on top.

## Layout

```
notes/      decisions, findings, working notes
```

Code arrives once the round-trip test says which project this is.

## Requires

- Windows, Python 3.12 or 3.13
- A DCS World installation
- pydcs, installed from GitHub not PyPI. The PyPI release is from April 2023 and stale; the repo tracks current DCS versions.

Tracked in the vault at `Personal/fun/DCS/DCS-AI`. See `CLAUDE.md`.

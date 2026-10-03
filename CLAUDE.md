# DCS-AI

An MCP server that lets Claude read and write DCS World `.miz` mission files, built on [pydcs](https://github.com/pydcs/dcs). Personal tool. Python, stdio, local.

## Tracked in the vault

This repo is tracked by the vault node **DAI**, at `C:\Users\Alex\Documents\Vault\Personal\fun\DCS\DCS-AI`.

The split, decided 2026-09-24:

- **Here** – the code, and the thinking. Decisions, findings and working notes go in `notes/`, next to the work, because that is where the work happens.
- **The vault node** – tracking only. `NODE.md` is a thin card so the project exists to the vault. `STATE.md` is the state.

**On closing a session here, write the vault node's `STATE.md`:** `status`, `updated`, `next`, and the Open rows. It is the only way that node stays true, because it does not get opened directly.

The vault is the projection, this repo is the master. That is backwards from every other node in the vault and it is deliberate, on trial with this project.

## Rules

- **pydcs is a dependency, never copied.** LGPL-3.0 permits using it as a linked library in closed commercial code, but not absorbing its source or data files. Install it, never paste it.
- **Read before write.** No write tooling until the round-trip test passes. See `notes/`.
- **Test against copies, never live missions.** Stock missions live in `C:\Program Files\Eagle Dynamics\DCS World OpenBeta` and `C:\Users\Alex\Saved Games\DCS.openbeta\Missions`. Copy out, never edit in place.
- **Single writer.** Never have this and the DCS Mission Editor open on the same mission.
- **No TODO files here.** Next steps go to the vault `STATE.md` at close. One home per fact.
- **Do not install dcs-mcp.** Its EULA bans competitive product development. Their public pages are fair reference and are already extracted in the vault node.

## Writing style

Alex's global style applies: no Oxford comma, no em-dashes (en-dash, comma or full stop), short and plain.

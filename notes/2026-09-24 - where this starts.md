# Where this starts

2026-09-24. Repo created. Nothing built.

Full reasoning, and an extraction of the nearest competitor dcs-mcp.com, are in the vault node at `Personal/DCS/DCS-AI`. The short version:

## The shape

Three layers. Claude, then a thin MCP server (this repo), then pydcs doing the real work on the `.miz` file. The server is glue. The engine is someone else's.

A `.miz` is a zip holding six entries, of which `mission` is a single large Lua table. Text is indirected: the mission holds `DictKey_*` references and the real strings live in `l10n/DEFAULT/dictionary`. Units sit five levels deep, at `mission.coalition.<side>.country[n].<category>.group[n].units[n]`. The file carries its own ID counters, `maxDictId` and `currentKey`, which must be bumped when anything is added.

## The risk worth knowing

pydcs was built to generate missions from scratch, its main consumer being DCS Liberation. Opening someone else's hand-built mission and giving it back intact is a different job, and a library only preserves what it models. Mitigating: the June 2026 commits are load-existing fixes, so editing is actively maintained.

dcs-mcp, a paid full-time effort, took eight weeks and ten releases to get round-tripping right, and shipped six consecutive versions where strike flights silently had no attack task. Every one of those bugs produced a file that opened, loaded and flew. The failure mode of this class of tool is not crashing, it is being quietly wrong.

## First test

Three steps, one script, one afternoon.

1. Does pydcs install and load a stock mission at all? Print the name and a group count.
2. Does it save? Write to a new file, reopen the copy.
3. Is anything missing? Unzip both, compare the inner `mission` files. Not the `.miz` files themselves: they are zips, so compression and timestamps differ even when contents match.

Expect step 3's raw text diff to be noisy, because pydcs will reorder tables and reformat numbers without changing meaning. The question is not "identical", it is "is anything missing". Parse both, walk the structures, report keys present in the original and absent in the copy.

Start with the smallest stock Caucasus mission. Repeat on something big and messy afterwards, because the bugs live in the parts nobody models.

## If it fails

Read with pydcs, write raw Lua for the fields that matter. That option exists only because pydcs is open source, which is the main advantage over dcs-mcp's closed engine.

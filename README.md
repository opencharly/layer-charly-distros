# charly-distros — retired

> **RETIRED — this repo publishes nothing.** Its one `distros`-family skill lives in the
> repo that holds the code, plugin or config it documents (the table below). Nothing is
> authored, built, deployed or consumed here: a change to it is a change at its destination
> repo, in the same pull request as the entity it documents.

**This repo no longer authors a skill.** It was the `charly-distros` concept candy: a `true`-no-op `plan:` and one `skill:` entity, with the prose in `.agents/skills/`.
Under `AGENTS.md` Part II #5 a skill lives in the repo whose code,
plugin or config it describes — and this repo holds none of it (measured before the
change: **0 `.go`, 0 `.cue`, no `candy/` directory**) — so it moved, byte-identically,
to the repo that does:

| Skill | Now authored in | The entity that owns it |
|---|---|---|
| `nvidia-layer` | [`opencharly/layer-nvidia`](https://github.com/opencharly/layer-nvidia) | the `nvidia` candy it documents |

**The addresses did not change.** Every skill keeps its `distros` family at its
destination node, so `/charly-distros:<skill>` still resolve — they are simply authored
where the entity is implemented. The move is the rule `AGENTS.md` Part II #5 states, tracked
in [opencharly/opencharly#600](https://github.com/opencharly/opencharly/issues/600).

## What remains here

| Property | Value |
|---|---|
| Layer / candy | `charly-distros` (drained concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | nothing — 0 `skill:` entities |
| Service / port | none |

Do not compose, reference or edit this repo: the skills, their routing nodes and their
prose all live at the destinations above, and this repo's retirement is tracked in
[opencharly/opencharly#600](https://github.com/opencharly/opencharly/issues/600).

# charly-distros

The `charly-distros` family — the distro base-image and GPU-runtime skills.

The `charly-distros` candy is a **concept candy**: it ships no install content
and owns the `distros` family of `skill:` entities whose names have no namesake
candy. It currently carries the `nvidia-layer` skill — NVIDIA GPU runtime
support (driver libraries, `nvidia-container-toolkit` for CDI device injection,
and VA-API hardware video acceleration). The rest of the `distros` family is
owned by the standalone `distro-*` repos (`distro-arch`, `distro-cachyos`,
`distro-debian`, `distro-fedora`, `distro-omarchy`, `distro-ubuntu`) and their
sibling `layer-*` repos. `candy/plugin-marketplace` regenerates the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus from
these entities, so the skills are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-distros` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 1 `skill:` entity: `nvidia-layer` |
| Projected to | `marketplace/distros/skills/` |
| Service / port | none |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entities in `charly.yml`; the marketplace regeneration projects them
into `/charly-distros:*` pages. To reference the repo directly, compose it in a
box. A box is a `candy:` node that carries the box's `base:` image and a nested
`candy:` list of layer refs (the nested `candy:` is the composition list; the
outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-distros:v2026.265.2045'
```

The GPU runtime layer itself is consumed through the `nvidia` candy — compose
`layer-nvidia` in a GPU box; the `nvidia-layer` skill here documents that candy's
behaviour.

## Layout

- `charly.yml` — the `charly-distros:` concept candy entity plus the
  `nvidia-layer-skill:` entity (`name: nvidia-layer`, `family: distros`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-distros:nvidia-layer`
- Authoring reference: `/charly-image:layer`
- Distro base images: `opencharly/distro-arch`, `opencharly/distro-cachyos`,
  `opencharly/distro-debian`, `opencharly/distro-fedora`,
  `opencharly/distro-omarchy`, `opencharly/distro-ubuntu`
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella

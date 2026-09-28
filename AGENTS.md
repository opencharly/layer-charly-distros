# AGENTS.md — layer-charly-distros

Standalone candy repo for the `charly-distros` concept candy — it ships no
install content and owns the `distros` family of `skill:` entities whose names
have no namesake candy. It currently carries one entity, the `nvidia-layer`
skill (NVIDIA GPU runtime support); the rest of the family is owned by the
standalone `distro-*` repos and their sibling `layer-*` repos. The entities live
in `charly.yml` at the repo root; `candy/plugin-marketplace` regenerates the
standalone opencharly/marketplace corpus from them.

Canonical files:

- `charly.yml` — the `charly-distros:` concept candy entity plus the
  `nvidia-layer-skill:` entity (`name: nvidia-layer`, `family: distros`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-distros:nvidia-layer` — the owning skill for this repo's single
  `skill:` entity (NVIDIA GPU runtime, CDI device injection, VA-API). Load
  before editing that entity.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, package sections, service declarations).
  Load before editing any entity field or plan step.

## Build / validate / test

- `charly box validate` at the repo root — the structural check: the manifest
  must parse and validate at the installed charly.
- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has no
  per-repo candy gate.
- The candy is documentation-only: its `plan:` is a `true` no-op plus a `true`
  `check:` that the skill entities are present and generated into the
  marketplace. There is no live bed.

## Modify this repo

- The `skill:` entity is the projected usage source. Edit it here, never the
  generated `SKILL.md` in the marketplace corpus; a corpus regeneration
  (`charly marketplace generate`) projects it.
- The `distros` family is split across several owning repos — when a skill's
  content changes, update the entity in the repo that owns it. A new
  distro-family skill belongs in its own owning repo (a `distro-*` or `layer-*`
  repo), not added here.
- Keep the concept candy's `plan:` no-op; it exists only to carry the entities.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.

# AGENTS.md — Azeroth Fitness

Before substantive work, read `docs/standards/AGENTS.md`, `docs/standards/FIELD_NOTES.md`, `README.md` and `PROJECT_CONTEXT.md`. The shared standards are vendored at the exact revision recorded in `docs/standards/standards.lock.json`. They are contributor instructions, not runtime files. Do not assume a remote link imports them automatically.

## Project profile

- Product: **Azeroth Fitness**, a humorous Azeroth-themed fitness companion inspired by the iPhone Fitness app. Exact mechanics and data sources must be taken from the local product specification, not guessed from the name.
- Visual direction: recognizable Blizzard-native UI and typography. Brand humor should not require copying another product's assets or replacing readable native controls.
- Owner conversation: Russian. Repository language: English. UI: all official WoW locale identifiers with English fallback, following the shared standards.
- Target client/build: **TODO — confirm actual target; do not assume Retail compatibility**.
- Lua version and TOC interface: **TODO — record verified values**.
- Installable addon folder and TOC path: **TODO**.
- Native settings category and slash commands: **TODO**.
- State ownership, migration policy and any personal CVar restoration: **TODO**.
- Controller status: **unverified** until exact modes/actions are tested. Shared standards do not supply a controller implementation.

## Links and release configuration

- Source repository: **TODO**.
- Issues: **TODO — direct repository Issues URL**.
- CurseForge public page: **TODO**.
- CurseForge description editor: **TODO — project-specific authors URL**.
- CI entry point, required status checks and packaging command: **TODO**.
- Existing release publisher, tag naming and CurseForge integration: **TODO**.
- Release strategy: branch + PR, squash merge, exact final-head checks. A preview request does not authorize a release; follow explicit owner authorization and any already agreed testing scope.

## Local product decisions

Record only approved Azeroth Fitness behavior here: tracked metrics, display semantics, performance budget, saved-data retention, privacy and reset behavior where applicable. Keep dated reproduction evidence in `PROJECT_CONTEXT.md` or Issues. Do not import another addon's feature flags, presets, slogans or release history.

When adopting this template, merge it with existing local instructions rather than overwriting them. Resolve TODOs from repository evidence or owner input before dependent work; continue independent work meanwhile.

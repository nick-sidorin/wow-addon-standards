# WoW Addon Standards

Version **0.1.1** — updated 2026-11-12; originally extracted 2026-11-10 from an actively developed Forever addon. This is a portable starting kit, not a runtime library or an assertion of universal Blizzard API compatibility.

## Contents

- `AGENTS.md`: the self-contained shared rules; copy this first when only one file is needed.
- `FIELD_NOTES.md`: the evidence behind the most expensive mistakes and their limits.
- `templates/LOCAL_AGENTS.md`: root instructions for a consuming addon, including an Azeroth Fitness starting profile.
- `templates/PROJECT_CONTEXT.md`: local product decisions and verification ledger.
- `templates/CURSEFORGE_DESCRIPTION.md`: separate short/full listing text, features first.
- `templates/RELEASE_HANDOFF.md`: the owner's release delivery contract.
- `CHANGELOG.md` and `VERSION`: versioned maintenance of the rules themselves.
- `tools/standards.py`: explicit synchronization from a reviewed local Git commit and offline integrity checks (Python 3.9+; standard library only).

The documents are in English so another coding agent can use them directly. Owner conversation remains Russian. No addon implementation, credentials or runtime dependency is included. Run `python3 -m unittest discover -s tests` to verify the sync tool; CI also verifies the source inventory with `sha256sum -c SHA256SUMS`.

## Recommended shared repository

Source repository: [nick-sidorin/wow-addon-standards](https://github.com/nick-sidorin/wow-addon-standards).

Use a vendored copy pinned to an exact reviewed commit. This is simpler than a submodule for agents/CI and leaves every addon repository self-contained. It also prevents an unrelated standards edit from silently changing an active task.

Example consuming layout:

```text
AzerothFitness/
├── AGENTS.md                         # local profile and explicit read instruction
├── PROJECT_CONTEXT.md
├── CURSEFORGE_DESCRIPTION.md
├── docs/
│   └── standards/
│       ├── AGENTS.md                 # copied shared rules, not the local profile
│       ├── FIELD_NOTES.md
│       └── standards.lock.json       # provenance of the copied files
├── AzerothFitness/                   # actual installable addon; illustrative name
└── ...
```

`docs/standards/AGENTS.md` is outside the source tree's instruction ancestry. Agents will not necessarily discover it automatically. The root file must explicitly say to read it before substantive work; see the local template. Do not rely on GitHub links or an undocumented include directive.

Initial adoption:

1. Review `AGENTS.md` and fill in the project's actual client, paths, commands, links and product decisions using the templates.
2. Copy the shared `AGENTS.md` and `FIELD_NOTES.md` into `docs/standards/`.
3. Record the standards repository URL, full source commit, version and SHA-256 of each copied document in `standards.lock.json`. Use the real upstream commit that supplied the documents. Hash verification checks local consistency; reviewing the upstream commit establishes what is being adopted.
4. Exclude `docs/standards/` and local contributor documents from installable packages. Preserve the project's real runtime inventory and license requirements.
5. Open a PR for adoption. This is a documentation change, not a gameplay release.

Illustrative lock shape (replace placeholders before use):

```json
{
  "repository": "<standards repository URL>",
  "commit": "<full reviewed commit SHA>",
  "version": "0.1.1",
  "files": {
    "AGENTS.md": "<sha256 of the shared document>",
    "FIELD_NOTES.md": "<sha256 of the shared document>"
  }
}
```

Practical adoption/update commands (run from the consuming addon repository):

```bash
git clone https://github.com/nick-sidorin/wow-addon-standards.git /tmp/wow-addon-standards
# Review an upstream commit and set this to its full 40-character SHA.
STANDARDS_COMMIT=<full-reviewed-commit-sha>
# On first adoption, review and copy tools/standards.py to scripts/standards.py.
python3 scripts/standards.py sync --source /tmp/wow-addon-standards --commit "$STANDARDS_COMMIT" --target .
python3 scripts/standards.py check --target .
```

For an existing clone, fetch upstream updates before choosing the commit. Sync reads files with `git show` at that SHA even if the working tree differs. It does not fetch, execute upstream code, overwrite root agent instructions or update runtime files. Add the offline check command to CI. It validates the pinned identity, document inventory and hashes; it does not contact GitHub or certify that the rules are appropriate. Review remains necessary.

For updates, change the standards upstream first, then open a small adoption PR in each addon with the new copied files and lock. Keep project rules in the local root file instead of editing the vendored text. A bot can automate adoption PRs later; no bot or recurring task is required now.

Alternatives: a Git submodule pins a revision but needs recursive checkout and packaging exclusions; a subtree is reasonable with more repositories and established Git tooling. Fetching remote `main` instructions on every agent run is deliberately discouraged. A GitHub repository template helps bootstrap new addons but does not keep existing ones synchronized.

## Azeroth Fitness starting point

Use `templates/LOCAL_AGENTS.md` as a root starter, preserving any existing instructions. It records the product as a humorous Azeroth-themed fitness companion, with native Blizzard visuals, rather than prescribing mechanics. Decide which client build is targeted and what the addon actually measures before adding event/data collection or claiming support. Localization, native presentation, packaging and truthful compatibility reporting apply immediately; onboarding, CVar restoration, controller navigation and “New” badges apply only when those features are present.

## Maintenance

Version these standards independently of addon versions. Add concise release notes for changed guidance and its evidence. Shared rules should stay small enough to read; field notes carry historical details. Do not copy game-specific controls or old task history into every addon.

# CurseForge publishing guide — <Addon name>

Maintainer instructions belong here, never in either copyable description file.

- [Edit description](<PROJECT_DESCRIPTION_EDITOR_URL>)
- [Public addon page](<CURSEFORGE_PUBLIC_URL>)

## Prepare the listing

Fill in the project's approved facts and remove irrelevant optional sections/placeholders from the description templates before publishing. Check the platform's current short-description length limit. Keep the short text unchanged when positioning is unchanged.

- `CURSEFORGE_DESCRIPTION.md`: full public Markdown only. Copy the entire file into the full-description field. No field label, short description, maintainer note or editor link belongs in it.
- `CURSEFORGE_SHORT_DESCRIPTION.txt`: plain-text short-description value only. Copy the entire file into that field.

Keep compact benefits first, ordered by relevance to the product; place optional conveniences later. Retain separate Issues and Source Code links, supported compatibility facts and the approved closing tagline. Link both copyable files plus the editor in release handoffs.

Updating a release does not automatically update these fields unless an integration explicitly handles it. Record whether listing editing is manual or confirmed automated. Exclude both field files and this guide from installable packages. Keep repository-specific paths and destinations in the local project profile.

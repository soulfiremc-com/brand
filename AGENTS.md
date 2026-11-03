# Repository instructions

## Scope

Maintain shared product language and existing visual identity for SoulFire.
Read README.md and terminology.md before changing a guide.
Read the relevant proposal before changing a disputed term.

## Decisions and compatibility

- Keep current vocabulary in the guides and unapproved renames in proposals/.
- Project is the accepted display name. Preserve `instance` in existing public and persisted identifiers.
- Follow decision 001 for accepted display names; other proposal items remain unapproved.
- Do not infer acceptance from publication or a merged proposal document.
- Record explicit maintainer decisions in decisions/.
- Preserve exact API identifiers, package names, stored IDs, and serialized node types.
- Keep implementation and migration work in the owning repositories.

## Writing and assets

- Write clear, natural English with active voice and sentence case.
- Avoid em dashes, filler, exaggerated claims, and ambiguous lifetime promises.
- Document ownership, identity, lifetime, and behavior for shared objects.
- Keep source references stable and include the relevant version or revision.
- Preserve imported asset bytes and maintain assets/sources.json.
- Do not invent logos, typography standards, or new asset licenses as factual existing guidance.

## Checks and Git

- Check local links, image paths, Markdown structure, and asset checksums.
- Use Conventional Commit messages, with a body for non-trivial changes.
- Do not create new branches without an explicit user instruction.
- Run configured commit hooks and wait for completion. Never bypass hooks.

## Branding and product language

Before naming features or changing user-facing text and visuals, read the [SoulFire brand guidance](https://github.com/soulfiremc-com/brand).
Use its terminology, naming, writing, and visual identity guides.
Keep proposed renames separate from accepted guidance.
Preserve public identifiers until the owning repository approves a migration.

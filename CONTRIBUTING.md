# Contributing

This repository coordinates SoulFire's product language and existing visual identity across repositories.
Changes need a clear reader goal and enough evidence for maintainers to assess them.

## Choose the change type

- For a factual correction, link the relevant source and update the guide.
- For a new shared term or rename, add a [proposal](proposals/README.md).
- For an accepted proposal, add a [decision record](decisions/README.md) and describe the rollout.
- For an asset import, preserve the source bytes and update [sources.json](assets/sources.json).

Keep speculative names in proposals until a maintainer explicitly accepts them.
Do not mark a proposal accepted because its file merges into this repository.
Do not combine documentation changes with an unannounced API or schema migration.

## Review the result

1. Check the facts against the owning repository and cite a stable source revision.
2. Check local links, image paths, tables, and fenced code blocks.
3. Check each term against the glossary and its owner and lifetime.
4. Keep public identifiers exact in code examples.
5. Check assets against their recorded checksums and sources.
6. Describe compatibility and translation work for label changes.

Use Conventional Commit messages with a concise, imperative description.
Add a body when the motivation or compatibility impact needs explanation.
Run configured commit hooks and wait for them to finish. Do not bypass hooks.

## Reference the guidance elsewhere

Add links to the owning repository's contributor instructions after its maintainers adopt the shared guidance.
A repository can use this text:

```markdown
Use the [SoulFire brand guidance](https://github.com/soulfiremc-com/brand)
for shared terminology, naming, writing, and existing visual assets.
Keep proposed renames separate from accepted guidance.
Preserve public identifiers until the owning repository approves a migration.
```

Keep implementation procedures, generated references, and release-specific behavior in the repository that owns them.

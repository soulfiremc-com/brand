# Decision 001: Accept the display-name migration

Date: 2026-11-03
Outcome: **Accepted**
Proposal: [004: Display-name migration](../proposals/004-naming-migration.md)
Decision PR: [Brand #1](https://github.com/soulfiremc-com/brand/pull/1)

## Decision and reason

The maintainer directed the reviewed naming PRs to be taken through checks and merged.
This explicitly accepts the display-name selection in Proposal 004. It does not accept all items in Proposals 001 and 002.

Use **Project** for the persistent container, **Fleet** for a selection of its bots, and clear action names for features and nodes.
Project describes a setup that remains available while its bots are stopped. Fleet describes the selected bots rather than their scripts, files, and access.
Keep **Go to position** to make the node's destination clear. Give variable nodes explicit owners and lifetimes.

The proposal contains the complete old-to-new mappings and rollout criteria.
Copies and exports keep their current behavior, with accurate credential disclosures and metadata descriptions.

## Compatibility and limits

Keep API and SDK names, wire fields, CLI literals, routes, stored IDs, plugin IDs, settings keys and namespaces, and serialized node types unchanged.
Existing configuration imports, saved graphs, and explicit graph labels remain valid. Keep old names searchable.
No runtime, data conversion, process isolation, ownership, or configuration-format change is approved by this decision.

Preset, SDK/domain type renames, independent plugin-package display metadata, plugins without settings pages, and the visual redesign remain deferred.
Other locales need Crowdin review. Server-supplied labels remain untranslated.

## Implementation and release

Acceptance establishes current contributor guidance. It does not establish a release date or claim the migration is already released.
The owning repositories implement and validate the migration:

1. [SoulFire #1056](https://github.com/soulfiremc-com/SoulFire/pull/1056): server metadata, CLI and SDK prose, and compatibility tests.
2. [SoulFireClient #1214](https://github.com/soulfiremc-com/SoulFireClient/pull/1214): app labels, discovery, demos, configuration disclosures, and English source strings.
3. [Public documentation #515](https://github.com/soulfiremc-com/soulfiremc.com/pull/515): usage guides and compatibility reference. Existing screenshots retain their version notes.

Merge these after checks and review, in this order. Release coordination and translation review remain distinct follow-up work.
The linked PRs record merge status; release links belong here when a release includes the migration.

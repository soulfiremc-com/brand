# Decision 002: Use Soulfire as the display name

Date: 2026-11-05
Outcome: Accepted for implementation. Not released.
Proposal: [005: Soulfire display spelling](../proposals/005-brand-spelling.md)

## Decision and scope

After comparing Soulfire, SoulFire, and SoulfireMC, the maintainer requested coordinated branding, code, name, and asset updates across repositories.
This records Soulfire as the intended display spelling. The request authorized preparation and non-draft PRs, not a live release.

Use **Soulfire** in current product text and new name-bearing graphics.
Keep **soulfiremc** in existing domains and handles.
Keep public identifiers, repository names, download filenames, executable names, profile data paths, and imported flame artwork compatible.
The proposal defines the affected surfaces and completion criteria.

## Implementation and release

Each owning repository reviews and ships its implementation separately.
The coordinated PRs below are open for review. Record release links when a release contains the migration.
Opening a PR does not establish that the change is merged, deployed, or released.
Current screenshots, generated reference snapshots, and recorded production evidence retain their original version context.
New video narration and graphics need regeneration and review before publication.

## Coordinated pull requests

Review the brand guidance first, then the implementation PRs. Existing identifiers keep the implementations compatible during rollout.

| Repository | Pull request |
| --- | --- |
| brand | [#2](https://github.com/soulfiremc-com/brand/pull/2) |
| SoulFire | [#1057](https://github.com/soulfiremc-com/SoulFire/pull/1057) |
| SoulFireClient | [#1215](https://github.com/soulfiremc-com/SoulFireClient/pull/1215) |
| soulfiremc.com | [#517](https://github.com/soulfiremc-com/soulfiremc.com/pull/517) |
| SoulFireChromecast | [#382](https://github.com/soulfiremc-com/SoulFireChromecast/pull/382) |
| SoulFirePluginExample | [#65](https://github.com/soulfiremc-com/SoulFirePluginExample/pull/65) |
| SoulFireBypass | [#38](https://github.com/soulfiremc-com/SoulFireBypass/pull/38) |
| .github | [#1](https://github.com/soulfiremc-com/.github/pull/1) |
| video | [#2](https://github.com/soulfiremc-com/video/pull/2) |
| com.soulfiremc.soulfire | [#1](https://github.com/soulfiremc-com/com.soulfiremc.soulfire/pull/1) |

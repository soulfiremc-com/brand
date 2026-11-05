# Proposal 005: Soulfire display spelling

Date: 2026-11-05
Status: Accepted for implementation in [Decision 002](../decisions/002-brand-spelling.md). Not released.

## Name and purpose

Use **Soulfire** as the product display name. It reads as one word and needs no internal-capitalization convention.
Use **Soulfire app**, **Soulfire server**, **Soulfire CLI**, and **Soulfire SDK** when the surface needs clarification.
Keep the existing description: Minecraft bots for testing, automation, and development.

The alternatives were **SoulFire** and **SoulfireMC**. SoulFire emphasizes the compound but requires a mid-word capital.
SoulfireMC adds Minecraft context but also resembles a server or community name.
The choice concerns display spelling. It does not establish search uniqueness or a new legal name.

## Compatibility

| Surface | Migration |
| --- | --- |
| App, server messages, website, documentation, metadata, and community text | Use Soulfire. |
| Translation values | Change the product spelling only. Preserve keys, interpolation, and translated wording. |
| Domains, email addresses, handles, and organization slug | Keep soulfiremc.com and existing soulfiremc identifiers. |
| Repository names and URLs | Keep SoulFire, SoulFireClient, SoulFireChromecast, SoulFireBypass, and SoulFirePluginExample. |
| SDK exports, Java types, package coordinates, protocol names, and public identifiers | Keep their exact spelling, including `SoulFire`. |
| Downloads and release artifact filenames | Keep existing SoulFire filenames and URL conventions. |
| App ID, URL schemes, executable names, profile directories, and installer identity | Keep existing identifiers and data access. |
| Imported flame icons and provenance records | Keep the original bytes and checksums. |
| Historical screenshots, generated references to pinned revisions, and recorded execution evidence | Preserve their original names and version context. |

Do not rename files or links with a global case replacement.
Code examples keep imports such as `import { SoulFire } from "@soulfiremc/sdk/bun"` and `from soulfire import SoulFire`.

## Assets and graphics

Keep the cyan flame, its geometry, colors, and existing icon exports.
Change the displayed product name in social cards, video title cards, thumbnail captions, SVG accessibility titles, and app metadata.
Keep imported source assets intact. Change accessibility titles in consuming copies where needed.
Regenerate cached graphics and narration from the updated templates before publication.
Do not repaint an old screenshot or alter recorded console output to imply that a historical release used the new spelling.

## Rollout and completion

Prepare coordinated PRs in brand, SoulFire, SoulFireClient, soulfiremc.com, SoulFireChromecast,
SoulFirePluginExample, SoulFireBypass, .github, video, and com.soulfiremc.soulfire.
Review the brand record first, then merge the implementation PRs after their checks pass.
The website can update independently because download URLs and SDK imports remain compatible.
The Flatpak fork overrides the display name while it packages an older release.

Completion requires the new spelling on current product surfaces, unchanged public identifiers,
working existing profile data and download links, and regenerated name-bearing graphics for new publications.
Repository descriptions, social profiles, store listings, external dashboards, and published media require separate service updates.
Opening or merging these PRs does not claim that those external surfaces changed.

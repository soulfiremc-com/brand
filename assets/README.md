# Assets

The files in [icons](icons) are unchanged copies of artwork from the SoulFire server repository.
The manifest records each original source URL, Git blob ID, and SHA-256 checksum.

| File | Format and size | Placement |
| --- | --- | --- |
| [icon-rounded.svg](icons/icon-rounded.svg) | SVG, 200 × 200 | Rounded product tile. |
| [icon-square.svg](icons/icon-square.svg) | SVG, 200 × 200 | Square product tile for platform masking. |
| [trimmed-icon.svg](icons/trimmed-icon.svg) | SVG, 200 × 200 | Existing variant with internal padding. |
| [icon.png](icons/icon.png) | PNG, 512 × 512 | Existing raster product icon. |
| [pov_favicon.png](icons/pov_favicon.png) | PNG, 64 × 64 | Existing favicon for the POV surface. |

The source filename `trimmed-icon.svg` remains unchanged for provenance.
Its artwork includes padding. The name does not describe a separate logo design.
The raster and vector files remain existing exports. They are not certified as pixel-identical renders.

Interface examples for a proposal live in [screenshots](screenshots/README.md). They are not logo assets.

## Source and license

Source: [SoulFire icons](https://github.com/soulfiremc-com/SoulFire/tree/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/resources/icons).

The [license](../LICENSE) matches the source repository.
This import does not add a new asset license or a trademark policy.

## Use and update

Read the [visual identity guide](../visual-identity.md) before using an asset.
For a different size, export from the appropriate SVG and preserve its geometry.
For an upstream update, import the reviewed bytes and update [sources.json](sources.json).
Record any new asset's origin and license before adding it.

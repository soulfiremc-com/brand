# Visual identity

This guide documents Soulfire's existing cyan flame identity.
It does not introduce a new logo, app theme, or typography system.

## Logo

![Soulfire rounded icon](assets/icons/icon-rounded.svg)

Use the original files in [assets](assets/README.md).
The flame and its inner cutout identify the product. The dark tile supports the cyan mark.

- Preserve the aspect ratio, flame geometry, and existing gradients.
- Use the rounded tile where the placement does not supply its own mask.
- Use the square tile where the platform applies a mask or requires square artwork.
- Keep text and unrelated artwork outside the logo canvas.
- Avoid extra shadows, outlines, animation, or recoloring of the supplied mark.
- Use a background that leaves the entire tile visible.

The existing padded variant serves placements that need internal margins.
Keep that padding unless a platform's asset specification requires a different export.
At small sizes, inspect the inner cutout and the flame silhouette for clarity.

## Existing SVG colors

These values come directly from the supplied SVGs. They are logo colors, not a complete interface palette.

| Role | Value |
| --- | --- |
| Flame gradient start | `#00F3FF` |
| Flame gradient end | `#33F2F5` |
| Tile gradient start | `#2A2D3E` |
| Tile gradient end | `#1C1E2A` |

Keep the gradient directions and stop positions from the source artwork.
Do not assume that cyan works as readable text on every light or dark surface.
Check text contrast in the interface that uses it.

## Typography and icons

This baseline specifies no shared font family, type scale, or interface icon library.
Use the owning app or site's established typography and icon system.
Write Soulfire in that system instead of inventing a wordmark.
Use a lowercase f in new title cards, social images, thumbnails, and other name-bearing graphics.
Regenerate these graphics from their source templates. Keep the existing flame and text-free app icons unchanged.
Use interface icons for controls and the flame for product identity.

A future typography or theme specification needs examples from the actual product surfaces and a separate proposal.
[Proposal 003](proposals/003-interface-system.md) is one such proposal. It has no accepted status.

## Screenshots

Older captures can show SoulFire. Keep their original pixels and identify their version rather than retouching product evidence.

Use screenshots that explain a real task and reflect the documented product version.
Hide credentials and private server details before publication.
Keep visible labels consistent with the feature's released vocabulary.
Give each image useful alternative text.

## Asset changes

Keep imported artwork unchanged and preserve its provenance.
For a replacement, document the source, intended placements, export sizes, and migration plan in a proposal.
Update the [asset manifest](assets/sources.json) after importing a reviewed source revision.

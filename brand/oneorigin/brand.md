# Brand

OneTaxonomy, OneLineage, OnePhylogeny, OnePedigree and OneFamily are separate tools from one maker: the [OneOrigin suite](README.md). Like a tool family, they share a backbone and keep their own character. The rules are in the [suite guidelines](guidelines.md); the values below are also in [tokens.json](tokens.json), the marks are in [marks/](marks/), and the shared icon parts are in [icons/](icons/).

This is the canonical brand text. It lives in OnePhylogeny's `docs/oneorigin/`, and each tool carries a locked copy in `brand/oneorigin/`. Change it in OnePhylogeny, never in a copy.

## Palette

The OneOrigin palette has its own colors, separate from the earlier ones still used by the app icons and the interface below. The teal, cream and aubergine were approved by the owner on 2026-11-12. The five tool colors are option D, which the owner picked on 2026-11-15 when OneFamily made five tools (D206). The values are in `palette` in [tokens.json](tokens.json).

| | OneTaxonomy | OneLineage | OnePhylogeny | OnePedigree | OneFamily |
| --- | --- | --- | --- | --- | --- |
| Base | `#fb81ab` | `#1ecdef` | `#58ac66` | `#898beb` | `#e5b254` |
| Level 1 (one level away) | `#fca7c4` | `#62dcf4` | `#8ac594` | `#acaef1` | `#edc987` |
| Level 2 (two levels away) | `#fdc3d7` | `#93e7f7` | `#afd7b6` | `#c6c7f5` | `#f3daad` |
| Text, on white | `#b05a78` (4.59:1) | `#137f94` (4.68:1) | `#43834e` (4.57:1) | `#6e6fbc` (4.50:1) | `#8e6e34` (4.74:1) |

Shared by every tool:

| | Light backgrounds | Dark backgrounds |
| --- | --- | --- |
| The one | `#1f6f6b` deep teal, 5.92:1 on white | `#3fb3a8`, 6.85:1 on `#1c1820` |
| Center of the one | `#fbf8f2` cream | `#fbf8f2` cream |
| Lines | `#363051` aubergine, 12.36:1 on white | `#ece6f2`, 14.30:1 on `#1c1820` |

- **The tool colors are evenly spaced**: pink, cyan, green, violet and gold sit about 72 degrees apart around the color wheel. Teal sits apart as the shared accent, darker than all five.
- **The one is teal with a cream center** in every mark: the selected rank, the sample, the person, the animal, and the suite's origin.
- **Levels are shades.** Level 1 is the base 30% of the way to white, level 2 is 52% of the way. Siblings share a shade, and each level away from the one is a step lighter. In OneTaxonomy the ranks below are darker, so a parent and its child never match.
- **Text uses the text color, never the base.** The bases are for fills: on white they reach only 1.90:1 (OneLineage) to 3.02:1 (OnePedigree). Each text color is its base darkened in 2% steps until it reaches 4.5:1 on white.
- **Lines are aubergine**, a deep shade of the palette's violet, so the structure belongs to the palette. On dark backgrounds they turn pale.

### Checks

These are tests on the tokens and the marks, in `scripts/oneorigin.test.mjs`, so a change that breaks one fails the build:

- **Colorblind distinctness.** Any two of the five tool colors and the one (light) are at least 15 apart (CIELAB ΔE), seen with normal vision and under protanopia, deuteranopia and tritanopia. Today: 41.5, 20.9, 22.0 and 21.3. The closest pairs are pink and cyan (protanopia) and green and the one (tritanopia). The colorblind views use the Machado, Oliveira and Fernandes (2009) matrices at full severity.
- **Contrast.** Every text color is 4.5:1 or better on white. The one is 4.5:1 or better on white and on its cream center, and its dark version on both dark backgrounds (`#1c1820`, and `#12151b` in the apps). Lines are 3:1 or better on their background.
- **The one on dark backgrounds.** The lighter teal `#3fb3a8` is at least 10 apart from every tool color, with each kind of vision. Today: 10.7, against green under tritanopia. The earlier palette reached only 7.0 here, which is part of why option D was picked. Still never draw the one without its cream center: the shape tells it apart too.
- **The rule.** Level shades and text colors follow the rule above exactly.
- **The marks.** Each mark is plain SVG, labelled, uses only palette colors for its background, and draws the one in teal with a cream center.

## Marks

Six marks, each as light, dark and small SVGs in [marks/](marks/): `oneorigin`, `onetaxonomy`, `onelineage`, `onephylogeny`, `onepedigree` and `onefamily`, as `<mark>-light.svg`, `<mark>-dark.svg` and `<mark>-small.svg`. They are drawn on a 200 × 200 view box, without a background.

- **Light** is for light backgrounds, and **dark** for dark ones: pale lines and the lighter teal.
- **Small** is for 48 px and under. It has thicker lines and larger nodes, and OnePhylogeny drops its faint outer generation so it stays clean at icon size. It uses the light colors.
- **One node size, always solid.** No faded or see-through nodes. The only exception is OnePhylogeny's faint outer generation, which shows that the tree goes on.
- **Orientation follows each field.** The suite and OneTaxonomy read top-down from one origin. OneLineage is a tree of life that grows up from the one and fans into three main branches. OnePhylogeny is a circular tree, OneFamily a spiral around a person, and OnePedigree reads like a pedigree certificate, with the animal on the left.
- **The zoom chain.** OneTaxonomy is the widest view, then OneLineage, OnePhylogeny, OnePedigree and OneFamily each zoom closer in. Tool colors and the suite mark follow this order.
- **The suite mark** grows from the one at the top to all five tool colors.

## App icon

The app icons, their tiles and the heart badge below are the earlier ones, drawn from the earlier palette. They stay as they are for now: new app icons, tiles and the maker's mark aren't decided yet.

| | OnePedigree | OneTaxonomy | OnePhylogeny |
| --- | --- | --- | --- |
| Tile gradient (top → bottom) | `#f8dcc0` → `#eeb684` (pastel orange) | `#f8d6d7` → `#eda9ac` (pastel pink) | `#e6d6d2` → `#c9aca5` (pastel mauve) |
| Glyph | Two parents joined above one offspring | A rooted tree read left to right | A sample on a branching tree |

Both use the earlier palette's brown `#4c312c` as ink (connectors, UI structure). Owner's choice 2026-11-02 (option A of the palette study; the swap, option C, stays possible: exchange the two hues).

Shared by every tool:

- Tile: 896 × 896 on a 1024 canvas, corner radius 200, vertical pastel gradient of a color from the earlier palette.
- Blocks: cream `#fbf8f2`, rounded (radius ≈ 36–40), connectors 34 px in brown `#4c312c` with round joins (owner's choice 2026-11-11, "A: round (Recommended)"; the three icons already drew them round, and the text said square).
- The heart badge (brown ring, pink disc, white heart; the paths in `icons/heart-badge.svg`), as the maker's mark, placed on "the one" (the focal individual, the selected taxon).
- Small sizes (16–32 px: menu bar, file lists, favicons): `brand/icon-small.svg`, the same tile and glyph without the badge, a larger tile and heavier lines. From 64 px up, the full icon.
- Masters: `brand/icon.svg` (source) and `brand/icon-1024.png` (transparent, for app icon generators such as `tauri icon`). A future tool takes a pastel of another color from the earlier palette (mauve `#91645d`, a lighter or deeper orange/pink) and its own glyph from the same blocks.

### Icon parts

The shared parts, cut from the three icons without changing a value, are in [icons/](icons/): each tool's tile (`tile-onepedigree.svg`, `tile-onetaxonomy.svg`, `tile-onephylogeny.svg`), a cream block (`block.svg`), a connector (`connector.svg`) and the heart badge (`heart-badge.svg`, its paths exactly as in the icons). Each tool's glyph and the badge's place on it stay in that tool's own `brand/icon.svg`.

## Interface

The interface colors below are also the earlier ones, and the apps and React packages still use them. Whether they move to the palette above isn't decided yet.

Both React packages share these (colors from the earlier palette: orange `#cf8137`, pink `#e48185`, brown `#4c312c`), under their own prefixes (`op-`, `ot-`), so neither depends on the other:

- **Icons**: the same 24 × 24 line icons in `icons.tsx`, drawn from Lucide (ISC), 1.75 stroke, round caps and joins, `currentColor`. Shown next to text where a label helps; alone only in compact floating toolbars, always with `aria-label` and a visible tooltip on hover and keyboard focus (`data-tip`). Icons standing alone must say the action (a magnifier for zoom, not a bare +). Buttons are at least 32 px (WCAG asks 24); icon strokes keep 3:1 contrast; overlays use shape as well as color.
- **Controls**: 32 px buttons, radius 8, 1 px border; floating toolbar at the top right of the canvas; cards and panels radius 10 with a soft shadow; focus ring 2 px, darker orange `#a65f20` on light backgrounds and `#e7a066` in dark mode (see Focus ring below).
- **Canvas**: drag the background to pan, Ctrl/⌘ + wheel or pinch to zoom, `+` `-` `0` keys, Fit, Download SVG, Print (chart only).
- **Selection**: the brand orange for the selected item; the darker orange for focus in light mode; brown for structure; pink for the brand mark and highlights.
- Each tool keeps its own functionality and layout; only the backbone is shared.

## Focus ring

Owner's decision 2026-11-11 (option A, "darker orange ring"): "keep the brand orange everywhere else, but use the darker orange #a65f20 for focus rings on light backgrounds (4.6 to 1 or better). Dark mode keeps the lighter orange, which already passes."

- **Light backgrounds**: focus rings are `#a65f20`. That's 4.91:1 on white and 4.61:1 or better on the cream panels (`#fbf7f4`, `#f7f8fa`, `#fdf7f7`). The brand orange was 3.07:1 on white and 2.88:1 on the panels, under the 3:1 that WCAG 2.2 asks of focus indicators (1.4.11, 2.4.13).
- **Dark mode**: focus rings stay `#e7a066`, 7.1:1 or better on every dark background the tools use.
- **Everything else** keeps the brand orange `#cf8137`: fills, accents, selection, primary buttons. OneTaxonomy already uses `#a65f20` for text in the selection colour on light backgrounds.
- Each tool sets the ring through its own focus variable (`--ophy-focus`, `--op-focus`, `--ot-focus`, and `--focus` in the Mac apps), so a light theme and a dark theme each get the right one, and a test checks the light value and its contrast.

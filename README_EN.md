<div align="center">

<img src="images/banner.svg" alt="Perler Pattern Studio" width="100%">

# Perler Pattern Studio

**Drop in an image → get a printable perler bead pattern → export it with rulers and a bead-count legend**

One HTML file does all of it. No install, no internet, no dependencies — just double-click.

[![License](https://img.shields.io/badge/license-MIT-ff7a18?style=flat-square)](LICENSE)
[![Single File](https://img.shields.io/badge/build-single--file-ff9d4d?style=flat-square)](#-features)
[![No Dependencies](https://img.shields.io/badge/dependencies-none-3ddc84?style=flat-square)](#-features)
[![Offline](https://img.shields.io/badge/offline-ready-41ccff?style=flat-square)](#-features)

[中文说明](README.md) · [Changelog](CHANGELOG.md)

</div>

---

## 📖 What is this

Perler bead artists usually chart patterns one of two ways: clicking cell by cell in a spreadsheet (slow, painful), or drawing in a phone app (no colour codes). This tool collapses the whole pipeline into one step:

**Feed it an image. Get back a chart you can print and bead from directly.**

It splits your image into a grid, picks one representative colour per cell, snaps that to the nearest colour in the **MARD 221-colour standard palette**, and exports a PNG with coordinate rulers and a bead-count legend baked in.

<div align="center">
<img src="images/ui-layout.svg" alt="UI layout overview" width="100%">
</div>

---

## ✨ Features

### 🖼️ Image to pattern

- **Median-colour sampling** — each cell takes the *median* of its pixels, not the mean. Averaging smears neighbouring colours into muddy transition greys; the median keeps original colour boundaries intact.
- **MARD 221-colour standard palette** — A (yellow/orange), B (green), C (blue), D (purple), E (pink), F (red), G (brown/skin), H (greyscale) and M (Morandi grey). 9 families, 221 colours, all transcribed from the official HEX colour card.
- **8 kit presets** — `2 / 24 / 48 / 72 / 96 / 120 / 144 / 221`, matching how beads are actually sold. Pick a kit and conversion only matches within it, so **the chart matches the beads you actually own**.
- **Edge padding** — 0–20 cells, adjustable. Padded areas stay empty instead of stretching your image.
- **Reference opacity** — 0–100%, so you can trace over the original while touching up details.

### ✏️ Manual drawing

- **Brush / Eraser / Eyedropper**, with drag-to-draw (Bresenham line interpolation, so fast strokes don't leave gaps).
- **4×4 up to 100×100**, any aspect ratio, plus 20²/30²/40²/50²/70²/100² quick presets.
- **Palette search** — type `A1` or `M15` to filter; no scrolling through 221 swatches.
- **Horizontal mirror / rotate 90° clockwise**, with rows and columns swapped automatically.
- **50 steps of undo/redo**, `Ctrl+Z` / `Ctrl+Y`.

### 🎨 Ironing finish preview

How a piece looks after ironing depends heavily on the beads themselves. 8 surface finishes are simulated:

| Finish | Effect |
|---|---|
| Normal | Plain colour blocks |
| Coarse glitter | Large sparkle points, chunky |
| Fine glitter | Dense micro-sparkle, subtle pearl |
| Glow glitter | Green glow base with highlights |
| Towel | Sparse woven texture |
| Bath towel | Dense woven texture |
| Cinderella | Diagonal highlight band |
| Steamer cloth | Dot-matrix weave |

Textures are generated from a **deterministic hash** of cell coordinates, so redraws never flicker or shift.

### 📐 Export and print

- **Export PNG** — white background, coordinate rulers, and an auto-generated bead-count legend underneath, sorted in natural order by family letter and number (`A2` before `A10`).
- **Print preview** — generates an A4 page and opens the print dialog, ready to go to paper.
- **Project save/load** — JSON containing canvas size and every cell's colour, so you can come back and keep editing.

---

## 🚀 Quick start

### Option 1: Just use it (recommended)

1. Download [`index.html`](index.html) (right-click → Save as);
2. Double-click it.

That's it. No install, no sign-up, no network.

### Option 2: Clone

```bash
git clone https://github.com/AVC459/Perler_Bead_Pattern_Editor.git
cd Perler_Bead_Pattern_Editor
# Double-click index.html, or:
start index.html        # Windows
open index.html         # macOS
xdg-open index.html     # Linux
```

### Three steps to a pattern

```
① Upload an image  →  ② Pick "max colours" (e.g. 72)  →  ③ Click "Convert to pattern"
```

Touch it up with the brush if anything looks off, then hit **Export PNG**.

> **Suggested starting point**: `50² canvas + 72 colours`. That pairing is the sweet spot for most pieces — fine enough to hold detail, and 72 is one of the most common kit sizes, so you won't need to buy a whole extra set for a handful of odd colours.

---

## 📦 Project layout

```
Perler_Bead_Pattern_Editor/
├── index.html                      # Everything (HTML + CSS + JS), 64 KB single file
├── example/
│   └── example-50x50.png           # Sample 50×50 export (with rulers and legend)
├── images/
│   ├── banner.svg                  # Header banner
│   ├── ui-layout.svg               # UI layout diagram
│   ├── alipay-qr.jpg               # Donation QR
│   └── wechat-qr.png               # Donation QR
├── CHANGELOG.md                    # Changelog
├── LICENSE                         # MIT
└── README.md / README_EN.md        # Bilingual docs
```

---

## 🖼️ What the export looks like

<img src="example/example-50x50.png" alt="Sample 50x50 export" width="100%">

This is a real 50×50 export. Note:

- **Rulers on top and left** — fine lines every cell, bold lines every 5 with numbers, so you can count cells directly while beading;
- **A colour code printed in every cell** (like `H6`, `M5`, `F11`) — grab beads by code instead of eyeballing colours;
- **The legend at the bottom** — listed as `M5 ×1015`, `H6 ×412`, so you know exactly how many bags to buy before you start.

---

## ❓ FAQ

<details>
<summary><b>Why MARD colour codes and not another brand?</b></summary>

MARD is the most widely circulated colour card in the Chinese perler bead community, and its codes (`A1`, `H7`, `M5`) map directly to listings when buying beads. Other brands use different systems — cross-reference against your own card first.
</details>

<details>
<summary><b>How should I choose "max colours"?</b></summary>

Choose based on **the beads you own**, not the image:

| Setting | Meaning |
|---|---|
| 2 | Black and white only (H7 + H1) |
| 24 / 48 / 72 / 96 | Starts at pack ① and layers up — beginner to intermediate |
| 120 / 144 | Packs A–E plus the sixth, covers most palettes |
| 221 | The full set, most faithful colour |

Set it too low and colours distort; too high and you get codes you don't own. **Pick by your bead stock.**
</details>

<details>
<summary><b>The converted result looks like a muddy blob. What now?</b></summary>

Three fixes, in order of effectiveness:

1. **Change the image.** The finest detail a pattern can hold is one cell. If your subject is small or linework is thin, it will mush. Aim for the subject filling 60%+ of the frame.
2. **Go bigger.** Move from 50² to 70² or 100² — same content, more cells to express it.
3. **Raise the colour tier.** 24 colours on a photo loses a lot; try 72 or 96.
</details>

<details>
<summary><b>How large a canvas can it handle? Will it lag?</b></summary>

Up to 100×100 = 10,000 cells. Conversion samples per cell and scans the candidate palette; 100² takes roughly 1–2 seconds on a typical machine. Drawing uses a two-layer canvas and only repaints the changed layer, so even a full canvas stays smooth.
</details>

<details>
<summary><b>Does any data get uploaded?</b></summary>

No. There is no networking code anywhere in this tool. Images are processed entirely in your local browser's Canvas, and it works fully offline. You're welcome to read the source and confirm.
</details>

---

## 🛠️ Implementation notes

Single file, vanilla HTML + CSS + JavaScript. Zero dependencies, zero build step.

| Module | Approach |
|---|---|
| Canvas | Two layers: reference image underneath, pixel pattern on top. Internal buffers scaled by `devicePixelRatio` (capped at 2×) for crispness without the cost |
| Rulers | Two separate canvases, absolutely positioned and aligned, sharing the same `CELL` constant as the drawing layer for pixel-exact sync |
| Drawing | `mousedown/mousemove/mouseup` plus touch events; Bresenham interpolation fills gaps on fast drags |
| Sampling | ~10×10 subsamples per cell, sorted per channel to take the median; pixels with alpha < 10 are skipped |
| Matching | Nearest colour by RGB Euclidean distance. Candidate set is pre-filtered by the selected kit, avoiding 221 comparisons per cell |
| Textures | Deterministic `hash(x, y) → [0,1)` drives sparkle placement, so redraws are stable |
| Export | Offscreen canvas at 22px/cell, composed with white background, rulers and legend, then `toDataURL` |
| History | Full deep copies of the 2D grid onto a stack, capped at 50 entries |

The code has a commented index at the top of `index.html` — read it block by block.

---

## 🤝 Contributing

Issues and PRs welcome. Directions I'd especially like to see:

- More brand colour cards (Hama / Artkal / 漫漫, etc.);
- Reverse recognition (photo of a finished piece → grid data);
- Tiled export for large pieces (print in sections, assemble after beading).

Open an issue first so we can talk it through before you write code.

---

## 📄 License

[MIT](LICENSE) — use it however you like, commercially included. No need to tell me if you modify it.

---

## Support

This tool is one HTML file from top to bottom — no server, no ads, and no plans to charge. It took "chart a perler pattern" from a two-hour job down to two minutes for me. If it does the same for you, you're welcome to buy me a coffee. **Entirely optional — everything works exactly the same if you don't.**

<table align="center">
  <tr>
    <td align="center" width="240"><img src="images/alipay-qr.jpg" width="200" alt="Alipay QR code"><br><b>Alipay</b></td>
    <td align="center" width="240"><img src="images/wechat-qr.png" width="200" alt="WeChat QR code"><br><b>WeChat</b></td>
  </tr>
</table>

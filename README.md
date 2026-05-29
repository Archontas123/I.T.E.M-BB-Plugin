<div align="center">
  <h1>I.T.E.M — Iterative Texture Evolution Macro</h1>
  <p><em>Blockbench plugin for generating progressive texture variations</em></p>
  <p>
    <img src="https://img.shields.io/badge/status-stable-green?style=flat-square" alt="Stable">
    <img src="https://img.shields.io/badge/platform-Blockbench-blue?style=flat-square" alt="Blockbench">
    <img src="https://img.shields.io/badge/license-MIT-white?style=flat-square" alt="MIT License">
    <a href="https://github.com/Archontas123/I.T.E.M-BB-Plugin/releases/latest"><img src="https://img.shields.io/github/v/release/Archontas123/I.T.E.M-BB-Plugin?style=flat-square" alt="Latest Release"></a>
    <a href="https://github.com/Archontas123/I.T.E.M-BB-Plugin/issues"><img src="https://img.shields.io/github/issues/Archontas123/I.T.E.M-BB-Plugin?style=flat-square" alt="Issues"></a>
    <img src="https://img.shields.io/github/last-commit/Archontas123/I.T.E.M-BB-Plugin?style=flat-square" alt="Last Commit">
  </p>
</div>

## Install

Visit the **[plugin page](https://archontas123.github.io/archontas-bb-plugins/)** for an interactive sandbox preview and one-click install instructions.

Or install manually:
1. Download [`item.js`](https://github.com/Archontas123/I.T.E.M-BB-Plugin/releases/latest/download/item.js) from the latest release.
2. Open Blockbench → `File` → `Plugins` → `Load Plugin from File`.
3. Select `item.js`.

*Requires Blockbench **4.9.0** or later.*

---

## Bug Reports & Feedback

Found an issue or have a macro request? Let's fix it!

- **GitHub Issues (preferred):** Open an issue on the [Issues page](https://github.com/Archontas123/I.T.E.M-BB-Plugin/issues). Describe the unexpected behavior and your desired outcome.
- **Discord:** Message **_archontas** directly.

---

## Features

### Scope Detection
Right-click any texture in the Blockbench texture panel and select **Iterate Texture...**. The plugin automatically determines the region to process, evaluated in priority order:

| Priority | Condition | Scope |
|:---:|---|---|
| **1** | Marquee selection active | Selected pixel boundaries only |
| **2** | Layers enabled + active layer group selected | Active layer contents only |
| **3** | Otherwise | Full texture bounds |

*When a selection or layer is processed, the output frames are cleanly composited back into the full texture—all other pixel regions and layers remain perfectly intact.*

---

### Modes

| Mode | Behavior Description |
|:---:|---|
| **End Result** | The slider values reflect your final desired state. The plugin linearly interpolates each step toward it. |
| **Per Step** | The slider values reflect the exact delta added per frame, accumulating progressively across iterations. |

---

### Adjustments

Fine-tune pixel values in real-time. Every slider reprocesses the active scope instantly:

| Control | Range | Description |
|---|:---:|---|
| **Brightness** | −100 → 100 | Additive RGB offset. |
| **Contrast** | −100 → 100 | 259-factor contrast scaling around midpoint values. |
| **Hue** | −180 → 180 | Hue rotation in degrees in HSL space. |
| **Saturation** | −100 → 100 | Saturation shift in HSL space. |
| **Opacity** | −100 → 100 | Additive alpha channel offset (±255 max). |
| **Invert** | Toggle | Inverts RGB channels (`255 − value`) uniformly per frame. |
| **Shadows** | −100 → 100 | Quadratic tone curve adjustment peaking at dark values ($v = 0$). |
| **Midtones** | −100 → 100 | Quadratic tone curve adjustment peaking at mid-range values ($v = 128$). |
| **Highlights** | −100 → 100 | Quadratic tone curve adjustment peaking at bright values ($v = 255$). |

---

### Output Formats

#### Spritesheet + `.mcmeta`
Frames are stacked vertically into a single compiled PNG. A matching `.mcmeta` configuration is exported alongside it containing your custom frame time (in game ticks) and interpolation settings—drop both files straight into your resource pack folder as a standard Minecraft animated texture.

#### Duplicate Textures
Each frame is added to your active Blockbench project as a separate texture asset, named `<original>_iter_N.png`. This is ideal for exporting manual progression tracks, state variants, or durability stages.

---

### Live Preview (Frame Navigator)
The interactive dialogue includes a real-time rendering viewport on the right side:
* **Refreshes Instantly:** Frame recalculations are debounced to standard screen refresh rates for fluid scrubbing.
* **Reference Frame:** Frame 0 always displays the original, unmodified source texture as a reference.
* **Scrubbing:** Use the **◀** and **▶** buttons to cycle through the generated animation states before writing files.

---

## Build

The plugin is written as a single self-contained script `item.js` at the root and requires no build or compilation pipeline.

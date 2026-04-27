# I.T.E.M — Iterative Texture Evolution Macro

**A Blockbench plugin for generating progressive texture variations.**

Right-click any texture and configure a sequence of adjustments — the plugin outputs every frame as either a vertical spritesheet (ready for Minecraft's `.mcmeta` animated texture format) or as individual duplicate textures in your project.

---

## Installation

1. Download `item.js` from the [releases page](../../releases/latest)
2. In Blockbench, go to **File → Plugins → Load Plugin from File**
3. Select the downloaded file

Requires Blockbench **4.9.0** or later.

---

## Usage

Right-click any texture in the texture panel and choose **Iterate Texture...**

The dialog opens with a live preview panel. Navigate frames with the arrow buttons to see exactly what each iteration will look like before confirming.

---

## Scope Detection

The plugin automatically determines what region to process, in priority order:

| Priority | Condition | Scope |
|----------|-----------|-------|
| 1 | Marquee selection active | Selected pixels only |
| 2 | Layers enabled + layer selected | Active layer only |
| 3 | Otherwise | Full texture |

When a selection or layer is the scope, the output is always composited back into the full texture — other layers remain intact.

---

## Modes

| Mode | Behavior |
|------|----------|
| **End Result** | Slider values = the desired final state. The plugin interpolates each step toward it. |
| **Per Step** | Slider values = the amount added each frame. Accumulates across iterations. |

---

## Adjustments

| Control | Range | Description |
|---------|-------|-------------|
| Brightness | −100 → 100 | Additive RGB offset |
| Contrast | −100 → 100 | 259-factor contrast scaling |
| Hue | −180 → 180 | Hue rotation in degrees |
| Saturation | −100 → 100 | HSL saturation shift |
| Opacity | −100 → 100 | Alpha channel offset |
| Invert | Toggle | Full RGB inversion per frame |
| Shadows | −100 → 100 | Tone curve — dark pixels |
| Midtones | −100 → 100 | Tone curve — mid pixels |
| Highlights | −100 → 100 | Tone curve — bright pixels |

---

## Output Formats

### Spritesheet + `.mcmeta`
Frames are stacked vertically into a single PNG. A `.mcmeta` file is exported alongside it with the configured frame time and interpolation flag — drop both files into your resource pack as a standard Minecraft animated texture.

### Duplicate Textures
Each frame is added to your Blockbench project as a separate texture, named `<original>_iter_N.png`.

---

## License

MIT

# I.T.E.M (Iterative Texture Evolution Macro)

I.T.E.M is a Blockbench plugin designed to generate progressive texture variations directly within the editor. 

Right-click any texture and configure a sequence of HSL, contrast, brightness, or tone curve adjustments. The plugin exports every frame either as a vertically-stacked spritesheet (compatible with Minecraft's `.mcmeta` format) or as duplicate texture files within the project.

## Installation

### Method A: One-Click Installation
Visit the **[plugins distribution portal](https://archontas123.github.io/archontas-bb-plugins/)** to preview and install the plugin directly.

### Method B: Manual Installation
1. Download [`item.js`](https://github.com/Archontas123/I.T.E.M-BB-Plugin/releases/latest/download/item.js) from the latest release.
2. In Blockbench, navigate to **File ➔ Plugins ➔ Load Plugin from File**.
3. Select `item.js`.

*Requires Blockbench version **4.9.0** or later.*

## Features

- **Scope Targeting:** Automatically detects the processing boundary based on active marquee pixel selections, selected layers, or full texture boundaries.
- **Adjustments:** Hue, Saturation, Brightness, Contrast, Opacity, Invert, and Spline-based quadratic Tone Curves (Shadows, Midtones, Highlights).
- **Modes:** Support for **End Result** (interpolated steps toward a target) and **Per Step** (accumulative changes per iteration).
- **Live Preview:** View real-time output iterations inside a debounced navigator preview panel before generating files.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

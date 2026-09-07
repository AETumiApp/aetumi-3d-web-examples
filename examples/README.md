# aetumi-3d-web-examples — Examples

Self-contained, **production-grade** Three.js (r160) examples. No build step: open any `.html` file in a modern browser and it runs.

| Example | Description |
| --- | --- |
| [`cinematic-hero.html`](./cinematic-hero.html) | A full-viewport cinematic 3D hero — a displaced icosahedron ("crystal") in a gradient environment, glowing via ACES tone mapping + emissive + fog, with subtle pointer-parallax. |

### Expert / production features (every example)

- **Capability detection + graceful fallback** — probes WebGL2 → WebGL → none. With no WebGL context (or with `prefers-reduced-motion`) it paints a tasteful CSS gradient poster instead of a blank canvas, and low-power devices (few cores / little memory) start at reduced quality.
- **Adaptive performance** — device pixel ratio is capped at 2, and a rolling FPS average steps DPR and geometry detail **down** below 50 fps and back **up** above 58 fps, with hysteresis so it never thrashes. The render loop pauses when the canvas scrolls offscreen (`IntersectionObserver`) or the tab is hidden (`visibilitychange`).
- **Strict cleanup** — a single `dispose()` removes every listener, cancels rAF, and disposes all geometries, materials, textures and the renderer; it runs on `pagehide`.
- **Accessibility** — the canvas is `role="img"` with a descriptive `aria-label`; the optional FPS/quality readout is a real keyboard-focusable `<button>` with a visible focus ring; motion respects `prefers-reduced-motion`.
- **Premium look** — ACES Filmic tone mapping, layered key/rim/fill lighting and emissive-plus-fog glow (no post-processing dependency).

Three.js r160 is loaded as ES modules through an importmap on **jsDelivr only** (`three` + `three/addons/`).

Explore more on the hub: **https://aetumi.app** · 3D web examples → https://aetumi.app/etec

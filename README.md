# Face Looker (Vanilla) 👁️

Create an interactive face that follows the cursor using plain HTML, CSS, and JavaScript. No frameworks. No build step.

## What this is

- A tiny vanilla JS widget that swaps images based on pointer position
- Designed to work with a pre-generated grid of face images (generated elsewhere)

## Quick start

1) Put your gaze images in a `faces/` folder next to `index.html` using this naming pattern:

```
gaze_px{X}_py{Y}_{SIZE}.webp
```

Defaults expected by the script:

- P_MIN = -15, P_MAX = 15
- STEP = 3 (values like -15, -12, ..., 0, 3, ..., 15)
- SIZE = 256 (filename suffix)

Examples:

- `gaze_px0_py0_256.webp` (center)
- `gaze_px15_py0_256.webp` (right)
- `gaze_px0_pym15_256.webp` (up)

2) Open `index.html` in a browser (or serve the folder with any static server).

That's it. Move your cursor over the face.

## Configuration

In `index.html`, adjust attributes on the `.face-tracker` element:

- `data-base-path` (default `/faces/`) — where images are served from
- `data-debug` (`true` | `false`) — show overlay with mouse coords and filename

Multiple faces are supported — add more `.face-tracker` elements with different `data-base-path` values.

## How it works

`face-tracker.js` maps pointer position to normalized coordinates in \([-1, 1]\), snaps to the nearest grid point using your step size, then picks the corresponding filename.

If you change your generation parameters, update these constants in `face-tracker.js` to match:

```
const P_MIN = -15;
const P_MAX = 15;
const STEP = 3;
const SIZE = 256;
```

## Styling

Edit `FaceTracker.css` to change size, shape, or add effects. Wrap the `.face-tracker` in your own container to control its dimensions.

## License

MIT — use in personal and commercial projects.

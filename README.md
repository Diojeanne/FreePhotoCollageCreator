# Free Photo Collage Creator

A self-contained, single-file photo collage maker that runs entirely in your browser. Drop in photos, arrange them in a grid or an angled layout, frame each one with pan and zoom, and export a finished image as JPEG, PNG, or WebP.

There is no build step, no installation, no account, and no server. The entire application is one HTML file. Nothing you do — including the photos you load — ever leaves your device.

---

## Highlights

- **26 layouts** across rectangular grids, lines, asymmetric splits, and angled/polygon arrangements.
- **Per-photo framing** — pan and zoom each photo independently to control exactly what shows in its cell.
- **Draggable dividers** — resize cells by dragging the seams between them; several angled layouts have movable boundaries too.
- **Custom output** — set any output resolution, border thickness, and border color.
- **Three export formats** — JPEG, PNG, or WebP.
- **Resumes where you left off** — your layout, settings, and loaded photos (with their framing) are saved locally and restored automatically next time you open the file.
- **Private by design** — no network requests, no telemetry, no external dependencies. Everything runs locally.

---

## Getting started

1. Download `collage.html`.
2. Open it in a web browser — either by double-clicking the file, or by hosting it and visiting the URL.

That's it. The single file is the whole application.

> **Tip on persistence:** the "resume where you left off" feature relies on browser storage, which behaves differently depending on how you open the file. See [Saved sessions](#saved-sessions-persistence) for the details — the short version is that **Firefox works from a local file, and any hosted copy works in every browser.**

---

## Layouts

Pick a layout from the **Layout** menu in the toolbar. They're grouped by type:

| Group | Layouts |
|---|---|
| **Grid** | 2 × 2 |
| **Lines** | Row of 2 · Column of 2 · Column of 3 · Row of 4 · Column of 4 |
| **Two rows** | 1 over 2 · 2 over 1 · 1 over 3 · 3 over 1 · 2 over 3 · 3 over 2 · 2 over 4 · 4 over 2 |
| **Two columns** | 1 beside 2 · 2 beside 1 · 1 beside 3 · 3 beside 1 · 2 beside 3 · 3 beside 2 |
| **Angled** | 3 angled — wide top · 3 angled — wide bottom · 3 chevron — point down · 3 chevron — point up · 4 X-split · 4 pinwheel |

The rectangular layouts (Grid, Lines, Two rows, Two columns) all have **draggable seams** — grab the line between any two cells and move it to rebalance them.

In the **Angled** group, three layouts have **adjustable boundaries** you can drag: *3 angled — wide top*, *3 angled — wide bottom*, and *4 pinwheel*. The remaining angled layouts (*chevron* and *X-split*) are fixed.

---

## Adding and framing photos

**Add a photo** to any cell by dragging an image file onto it, or by clicking an empty cell to open a file picker.

Once a cell has a photo, you can frame it:

- **Pan** — drag the photo to reposition it within its cell.
- **Zoom** — scroll the mouse wheel over the photo, use the **Zoom** slider in the toolbar, or (on rectangular cells) use the small control bar that appears when you hover over the cell.
- **Reset framing** — double-click the photo, or use the **⟳** reset button.
- **Replace** — drop a new image onto a cell that already has one, or use the replace button on the cell's hover control bar.

### The toolbar Zoom slider

Click (or scroll over) any photo to **select** it — the selected cell shows a highlighted ring. The **Zoom** slider and **⟳** reset button in the toolbar then control that selected cell.

This matters most for the **angled layouts**, whose cells are shaped polygons and don't have an on-cell control bar. Selecting the cell and using the toolbar slider lets you zoom them without a scroll wheel — useful on trackpads, touchscreens, or any device where scroll-to-zoom isn't available. When you load a photo, its cell is selected automatically, so the slider is ready to use right away.

---

## Resizing the grid

- **Rectangular layouts:** hover over a seam between cells until the cursor changes, then drag to move it. In the 2 × 2 layout, pulling one divider off-center automatically squares up the others so the cells always tile cleanly.
- **Angled layouts (adjustable ones):** drag the boundary lines to reshape the cells. The boundaries are constrained so the cells can't cross over or collapse.

---

## Output settings

All output controls live in the toolbar and update live:

- **Output** — type a width and height (in pixels) and click **Apply**. **Default** restores 1050 × 700. This is the resolution of the exported image; the on-screen editor scales to fit your window, so the preview always matches the final result.
- **Border** — set the seam thickness (0–50 px) and pick a border color. The border is drawn between cells and around the outer edge.
  - On rectangular layouts, a thicker border makes the gaps wider and the cells correspondingly smaller.
  - On angled layouts, the border is drawn as a line of that thickness along each seam.
- **Format** — choose **JPEG**, **PNG**, or **WebP** for export.

---

## Saving

Click **Save** to export the collage. The file downloads as:

```
PhotoCollage-YYYY-MM-DDThhmmss.<ext>
```

…where the timestamp is the moment you saved and the extension matches your chosen format (`.jpg`, `.png`, or `.webp`). The export is rendered at your full output resolution, independent of your window size or zoom level.

**Clear all** empties every cell so you can start a fresh collage. Your settings (layout, output size, border, format) are kept.

---

## Saved sessions (persistence)

The tool continuously saves your work to your browser's local storage, so you can close the tab — or quit the browser entirely — and pick up exactly where you left off when you reopen the file.

**What's saved:**

- Output resolution and export format
- Border thickness and color
- The current layout and the positions of any dividers or adjustable boundaries
- Every loaded photo, along with its individual pan and zoom

Photos are stored as their original image data in **IndexedDB** (not as low-quality copies), so they come back at full fidelity.

**To clear saved work:** use **Clear all** to empty the photos, or clear the site's storage / browsing data in your browser to wipe everything including settings.

### Where persistence works

| How you open it | Persistence |
|---|---|
| Hosted over `http://` or `https://` (any browser) | ✅ Works |
| Local file (`file://`) in **Firefox** | ✅ Works |
| Local file (`file://`) in **Chrome / Edge / Brave / other Chromium browsers** | ⚠️ Not saved — these browsers disable IndexedDB for local files by default |
| Private / Incognito window | ⚠️ Cleared when the window closes |

If persistence isn't available, the tool still works perfectly — it just won't remember your session next time. For a published, hosted copy, persistence works everywhere.

---

## Quick reference

| Action | How |
|---|---|
| Add a photo | Drag an image onto a cell, or click an empty cell |
| Replace a photo | Drag a new image onto the cell, or use the cell's replace button |
| Pan a photo | Drag it |
| Zoom a photo | Scroll over it, or use the toolbar **Zoom** slider, or the hover control bar |
| Select a cell | Click or scroll over it (it gets a highlighted ring) |
| Reset a photo's framing | Double-click it, or the **⟳** reset button |
| Resize cells | Drag the seams / boundary lines |
| Change output size | **Output** width × height → **Apply** |
| Change border | **Border** thickness and color |
| Choose format | **Format** menu |
| Export | **Save** |
| Start over | **Clear all** |

---

## Privacy

This tool makes **no network requests of any kind**. It loads no external scripts, fonts, or trackers, and it sends nothing anywhere. Your photos are processed entirely in your browser and are only ever stored on your own device (in browser storage, for the resume feature). There is no analytics, no telemetry, and no account.

---

## Browser support and limitations

- Works in current versions of Firefox and Chromium-based browsers (Chrome, Edge, Brave, and others).
- **WebP export** requires a browser that can encode WebP. Current Firefox and Chromium versions can; if yours can't, you'll get a clear message and can choose JPEG or PNG instead.
- **Local-file persistence** is limited in Chromium browsers (see the table above). This is a browser security restriction, not a limitation of the tool.
- Very large border values combined with many cells will, as expected, shrink the cells significantly on rectangular layouts.

---

## License

Free Photo Collage Creator is free software, licensed under the **GNU General Public License, version 3 or later (GPLv3+)**.

    Free Photo Collage Creator — a self-contained photo collage maker.
    Copyright (C) 2026  Clarissa Millarker

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.

A full copy of the license text must be distributed with the program — add it as a `LICENSE` (or `COPYING`) file in the same directory. You can obtain the canonical text from <https://www.gnu.org/licenses/gpl-3.0.txt>.

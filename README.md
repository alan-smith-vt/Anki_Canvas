# Anki_Canvas
[Open Kanji Canvas](https://alan-smith-vt.github.io/Anki_Canvas/vocab_canvas.html)

## E-ink tablets (Boox Note Air etc.)

Add `?eink=1` to the URL, or tap the `▣` button top-right. The setting is remembered.

[Open in e-ink mode](https://alan-smith-vt.github.io/Anki_Canvas/vocab_canvas.html?eink=1)

E-ink mode:

- white, high-contrast theme with no glow, shadows, or CSS animations
- struggling / shaky terms are also drawn **bold** / semi-bold, so they read on a monochrome or muted-color panel
- the canvas only repaints when something changes (the dark mode used to redraw every frame, which makes e-ink flicker and ghost constantly)
- panning repaints are throttled to a few per second
- a toolbar with `‹ Page › − + ⊡` for page-by-page navigation, stepped zoom, and fit-all, so no pinch zoom is needed
- tap a term to inspect, tap again to dismiss, long-press for radical search, tap the `L`/`R` buttons above a page to start a review half

Tips for the Boox browser: set the app's refresh mode to "Regal" or "Balanced" rather than "Ultrafast"/A2 so red/orange terms keep their color, and use the page arrows instead of dragging when the panel smears.

### Running from a local clone (no network)

The app is plain static files, so a clone on the tablet works without a server:

1. Get the repo onto the tablet: install Termux and `git clone`, or download the GitHub zip and unzip it with the Boox file manager into e.g. `/sdcard/Anki_Canvas`.
2. In the browser (NeoBrowser or Chrome), open
   `file:///sdcard/Anki_Canvas/vocab_canvas.html?eink=1`
   and bookmark it. `vocab_data.js` is loaded with a plain `<script>` tag, so it works from `file://`.
3. The bundled Noto Sans JP web font is blocked by Chrome on `file://` URLs and the page falls back to the system Japanese font, which on Boox is fine. If you want the bundled font, serve the folder instead: in Termux run `python -m http.server 8000` inside the clone and open `http://localhost:8000/vocab_canvas.html?eink=1`.
4. To update, `git pull` (or re-download the zip) and reload.

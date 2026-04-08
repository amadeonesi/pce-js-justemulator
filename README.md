# PCE.js Portable — Offline Mac Plus Emulator

Run a classic Mac Plus (System 7) in your browser — fully offline, no internet needed.

---

## What's included

| File                  | Purpose                                          |
|-----------------------|--------------------------------------------------|
| `index.html`          | The emulator web page                            |
| `bundle.js`           | Pre-bundled PCE.js emulator engine (~1 MB)       |
| `pce-macplus.wasm`    | WebAssembly emulator core (~574 KB)              |
| `macplus-pcex.rom`    | PCE ROM patch (required)                         |
| `mac-plus.rom`        | **YOU supply this** — Mac Plus ROM (128 KB)      |
| `hd1.qed`             | **YOU supply this** — Mac OS disk image          |
| `pce-config.cfg`      | **YOU supply this** — emulator config            |

---

## Quick start

### Step 1 — Get the Mac OS system files

The original demo site provides them. Download:

```
https://jamesfriend.com.au/pce-js/dist/macplus-system.zip
```

Unzip it into this folder. You should end up with:
- `mac-plus.rom`
- `hd1.qed`
- `pce-config.cfg`

### Step 2 — Start a local web server

Browsers require a web server (even locally) for WebAssembly to load.

**Option A — Python (usually pre-installed)**
```bash
# Python 3
python3 -m http.server 8080

# Python 2
python -m SimpleHTTPServer 8080
```

**Option B — Node.js**
```bash
npx http-server . -p 8080
```

**Option C — VS Code**
Install the "Live Server" extension, right-click `index.html` → *Open with Live Server*.

### Step 3 — Open in browser

Navigate to: **http://localhost:8080**

The emulator will load and boot into Mac OS System 7.

---

## Controls

| Action         | How                                                  |
|----------------|------------------------------------------------------|
| Mouse          | Move normally inside the canvas                      |
| Lock mouse     | Click the **Lock mouse** button                      |
| Fullscreen     | Click **Fullscreen** or F11                          |
| Resize canvas  | Click **Resize canvas** to scale up 2×               |
| Keyboard       | Type normally; the Mac intercepts most keys          |

---

## Using a different disk image

You can swap in any Mac-compatible disk image (.img, .dsk, or .qed format).

1. Edit `pce-config.cfg` and update the disk image filename.
2. Update the `autoloadFiles` array in `index.html` to match.

To create your own disk images, use the native PCE or [Mini vMac](https://www.gryphel.com/c/minivmac/).

---

## Troubleshooting

**"Failed to start emulator"**  
You're missing one of the required disk/ROM files. Make sure `mac-plus.rom`,
`hd1.qed`, and `pce-config.cfg` are all in the same folder as `index.html`.

**Opening `index.html` directly in the browser doesn't work**  
Browsers block WebAssembly when loaded from `file://`. You must use a local
web server (see Step 2 above).

**Screen is blank / emulator hangs**  
Try refreshing the page. If using Chrome, make sure the tab is in focus.

---

## Credits

- **PCE.js** by [James Friend](https://jamesfriend.com.au/) — browser port using Emscripten
- **PCE emulator** by [Hampa Hug](http://www.hampa.ch/pce/)
- Source code: https://github.com/jsdf/pce (GPL-2.0)

# 🎸 GuitarScroll

**GuitarScroll** is a browser-based PDF viewer designed for musicians. It auto-scrolls your sheet music or guitar tabs while you play — and pauses automatically when you stop, using your device's microphone.

🔗 **Live demo:** [atilimatilgan.github.io/GuitarScroll](https://atilimatilgan.github.io/GuitarScroll/)

---

## The Problem

Reading guitar notation or tabs from a PDF means constantly stopping to scroll the page — breaking your flow and interrupting your playing.

Fixed-speed auto-scroll tools (browser extensions, etc.) don't help much either: the speed never quite matches your actual playing pace, especially when you slow down for a tricky passage or pause to think.

## The Solution

GuitarScroll listens to your playing via the microphone:

- **Scroll continues** while you're playing
- **Scroll pauses** automatically after ~1.5 seconds of silence
- **Scroll resumes** the moment you start playing again

No tapping, no clicking, no interruptions.

---

## Features

- 📄 **PDF upload** — drag & drop or file picker
- 🎤 **Mic-based smart pause** — silence detection via Web Audio API
- 🎚️ **Adjustable scroll speed** — fine-tune 1 px/s at a time
- 🎛️ **Mic sensitivity slider** — adapt to noisy environments
- ⌨️ **Keyboard shortcuts** — hands-free control
- 🌑 **Dark theme** — easy on the eyes in dimly lit practice rooms
- 📦 **Single HTML file** — no install, no server, no dependencies

---

## Usage

### Option A — Use online
Open [atilimatilgan.github.io/GuitarScroll](https://atilimatilgan.github.io/GuitarScroll/) in Chrome or Safari.

### Option B — Run locally
```bash
git clone https://github.com/atilimatilgan/GuitarScroll.git
cd GuitarScroll
python3 -m http.server 8080
# Open http://localhost:8080
```

> **Note:** Microphone access requires a secure context (HTTPS or localhost). Opening `index.html` directly via `file://` will block mic access in Chrome — use the local server method above.

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Pause / Resume scroll |
| `↑` | Increase speed (+1 px/s) |
| `↓` | Decrease speed (−1 px/s) |
| `→` | Jump forward 200px |
| `←` | Jump back 200px |
| `Home` | Go to beginning |

---

## Controls

| Control | Description |
|---------|-------------|
| **🎤 Mik Aç / Kapat** | Toggle microphone |
| **▶ Başlat / ⏸ Duraklat** | Start or manually pause scroll |
| **⏮ / ⏭** | Return to top / jump forward |
| **Hız − / +** | Adjust scroll speed (1 px/s steps) |
| **Hassasiyet slider** | Set mic sensitivity threshold |

**Mic status indicators:**
- 🟢 Green dot — sound detected, scrolling active
- 🟠 Orange dot — silence detected, scroll paused
- Orange bar below toolbar — counts down to auto-pause (1.5 s)

---

## Tech Stack

- **[PDF.js](https://mozilla.github.io/pdf.js/)** — PDF rendering in the browser
- **Web Audio API** — microphone input & RMS energy analysis
- **Vanilla HTML/CSS/JS** — zero dependencies, single file

---

## License

MIT © [Atılım Atılgan](https://atilimatilgan.github.io)

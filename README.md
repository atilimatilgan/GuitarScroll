# 🎸 GuitarScroll

**GuitarScroll** is a browser-based PDF viewer designed for musicians. It auto-scrolls your sheet music or guitar tabs while you play — and pauses automatically when you stop, using your device's microphone.

🔗 **Live demo:** [atilimatilgan.github.io/GuitarScroll](https://atilimatilgan.github.io/GuitarScroll/)

---

## The Problem

Reading guitar notation or tabs from a PDF means constantly stopping to scroll the page — breaking your flow and interrupting your playing.

A fixed `px/s` auto-scroll never quite matches your real playing pace (pixels per second isn't a musical unit), and at every page break you hit a blank gap and lose sight of the notes.

## The Solution

- **Page gaps are gone.** Every staff system is cut out of the PDF and stacked into one continuous sheet; page margins are trimmed so the notes are also bigger.
- **Speed is musical.** GuitarScroll detects the staff systems and the bar lines automatically, so you set a **tempo (BPM)** and the page moves one measure per `beats × 60 / BPM` seconds. The current measure is highlighted, with a moving "now" line.
- **Level presets** (Beginner / Intermediate / Advanced) set tempo, metronome, count-in, pause tolerance and how far ahead you can see.
- **Metronome + count-in** (accented first beat, audible count-in measure), plus a **Tap tempo** button to find your own pace.
- **Mic smart pause** (as before): scroll pauses after silence and resumes when you play.
- **🎧 Listen-and-follow (beta):** the app listens to your note onsets, matches them to the note columns it found in the tab, and adapts the tempo to how you actually play.

### About "Yousician-style" following

True note-by-note following needs the score as data (MusicXML/MIDI) plus polyphonic pitch tracking. A PDF is just a picture, so GuitarScroll does the realistic version: it reads the *rhythm* (where notes are on the tab) and follows your *tempo* by median inter-onset timing, which tolerates missed or extra notes. Position is only approximate (it can trail you by about half a measure); click a measure (or scroll) to re-sync at any time.

---

## Features

- 📄 **PDF upload** — drag & drop or file picker
- 📐 **Automatic system / bar-line detection** for staff + tab scores (falls back to fixed px/s mode for other PDFs)
- ♩ **BPM-based scrolling**, per-song remembered tempo
- 🥁 **Metronome, count-in, tap tempo**
- 🎤 **Mic-based smart pause** with a live level meter
- 🎧 **Listen-and-follow tempo adaptation (beta)**
- 🖱️ **Click a measure to jump there**; manual scrolling re-syncs the position
- 🔁 **Loop a passage** — drag across measures with the mouse (or `Shift`+click, or tap 🔁 then the first and last measure on touch screens); playback, metronome and count-in wrap seamlessly and a lap counter shows how many times you've played it
- ⌨️ **Keyboard shortcuts** — hands-free / pedal friendly
- 🌑 **Dark theme**, single HTML file, no dependencies besides PDF.js

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
| `Space` | Start / pause / resume |
| `↑` / `↓` | Tempo ±1 BPM (`Shift`: ±5). In fixed-speed mode: ±10 px/s |
| `→` / `←` | Next / previous measure |
| `PgDn` / `PgUp` | Next / previous staff line |
| `Home` | Back to the start |
| `M` | Metronome on/off |
| `L` | Loop on/off (keeps the selected range) |
| `Esc` | Remove the loop |
| Mouse drag on the notes | Select measures to loop |
| `Shift`+click | Loop from the current measure to the clicked one |

**Mic status indicators:** 🟢 sound detected · 🟠 silence, scroll paused · orange bar under the toolbar counts down to the auto-pause.

> **Tip:** with the metronome on, use headphones so the click doesn't reach the microphone.

---

## Tech Stack

- **[PDF.js](https://mozilla.github.io/pdf.js/)** — PDF rendering in the browser
- **Canvas pixel analysis** — staff-line, bar-line and note-column detection
- **Web Audio API** — metronome scheduling, microphone level & onset detection
- **Vanilla HTML/CSS/JS** — zero dependencies, single file

---

## License

MIT © [Atılım Atılgan](https://atilimatilgan.github.io)

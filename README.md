# Lyra Studio 🎙️✨

**Lyra Studio** is a beautiful, zero-dependency web application for manually and automatically syncing lyrics to audio. Create standard and word-level subtitle files directly in your browser without uploading your audio to external servers. 

Built as a **single HTML file**, it requires no build step, no frameworks, and no installation. Just open it in your browser and start syncing.

---

## ✨ Features

### 🎵 Audio Player & Waveform
- **Drag & Drop**: Load any local audio file (MP3, WAV, FLAC, OGG, etc.).
- **Visual Waveform**: Automatically generates and renders a seekable waveform using the Canvas API.
- **Vinyl Speed Control**: Slow down or speed up the track (0.5× to 1.25×). Pitch and tempo are linked (like a vinyl record), making it easier to tap along to fast songs.

### ⏱️ Manual & Auto Syncing
- **Tap to Sync**: Press `Space` to stamp the current timestamp to the selected lyric line.
- **Tap Compensation**: Adjust for your reaction time (0–500ms) to ensure perfect accuracy.
- **🤖 Auto-Time (Vocal Detection)**: Uses the Web Audio API (`OfflineAudioContext`) to isolate vocal frequencies (250Hz–3500Hz), detect vocal regions via energy thresholds, and automatically map lyric timings based on word count.
- **Nudge & Shift**: Fine-tune individual lines by ±0.1s, or shift the entire lyric block at once.

### 🎤 Karaoke & Playback
- **Karaoke Fill**: A smooth visual sweep fills the current lyric line as the audio plays.
- **Auto-Scroll**: The lyric list automatically follows the currently playing line.
- **Undo/Redo History**: Full history stack so you never lose your perfect stamps.

### 📦 Multi-Format Export
Export your synced projects to industry-standard formats:
- **LRC**: Standard line-level timestamps.
- **Enhanced LRC**: Word-level timing (karaoke style).
- **SRT**: Standard SubRip format for video subtitles.
- **WebVTT**: Standard web video text format.
- **Plain Text**: Raw lyrics without timestamps.

### 💾 Local Library & Privacy
- **100% Local**: Your audio files never leave your device.
- **Project Saving**: Save your lyrics, metadata (Title, Artist, Album), and timestamps to your browser's `LocalStorage` to resume later.

---

## ⌨️ Keyboard Shortcuts

Lyra is designed to be used primarily with the keyboard for fast, uninterrupted syncing.

| Key | Action |
| :--- | :--- |
| `Space` | Stamp the selected line and move to the next |
| `↑` / `↓` | Navigate up/down through lyric lines |
| `Backspace` | Clear the timestamp of the current line |
| `R` | Replay the current line (jumps back slightly) |
| `[` / `]` | Nudge the current line's timing by -0.1s / +0.1s |
| `Ctrl + Z` | Undo |
| `Ctrl + Shift + Z` | Redo |

---

## 🚀 Getting Started

Because Lyra Studio is a single, self-contained HTML file, getting started is incredibly simple.

1. Download the `lyra.html` file (or clone this repository).
2. Double-click the file to open it in any modern web browser (Chrome, Firefox, Safari, Edge, Brave).
3. **Drop an audio file** onto the dashed box.
4. **Paste your lyrics** into the text area and click **Start syncing**.
5. Press `Space` in time with the vocals!

*(Note: Unlike applications that require `AudioWorklet` or Service Workers, Lyra works perfectly when opened directly via `file://` or hosted on any static server).*

---

## 🛠️ Technical Architecture

Lyra Studio is a masterclass in vanilla web development, packing a full Digital Signal Processing (DSP) pipeline into a single file.

- **Zero Dependencies**: No React, no Vue, no npm packages, no build tools. Pure ES6+ JavaScript, HTML5, and CSS3.
- **Web Audio API**: 
  - `AudioContext` for real-time playback and frequency analysis (aura visualizer).
  - `OfflineAudioContext` for the **Auto-Time** feature. It applies a bandpass filter (Highpass 250Hz, Lowpass 3500Hz) to isolate vocals, calculates the RMS energy envelope, and uses thresholding to detect where singing occurs.
- **Canvas API**: Used to draw the audio waveform peaks and overlay lyric markers.
- **CSS Variables & Glassmorphism**: Fully responsive design with automatic Dark Mode support (`prefers-color-scheme`), smooth CSS transitions, and a collapsible sidebar.
- **LocalStorage**: Used for persisting the current draft (`lyra:v1`), the project library (`lyra:lib`), and UI state (`lyra:nav`).

---

## 📄 License

[Add your license here, e.g., MIT License]

---

*Built with ❤️ for musicians, translators, and subtitle enthusiasts.*

# AuraLiveMic

### Real-Time Vocal Resonance & Harmonization Engine

[![Web Audio API](https://img.shields.io/badge/Web_Audio_API-Powered-ff7139?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![Vanilla JS](https://img.shields.io/badge/Vanilla-JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black)]()
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)

*Turn your voice into a shimmering, resonant chord directly in your browser.*

[Live Demo](#) • [Features](#-features) • [Signal Flow](#-signal-flow) • [Roadmap](#-roadmap)

</div>

---

## 📖 Overview

**Resonant Mic** is a zero-dependency, browser-based Digital Signal Processing (DSP) playground. It captures your microphone input in real-time and routes it through a sophisticated Web Audio API node graph designed to extract, amplify, and harmonize the natural resonant frequencies of your voice.

Whether you are experimenting with vocal formants, creating ambient soundscapes, or just want to sound like a shimmering choir, Resonant Mic processes your audio locally with ultra-low latency—no server required.

> **Note:** Due to browser security policies regarding microphone access, this application must be served over **HTTPS** or run on **localhost**.

---

## ✨ Features

### 🎛️ Advanced DSP Engine
* **Chord-Tuned Resonance:** Select from predefined chords (C Maj, A Min, F Maj, G Maj). The engine automatically tunes its bandpass filters and delay lines to the root and intervals of the selected chord.
* **Cascaded Bandpass Filters:** Dual-stage, high-Q resonant filters per note for incredibly sharp, vocal-like formant shaping.
* **Pre-Filter Saturation:** Soft-clipping (`tanh`) waveshaper to excite upper harmonics, giving the filters more material to resonate.
* **Root-Tuned Feedback Delay:** A comb-filter style delay line tuned exactly to the period of the chord's root frequency for shimmering, rhythmic echoes.
* **LFO Q-Modulation:** Slow, organic "breathing" movement applied to the filter Q-factors to prevent static, sterile resonance.
* **Master Dynamics:** Built-in compressor to tame harsh peaks and glue the wet/dry signals together.

### 📊 Real-Time Visualizers
* **Oscilloscope:** High-fidelity time-domain waveform rendering.
* **Spectrum Analyzer:** Real-time FFT (Fast Fourier Transform) frequency distribution bar graph.

### 🎨 Modern UI/UX
* **Dark Mode Native:** Sleek, eye-friendly interface designed for long studio sessions.
* **Responsive Design:** Fully optimized for desktop and mobile viewports.
* **Graceful Error Handling:** Clear, user-friendly UI alerts for microphone permission denials, missing hardware, or insecure contexts.
* **Zero-Framework:** 100% Vanilla JS, HTML5, and CSS3. No React, no Vue, no build step required.

---

## 🔀 Signal Flow

For the audio engineers and DSP enthusiasts, here is the internal routing graph:

```text
[Mic Input] 
    └─► [Input Gain] 
         └─► [High-Pass Filter (80Hz)]
              ├──► [Dry Mix Gain] ─────────────────────────────┐
              └──► [Resonance Bus]                             │
                    ├──► [Waveshaper (Saturation)] ──┐         │
                    └──► [Bypass Gain] ──────────────┼─► [Sum]─┼─► [Master Gain] ─► [Compressor] ─► [Analyser] ─► [Output]
                                                     │         │
[Chord Freqs] ─► [Cascaded Bandpass Bank (x4)] ◄─────┘         │
[Root Freq]  ─► [Tuned Delay + Feedback LPF] ◄─── Resonance Bus│
```

---

## 🚀 Getting Started

Because Resonant Mic is a single-file application, getting started is incredibly simple.

### Local Development
1. Clone the repository:
```bash
   git clone https://github.com/yourusername/resonant-mic.git
   cd resonant-mic
```
2. Serve the file using a local HTTP server (Required for `getUserMedia`):
```bash
   # Using Python 3
   python -m http.server 8000
   
   # OR using Node.js (http-server)
   npx http-server
```
3. Open your browser and navigate to `http://localhost:8000` (or the port specified by your server).
4. Click **🎙 Start Mic** and allow browser permissions.

---

## 🗺️ Roadmap

This project is actively evolving. Here is what is planned for future releases:

### 🎵 Audio & DSP
- [ ] **Custom Chord Builder:** Allow users to input custom frequencies or intervals.
- [ ] **Pitch Tracking:** Implement an autocorrelation pitch tracker to dynamically shift chord roots based on the user's singing pitch.
- [ ] **Convolution Reverb:** Add a wet/dry reverb bus with impulse response (IR) loading for spatial depth.
- [ ] **Stereo Widening:** Implement mid/side processing or Haas effect delays for a wider stereo image.

### 🎨 UI & Workflow
- [ ] **Preset System:** Save and load custom DSP configurations using `localStorage`.
- [ ] **Audio Recording:** Integrate `MediaRecorder` API to record and export processed audio as `.wav` or `.webm`.
- [ ] **MIDI Support:** Map physical MIDI controllers to filter cutoffs, LFO rates, and chord changes via Web MIDI API.
- [ ] **WebGL Visualizers:** Upgrade the Canvas API visualizers to WebGL (using Three.js or raw shaders) for 3D audio-reactive particle systems.

### ⚙️ Architecture
- [ ] **Audio Worklets:** Migrate heavy DSP math (like custom waveshapers or delays) to AudioWorkletNodes for guaranteed zero-dropout performance on main-thread heavy pages.
- [ ] **WebAssembly (Wasm):** Port core C++ DSP algorithms to Wasm for studio-grade filter slopes and saturation models.

---

## 🤝 Contributing

Contributions are welcome! If you have ideas for new DSP nodes, UI improvements, or bug fixes:

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/AmazingDSPFeature`).
3. Commit your changes (`git commit -m 'Add Amazing DSP Feature'`).
4. Push to the branch (`git push origin feature/AmazingDSPFeature`).
5. Open a Pull Request.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information. You are free to use, modify, and distribute this code in personal and commercial projects.

---

<div align="center">
  <sub>Built with ❤️ and the Web Audio API.</sub>
</div>

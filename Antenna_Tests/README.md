# 📡 Antenna Measurement Report
**Author:** Antonis Maglaras  
**Date:** November 2025  
**Measurement Tools:** TinySA ULTRA Plus ZS406, NanoVNA-H4 V4

---

## Overview

This document summarizes comparative measurements and performance observations of two receiving antennas used with SDR equipment:

1. **Moonraker X1-HF** — a wideband HF receive-only antenna (1-50 MHz).  
2. **Sirio Boomerang 27A** — a monoband CB vertical antenna (26.8-27.6 MHz).

Measurements were conducted using a **NanoVNA** for impedance and match characterization, and a **TinySA** for real-world spectrum behavior and signal-to-noise comparison.

---

## 🧲 1. Moonraker X1-HF — Wideband Receive Antenna

### General Characteristics

| Parameter | Value / Observation |
|:--|:--|
| **Type** | Passive wideband HF receiving antenna |
| **Frequency Range** | 1.8 – 30 MHz |
| **Feedline (TDR)** | ≈ 25.3 m RG-58 |
| **Ferrite Choke** | Yes — effective in reducing common-mode current, especially near 7 MHz |
| **FM Notch Filter** | Optional — no effect below 50 MHz, useful to block 88–108 MHz broadcast overload |
| **TinySA Noise Floor** | ≈ –95 dBm (LNA off) / ≈ –85 dBm (LNA on) |
| **TinySA Spectrum Shape** | Smooth response across 1–30 MHz with a mild rise around 25–35 MHz |
| **Purpose** | HF general reception, WSPR, FT8, digital modes |
| **Transmit Capability** | ❌ Receive-only — not designed for transmission |

---

### Per-Band NanoVNA + TinySA Analysis

| Band | Frequency | VSWR | Return Loss | TinySA Behavior / Signal Response | Notes |
|:--|--:|--:|--:|:--|:--|
| **80 m** | 3.7 MHz (measured 3.509 MHz) | 5.75 : 1 | –3.05 dB | Low energy, dominated by MW/BC noise | Out of resonance; use a 2 MHz HPF for cleaner noise floor |
| **40 m** | 7.0 MHz | 2.94 : 1 | –6.15 dB | Moderate signal activity, visible HF stations | Ferrite choke reduces CM coupling and stabilizes impedance |
| **20 m** | 14.0 MHz | 3.55 : 1 | –5.08 dB | Smooth response, average signal level | Acceptable for FT8 / general HF listening |
| **11 m / CB** | 27.0 MHz | 2.59 : 1 | –7.07 dB | Clearer spectrum, small 25–35 MHz “hill” | Best region of performance for this antenna |

---

### Summary

- ✅ Excellent **broadband receive** coverage from 1.8–30 MHz.  
- 🔊 Best “sweet spot” around **25–30 MHz**.  
- ⚙️ Keep **ferrite choke** and **FM notch** inline for optimal noise suppression.  
- 🚫 Not suitable for transmission.  
- 💡 For cleaner low-band reception, add a **2 MHz high-pass** or **LC preselector**.

---

## 🗼 2. Boomerang — CB / 11 m Vertical Antenna

### General Characteristics

| Parameter | Value / Observation |
|:--|:--|
| **Type** | Monoband vertical (CB band) — capable of RX/TX |
| **Frequency Range** | 26.8 – 27.4 MHz |
| **Physical Design** | ~2.7 m whip with adjustable ground radial and wall-mount bracket |
| **Feedline (TDR)** | ≈ 23.7 m RG-58 |
| **Ferrite Choke** | Recommended near feedpoint or shack (5–7 turns on FT240-43) |
| **FM Notch Filter** | Not needed — antenna is inherently narrowband |
| **TinySA Noise Floor** | ≈ –98 dBm (LNA off) / ≈ –96 dBm (LNA on) |
| **TinySA Spectrum Shape** | Sharp single peak centered at 27.12 MHz |
| **Usage** | Ideal for CB (AM/FM/SSB), 10 m FT8/PSK, or local narrowband monitoring |

---

### NanoVNA + TinySA Measurements

| Parameter | Value | Observation |
|:--|:--|:--|
| **Resonant Frequency** | 27.0 MHz | Perfect alignment between NanoVNA and TinySA |
| **VSWR** | **1.20 : 1 @ 27 MHz** | Excellent impedance match |
| **Return Loss** | **–24 dB** | Only ≈ 0.4 % reflected power |
| **Resonant Bandwidth** | 26.8 – 27.3 MHz | Narrow, clean passband |
| **TinySA (LNA off)** | –77 dBm peak @ 27.12 MHz | Very low noise, strong carrier |
| **TinySA (LNA on)** | –66 dBm dual peaks (27.09 / 27.21 MHz) | Shows adjacent CB channels, +10 dB boost |
| **Signal / Noise Ratio** | ~+20 dB | Excellent clarity in-band |

---

### Summary

- ✅ **Perfectly tuned** for CB at 27 MHz (ch. 14–15).  
- 🔊 Narrow bandwidth = minimal off-band noise.  
- ⚙️ LNA beneficial only for weak signals; avoid overload in dense RF environments.  
- 🔩 Excellent for **FT8/10 m** or **CB DX**.  
- 📈 NanoVNA + TinySA results fully agree: resonance at 27.1 MHz, VSWR 1.2 : 1, RL –24 dB.

---

## 📚 Combined Overview

| Feature | **Moonraker X1-HF** | **Boomerang** |
|:--|:--|:--|
| **Purpose** | Wideband HF reception | Monoband CB (RX/TX) |
| **Best Frequency Region** | 25 – 30 MHz | 27 MHz (center) |
| **VSWR (best)** | 2.6 : 1 @ 27 MHz | 1.2 : 1 @ 27 MHz |
| **Return Loss (best)** | –7 dB | –24 dB |
| **Bandwidth** | Very wide (1.8–30 MHz) | Narrow (≈ 500 kHz) |
| **Noise Floor (TinySA)** | –95 dBm / –85 dBm (LNA on) | –98 dBm / –96 dBm (LNA on) |
| **Transmit Capability** | ❌ Receive-only | ✅ TX capable |
| **Best Use Case** | SDR monitoring, HF digital modes, wide coverage | CB / 10 m local comms or FT8 |
| **General Verdict** | Excellent wideband receiver | Exceptionally clean and efficient single-band performer |

---

## 🧭 Final Notes

- The **NanoVNA** provides impedance and return loss — a *static* view of matching.  
- The **TinySA** reveals the *dynamic* spectrum behavior and environmental noise impact.  
- When combined, both tools confirm the expected electrical behavior of each antenna:
  - **Moonraker X1-HF** performs as a broadband HF listener, most responsive near 25–30 MHz.  
  - **Boomerang** is tightly resonant and highly efficient at 27 MHz.  
- Ferrite chokes remain beneficial for both systems to reduce RF on the feedline shield.

---

*Measurements and observations conducted by Antonis using personal, basic test equipment under typical urban QTH conditions (KM17UW).*

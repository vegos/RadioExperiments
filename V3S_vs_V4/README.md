# MiniATS V3S & V4 — RF Testing with Signal Generator  
  
### Comparative evaluation, hardware mods, High-Z differences & USB/AM measurements

## 📌 Introduction

This document summarizes a series of RF tests performed on the **MiniATS V3S** and **MiniATS V4** receivers using a laboratory-grade signal generator across several HF frequencies, in both **USB** and **AM** modes.

All tests were performed under:

- identical signal levels per mode,
- identical connection path and 30 dB attenuator,
- identical MiniATS settings,
- identical firmware on both devices.

The goal is to evaluate:

- RF gain differences
- S-meter behavior
- frequency flatness (3–27 MHz)
- the effect of hardware modifications
- the impact of different High-Z (JFET) front-end implementations

## 🧪 Test Setup

**RF Generator:** Owon DGE1060  
**Signal path:**  
BNC → RG58 → SMA adapters → 30 dB attenuator → MiniATS (High-Z always active)

**MiniATS settings (same on both units):**
- Bandwidth: 3.0 kHz
- AGC: ON
- Volume: 35
- Step: 1 kHz (USB), 5 kHz (AM)
- Firmware: [v2.33](https://github.com/esp32-si4732/ats-mini)

### USB Tests (5 mVpp, −72 dBm)
- Waveform: Sine
- Generator output: 5 mVpp / 50 Ω
- Equivalent: −42 dBm → −72 dBm after 30 dB pad

### AM Tests (1 mVpp, −86 dBm)
- Modulation: AM, 440 Hz tone, 80% depth
- Equivalent: −56 dBm → −86 dBm after 30 dB pad

## ⚡ Hardware Modifications — MiniATS V3S

### ✔ Power Supply Mod
https://github.com/vegos/RadioExperiments/tree/main/Amnvolt_V3S/JFET_Power_Supply_Mod

### ✔ SMA Input Protection
Added BAS70‑05 Schottky diode between SMA center pin and ground.

### ✔ HF Air-Coil Input Inductor
Replaced original SMA RF trace with a **0.2 mm wire, 7‑turn, ~2 mm diameter air‑coil**.

**Function:**
- HF choke
- Matching element
- EMI suppressor
- Eliminates **theremin effect** when touching the SMA ground

## ⚡ Hardware Modifications — MiniATS V4

### ✔ SMA protection diode (factory)
Already installed.

### ✔ Same HF Air-Coil as V3S
0.2 mm wire, 7 turns, ~2 mm diameter.

### ✔ Removal of coupling capacitor
Removed headphone-ground → antenna coupling capacitor to prevent headphones acting as antenna.

### ✔ Reduction of SI4732 VCO interference
The V4 suffers stronger VCO leakage; the air‑coil reduces this significantly.  
Related: https://github.com/vegos/RadioExperiments/tree/main/Amnvolt_V4_mods

## 🔬 High-Z Front-End (JFET) Differences

Both MiniATS versions use a JFET-based High-Z buffer that is always in the RF path.  
They use **different JFET parts** and biasing networks.

Effect:
- V3S has **1–3 dB higher RF gain**
- identical noise floor
- identical AGC logic
- identical firmware S-meter scaling
- V3S shows **0.5–1 S-unit stronger** for the same signal

## 📊 USB Measurements (5 mVpp → −72 dBm)

### MiniATS V3S
| Frequency | S-Meter |
|----------|---------|
| 3 MHz | S9 |
| 7 MHz | S9 |
| 10 MHz | S9 |
| 14 MHz | S9 |
| 18 MHz | S9 |
| 27 MHz | S9–S9+0.5 |

### MiniATS V4
| Frequency | S-Meter |
|----------|---------|
| 3 MHz | S8.5–S9 |
| 7 MHz | S8.5–S9 |
| 10 MHz | S8.5–S9 |
| 14 MHz | S8.5–S9 |
| 18 MHz | S8.5–S9 |
| 27 MHz | S9 |

## 📊 AM Measurements (1 mVpp → −86 dBm)

### MiniATS V3S
| Frequency | S-Meter |
|----------|---------|
| 3 MHz | S3.0–3.5 |
| 7 MHz | S3.5 |
| 10 MHz | S4 |
| 14 MHz | S4 |
| 18 MHz | S4–4.5 |
| 20 MHz | S4.5 |
| 27 MHz | S5 |

### MiniATS V4
| Frequency | S-Meter |
|----------|---------|
| 3 MHz | S2–2.5 |
| 7 MHz | S2.5–3 |
| 10 MHz | S3 |
| 14 MHz | S3 |
| 18 MHz | S3.5 |
| 20 MHz | S3.5 |
| 27 MHz | S4 |

## 📈 Plots

![MiniATS USB Comparison](./images/miniats_usb_comparison.png)  
![MiniATS AM Comparison](./images/miniats_am_comparison.png)

## ✔ Conclusions

The MiniATS V3S and V4 share identical firmware and similar architecture, yet their **High‑Z JFET input stages differ**, giving the V3S a consistent **1–3 dB gain advantage**.

Both receivers show good frequency flatness across 3–27 MHz.  
The air‑coil modification greatly improves RF behavior, removes SMA-ground capacitive interactions ("theremin effect"), and — especially on the V4 — reduces SI4732 VCO interference.  
More information about the coil etc you can find on [Peter Neufeld](https://peterneufeld.wordpress.com/) blog.  
  
Functionally, both units perform similarly overall; BUT the V3S simply has a slightly stronger High‑Z front-end response which reflects to better reception.  
  
Note that this is covers ONLY the performance of the radios, it doesn't cover any other known problems (V4 out-of-the-box suffers from clicking noise, VCO leakage, noise coming from the headphones-as-antenna traces and circuit, and more).  

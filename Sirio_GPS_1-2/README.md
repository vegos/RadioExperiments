# Sirio GPS 1/2 – Reference Measurements (20–30 MHz)

This document contains the **reference measurements** of the **Sirio GPS 1/2 (½-wave vertical)** across **20–30 MHz**, using the same setup and methodology as the Sirio Boomerang 27A measurements, in order to allow a direct and meaningful comparison.

## Antenna Description (Manufacturer Specs)

- **Type**: ½ λ vertical
- **Radiation pattern**: Omnidirectional
- **Polarization**: Linear vertical
- **Frequency range**: 26.4–29.0 MHz (tunable)
- **Gain**: 0 dBd (≈ 2.15 dBi)
- **Bandwidth**: ≥ 1.6 MHz @ SWR ≤ 2
- **Max Power**:
  - 250 W CW (continuous)
  - 750 W CW (short time)
- **Grounding / protection**: DC-grounded
- **Connector**: SO-239 (UHF female)

### Mechanical Characteristics

- **Materials**: Aluminium, Copper, Galvanized steel, Nylon
- **Height (approx.)**: 5950 mm (19.52 ft)
- **Weight (approx.)**: 2100 g (4.63 lb)
- **Mounting type**: On-mast

---

## Measurement Setup

- **Antenna**: Sirio GPS 1/2, installed as a replacement for the Sirio Boomerang 27A.
- **Purpose**: CB transmit/receive and operation around 27.700 MHz with a CRT SS9900V.
- **Instruments**:
  - **NanoVNA** – S11 / SWR / Return Loss sweep.
  - **tinySA** – Spectrum scan of received RF power / ambient noise.
- **Sweep Range**: 20–30 MHz

### Environmental & Installation Conditions (important)

These measurements were taken:

- with **~15 meters of RG58 coaxial cable**,  
- in a **densely built urban environment**,  
- with the antenna installed at a **significantly lower height than the surrounding buildings**.

The antenna was tested under **the same environmental and feedline conditions** as the Sirio Boomerang 27A, ensuring that any observed differences primarily reflect antenna behaviour rather than installation variables.

---

## 1. NanoVNA – S11 / SWR / Return Loss (20–30 MHz)

![NanoVNA sweep 20–30 MHz](./images/GPS12_NanoVNA.bmp)

### Key Results

- **Minimum SWR**:
  - Frequency: **TBD MHz**
  - SWR_min ≈ **TBD**
  - Return Loss ≈ **TBD dB**
  - Mismatch loss ≈ **TBD dB**

- **Bandwidth for SWR ≤ 2 : 1**:
  - From **TBD MHz** to **TBD MHz**
  - Total BW ≈ **TBD MHz**

- **Approximate SWR ≤ 3 : 1**:
  - **TBD MHz**

### Representative Frequencies (CB, 10 m, and 15 m region)

> Note: 21.000 MHz lies in the **15 m amateur band region** (21.000–21.450 MHz).

| Frequency (MHz) | Sample (MHz) | SWR  | RL (dB) | Mismatch Loss (dB) | Notes |
|-----------------|--------------|------|---------|---------------------|-------|
| 21.000          | TBD          | TBD  | TBD     | TBD                 | 15 m region |
| 26.965 (CH1)    | TBD          | TBD  | TBD     | TBD                 | Lower CB |
| 27.125          | TBD          | TBD  | TBD     | TBD                 | CB center |
| 27.185 (CH19)   | TBD          | TBD  | TBD     | TBD                 |           |
| 27.405 (CH40)   | TBD          | TBD  | TBD     | TBD                 | Upper CB |
| 27.700          | TBD          | TBD  | TBD     | TBD                 |           |
| 28.000          | TBD          | TBD  | TBD     | TBD                 | 10 m |

> **NanoVNA Summary**  
> *(To be completed after measurements.)*

---

## 2. tinySA – Spectrum Analysis (20–30 MHz)

![tinySA spectrum 20–30 MHz](./images/GPS12_tinySA.bmp)

The tinySA measurement shows **ambient RF activity and received signal levels**, not impedance matching.

### Scan Settings

- Start: **20 MHz**
- Stop: **30 MHz**
- RBW: **10 kHz**
- Attenuation: **0 dB**

### Average Level per 2 MHz Segment

| Range (MHz) | Avg (dBm) | Min (dBm) | Max (dBm) | Notes |
|-------------|-----------|-----------|-----------|-------|
| 20–22       | TBD       | TBD       | TBD       |       |
| 22–24       | TBD       | TBD       | TBD       |       |
| 24–26       | TBD       | TBD       | TBD       |       |
| 26–28       | TBD       | TBD       | TBD       |       |
| 28–30       | TBD       | TBD       | TBD       |       |

### Notable Frequencies

| Frequency (MHz) | Sample (MHz) | Level (dBm) | Notes |
|-----------------|--------------|-------------|-------|
| 21.000          | TBD          | TBD         | 15 m |
| 26.965          | TBD          | TBD         | CB |
| 27.185          | TBD          | TBD         | CB |
| 27.405          | TBD          | TBD         | CB |
| 27.700          | TBD          | TBD         |     |
| 28.000          | TBD          | TBD         | 10 m |

> **tinySA Summary**  
> *(To be completed after measurements.)*

---

## 3. Combined Interpretation (NanoVNA + tinySA)

*(To be completed after both measurement sets are available.)*

---

## 4. Files

- **NanoVNA**: `GPS12_YYYYMMDD.s1p`  
- **tinySA**: `GPS12_YYYYMMDD.csv`  
- **Images**:
  - `./images/GPS12_NanoVNA.bmp`
  - `./images/GPS12_tinySA.bmp`

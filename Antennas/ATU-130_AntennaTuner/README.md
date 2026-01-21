# ATU-130 Automatic Antenna Tuner – How It Really Works  
## Practical Behavior, Measurements & Common Misunderstandings

This document summarizes **real-world measurements and observed behavior** of the popular **ATU-130 automatic antenna tuner**, based on extensive hands-on testing.

The goal is to clarify **what the ATU-130 actually does**, **what its display really means**, and **why you get confused by its SWR readings**.

---

## Test Setup & Equipment Used

All measurements and conclusions in this document are based on the following real setup:

- **Transceiver:** CRT SS9900V  
- **Antenna:** Sirio GPS 1/2 λ (½-wave CB vertical)  
- **VNA:** NanoVNA H4  
- **SWR & Power Meter:** SQV SWR-120 (analog)  
- **Coaxial Cables (antenna & pigtails):** RG58  
- **Connectors:** UHF (PL-259 / SO-239)  

Measurements were taken:
- before the tuner (TX side),
- after the tuner (antenna side),
- in BYPASS, RESET and TUNED states,
- across multiple frequencies (CB band, ~30 MHz, ~21 MHz),
- with and without proper tuner grounding.
- power gain was at 10/45 on CRT with FM modulation. 

---

## Seller Description (As Provided)

⚠️ **Important:**  
**No official manual exists** for the ATU-130 — neither printed nor online.  
The following text is the **only documentation provided by the seller**.

---

### Product Title
**1.8–50 MHz 200W Micro Shortwave Automatic Antenna Tuner  
10–15 VDC Organic Light Emitting Diode Display**

---

### Features

- **ANTENNA TUNER:**  
  Miniature shortwave automatic antenna tuner, without any control line operation, suitable for most radio stations.

- **EXCELLENT PARTS:**  
  Adopts C channel 1000V high voltage SMD capacitor, advanced PIC chip and UHF connector to ensure stable performance.

- **GOOD PERFORMANCE:**  
  Higher level capacitance, larger magnetic ring, thicker wire diameter, greater power bearing capacity, total inductance 12.4 µH.

- **ALUMINUM ALLOY:**  
  The shell of the antenna tuner is made of aluminum alloy, with light weight, fast heat dissipation and corrosion resistance.

- **COMPACT SIZE:**  
  Compact structure, convenient connection, portable design suitable for home or vehicle use.

---

### Specifications

- **Item Type:** Automatic Antenna Tuner  
- **Model:** ATU-130  
- **Material:** Aluminum Alloy  
- **Power Supply Voltage:** 10–15 VDC (center positive)  
- **Maximum Current Consumption:** 500 mA  
- **Maximum Working Power:** 150 W  
- **Starting Tuning Minimum Power:** 5 W  
- **Minimum Measurable Power:** 0.1 W  
- **Measurement Accuracy (≤10 W):** 0.1 W  
- **Measurement Accuracy (>10 W):** 1 W  
- **Maximum Installed Inductance:** 8.53 µH  
- **Minimum Installed Inductance:** 0.05 µH  

---

### Micro Automatic Antenna Tuner Notes

> **Has the function of power meter standing wave meter**  
> *(according to BYPASS, straight through mode, one horizontal line in the middle of the screen, the test value is approximate, and the accuracy is lower than that of professional high accuracy meter, for reference).*

- **MCU:** PIC18F2520  
- **Inductors:** 4 large magnetic ring inductors (3rd edition, reduced heating)  
- **Relays:** HF32 (10A), HF33 (5A)  
- **Capacitors:** High voltage porcelain chip capacitors  

- **Maximum Measurable Power:**  
  - SSB peak up to 275 W  
  - Recommended continuous SSB ≤ 200 W  

- **Continuous Modes (FT8, CW, FM):**  
  ≤ 100 W recommended  
  (reduce power when initial SWR is high; suggested duty cycle: 5 min TX / 10 min rest)

---

## 1. What the ATU-130 Actually Does

The ATU-130 is a **relay-switched impedance matching network** (L / π / T topology).

**It:**
- ✔️ Transforms antenna impedance so the **transceiver input sees ~50 Ω**
- ✔️ Protects the transmitter PA
- ✔️ Enables off-band operation

**It does NOT:**
- ❌ Make the antenna resonant
- ❌ Improve antenna radiation efficiency
- ❌ Guarantee low SWR on the antenna side
- ❌ Replace a calibrated SWR meter or VNA

---

## 2. Where Matching Happens (Critical Concept)

The ATU-130 performs matching **at its INPUT (TX side)**.

| Measurement Location | Typical Result |
|----------------------|----------------|
| Before tuner (TX side) | SWR ≈ 1.0–1.3 |
| After tuner (antenna side) | SWR ≈ 2–3+ |

This is **normal behavior** for an antenna tuner.

---

## 3. RESET vs BYPASS (Not the Same)

### RESET
- Sets LC = 0
- RF still passes through PCB, relays, coupler
- ❌ Not neutral
- ❌ Can worsen SWR

### BYPASS
- Straight-through RF path (as much as layout allows)
- ✔️ Only mode where ATU SWR display has practical meaning (but still not accurate enough)

---

## 4. What the Built-In SWR / Power Meter Really Means

Per the seller description:

> *"...according to BYPASS, straight through mode... test value is approximate... for reference."*

### Practical meaning:
- ✔️ Trend indication only
- ❌ Not calibrated
- ❌ Not reliable in TUNED mode
- ❌ Not comparable to external meters or VNA

---

## 5. NanoVNA Findings (Key Evidence)

Using NanoVNA H4 with proper SOLT calibration:

- RF path **changes** between BYPASS / ON / OFF
- OFF ≠ true bypass
- BYPASS uses a distinct RF path
- Typical insertion loss: **~0.5–0.7 dB**
- Confirms:
  - Relays function correctly
  - No “fake tuning”

---

## 6. Effect of Grounding

Improved grounding resulted in:
- More stable tuning
- Better agreement between CB and ATU readings
- Reduced common-mode current

**Conclusion:**  
The ATU-130 is **highly sensitive to grounding quality**.

---

## 7. Representative Measurements

### Near Resonance (~27–28 MHz)
| Mode | TX SWR | ATU SWR | After ATU |
|----|----|----|----|
| BYPASS | ~1.1 | ~1.1 | ~1.2–1.3 |
| TUNED | ~1.0–1.1 | ~1.05 | ~1.2 |

---

### 30 MHz
| Mode | TX SWR | ATU SWR |
|----|----|----|
| RESET | ~2.3 | ~4.2 |
| TUNED | ~1.0 | ~1.1–1.2 |

---

### 21 MHz (15 m band, CB antenna)
| Mode | TX SWR | ATU SWR | After ATU |
|----|----|----|----|
| BYPASS | ~2.7 | ~3.5 | ~3+ |
| TUNED | ~1.3–1.5 | ~1.05 | ~3 |

Low SWR at the transmitter **does not imply good radiation efficiency**.

---

## Additional NanoVNA Observations (Important but Easy to Miss)

During NanoVNA testing (S1P and S2P measurements with proper SOLT calibration), several **non-obvious but very important behaviors** of the ATU-130 were observed. These are things that **cannot be reliably detected using SWR meters alone**.

---

### 1. OFF ≠ BYPASS (Electrically)

NanoVNA measurements clearly showed that:

- **OFF**, **ON**, and **BYPASS** states all use **different RF paths**
- **OFF is NOT a true bypass**
- Even when powered off, the tuner remains electrically inline and affects:
  - impedance
  - phase
  - return loss

This explains why:
- Simply turning the tuner off can still change SWR
- RESET or OFF may sometimes appear “better” or “worse” without obvious logic

**Conclusion:**  
If a neutral RF path is required, **only BYPASS should be used** — and even that is not ideal.

---

### 2. BYPASS Is Not a “Piece of Wire”

From S21 (insertion loss) measurements:

- Typical insertion loss:
  - **BYPASS:** ~0.6–0.7 dB
  - **ON / TUNED:** ~0.5–0.6 dB

In some frequency ranges, the BYPASS path was **slightly worse** than the tuned path.

This happens because BYPASS still passes through:
- PCB traces
- relay contacts
- the directional coupler

**Conclusion:**  
“Putting the tuner in bypass so it does nothing” does **not** mean zero RF impact.

---

### 3. The ATU Changes Phase, Not Just SWR

Complex S11 and S21 data showed that the ATU-130:

- Changes both:
  - the **magnitude** of the reflection coefficient (|Γ|)
  - the **phase** of the reflection

This means:
- Two configurations can show the **same SWR**
- Yet behave very differently regarding:
  - common-mode currents
  - coax radiation
  - tuning stability

**Conclusion:**  
SWR alone does not describe the full RF behavior.  
The NanoVNA clearly demonstrated this.

---

### 4. Insertion Loss Is Real but Normal

NanoVNA measurements showed a **stable insertion loss** of approximately:

- **0.5–0.7 dB** across the tested HF range

There were:
- no sharp notches
- no parasitic resonances
- no abnormal frequency-dependent loss

**Conclusion:**  
The ATU-130 is electrically healthy.  
The measured loss is normal for a compact relay-based tuner.

---

### 5. The ATU Measures SWR at a Different Electrical Reference Plane

By correlating NanoVNA data with SWR meter readings, it became clear that:

- The ATU’s internal SWR measurement is taken at a **different electrical point**
- It does not correspond to:
  - the transceiver SWR meter
  - an external SWR bridge
  - the VNA reference plane

This explains observations such as:
- ATU reporting SWR ≈ 1.04 while the transmitter actually sees ~1.5
- RESET showing unrealistically low or high SWR values

**Conclusion:**  
This is not a fault — it is a limitation of:
- a non-calibrated directional coupler
- combined with a different measurement point

---

## Overall NanoVNA-Based Conclusions

NanoVNA testing confirmed that:

- ✔️ The ATU-130 functions electrically as designed
- ✔️ Relays and LC networks are genuinely engaged
- ✔️ There is no “fake tuning”
- ❌ OFF, RESET and BYPASS are not equivalent
- ❌ The built-in SWR display is not a measurement instrument

> **Without NanoVNA measurements, it would be very difficult  
> to distinguish “bad readings” from a “bad tuner”.**

---

## 8. Final Verdict

✔️ ATU-130 works as intended  
✔️ Proper impedance transformation  
✔️ Protects the transmitter  
✔️ Enables off-band operation  

❌ Does not fix antenna efficiency  
❌ Built-in SWR meter is **reference only**  
❌ RESET is not bypass  

---

## Additional NanoVNA Observations (Important but Easy to Miss)

During NanoVNA testing (S1P and S2P measurements with proper SOLT calibration), several **non-obvious but very important behaviors** of the ATU-130 were observed. These are things that **cannot be reliably detected using SWR meters alone**.

---

### 1. OFF ≠ BYPASS (Electrically)

NanoVNA measurements clearly showed that:

- **OFF**, **ON**, and **BYPASS** states all use **different RF paths**
- **OFF is NOT a true bypass**
- Even when powered off, the tuner remains electrically inline and affects:
  - impedance
  - phase
  - return loss

This explains why:
- Simply turning the tuner off can still change SWR
- RESET or OFF may sometimes appear “better” or “worse” without obvious logic

**Conclusion:**  
If a neutral RF path is required, **only BYPASS should be used** — and even that is not ideal.

---

### 2. BYPASS Is Not a “Piece of Wire”

From S21 (insertion loss) measurements:

- Typical insertion loss:
  - **BYPASS:** ~0.6–0.7 dB
  - **ON / TUNED:** ~0.5–0.6 dB

In some frequency ranges, the BYPASS path was **slightly worse** than the tuned path.

This happens because BYPASS still passes through:
- PCB traces
- relay contacts
- the directional coupler

**Conclusion:**  
“Putting the tuner in bypass so it does nothing” does **not** mean zero RF impact.

---

### 3. The ATU Changes Phase, Not Just SWR

Complex S11 and S21 data showed that the ATU-130:

- Changes both:
  - the **magnitude** of the reflection coefficient (|Γ|)
  - the **phase** of the reflection

This means:
- Two configurations can show the **same SWR**
- Yet behave very differently regarding:
  - common-mode currents
  - coax radiation
  - tuning stability

**Conclusion:**  
SWR alone does not describe the full RF behavior.  
The NanoVNA clearly demonstrated this.

---

### 4. Insertion Loss Is Real but Normal

NanoVNA measurements showed a **stable insertion loss** of approximately:

- **0.5–0.7 dB** across the tested HF range

There were:
- no sharp notches
- no parasitic resonances
- no abnormal frequency-dependent loss

**Conclusion:**  
The ATU-130 is electrically healthy.  
The measured loss is normal for a compact relay-based tuner.

---

### 5. The ATU Measures SWR at a Different Electrical Reference Plane

By correlating NanoVNA data with SWR meter readings, it became clear that:

- The ATU’s internal SWR measurement is taken at a **different electrical point**
- It does not correspond to:
  - the transceiver SWR meter
  - an external SWR bridge
  - the VNA reference plane

This explains observations such as:
- ATU reporting SWR ≈ 1.04 while the transmitter actually sees ~1.5
- RESET showing unrealistically low or high SWR values

**Conclusion:**  
This is not a fault — it is a limitation of:
- a non-calibrated directional coupler
- combined with a different measurement point

---

## Overall NanoVNA-Based Conclusions

NanoVNA testing confirmed that:

- ✔️ The ATU-130 functions electrically as designed
- ✔️ Relays and LC networks are genuinely engaged
- ✔️ There is no “fake tuning”
- ❌ OFF, RESET and BYPASS are not equivalent
- ❌ The built-in SWR display is not a measurement instrument

> **Without NanoVNA measurements, it would be very difficult  
> to distinguish “bad readings” from a “bad tuner”.**

---

## TL;DR

> **If the SWR before the tuner is low,  
> the ATU-130 is doing its job —  
> even if the antenna side still looks ugly.**

---

*If this document saved you several hours of confusion,  
you are definitely not the first one.*

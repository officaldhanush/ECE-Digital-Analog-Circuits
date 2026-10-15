# Hands-On Electronics & Digital Logic Labs ⚡

A collection of foundational digital logic gates and analog timing circuits built using **Logic Circuit Simulator Pro**, **PROTO**, and verified with **Electrodoc**.

---

## 🛠️ Tools Used
* **Logic Circuit Simulator Pro:** Digital logic gate construction and truth table verification.
* **PROTO:** Interactive SPICE circuit simulation for analog/mixed-signal circuits.
* **Electrodoc:** Component calculations (Resistor Color Codes, LED Series Resistors).

---

## 1. Component Calculations (Electrodoc)
* **$1\text{ k}\Omega$ Resistor Code:** Verified **Brown – Black – Red – Gold** ($\pm 5\%$).
* **LED Current Limiting:** Calculated $R = 350\ \Omega$ for a $9\text{V}$ source, $2\text{V}$ LED forward drop ($V_f$), and $20\text{mA}$ forward current ($I_f$).

$$R = \frac{V_{CC} - V_f}{I_f} = \frac{9\text{V} - 2\text{V}}{0.020\text{A}} = 350\ \Omega$$

---

## 2. Universal Logic Implementation (Logic Circuit Simulator Pro)
Built fundamental logic functions using **only 2-input NAND gates**:

### A. NOT Gate (Inverter)
* **Configuration:** 1 NAND gate with inputs tied together.

### B. AND Gate
* **Configuration:** 2 NAND gates (NAND 1 feeds into an inverter stage).

### C. OR Gate
* **Configuration:** 3 NAND gates using De Morgan's Law ($A + B = \overline{\overline{A} \cdot \overline{B}}$).

---

## 3. Astable 555 Timer Flasher (PROTO)
An analog oscillator circuit generating a continuous square wave output to pulse an LED indicator.

### Circuit Specifications
* **Supply Voltage ($V_{CC}$):** $9\text{ V}$
* **Timing Resistors:** $R_1 = 1\text{ k}\Omega$, $R_2 = 10\text{ k}\Omega$
* **Timing Capacitor:** $C = 10\mu\text{F}$
* **Output Frequency:** $\approx 6.8\text{ Hz}$

---

## 📁 Repository Structure
![555 Timer Flasher Circuit](Screenshot_20261007-175421_PROTO.png)

## 2. Universal Logic Implementation (Logic Circuit Simulator Pro)

The standard NAND gate (the universal gate) was used as the single building block to construct the three fundamental logic functions.

### A. NAND Gate Base Case
Verified the operation of a single 2-input NAND gate.
* **Output:** LOW only when both inputs are HIGH.

![Base 2-Input NAND Gate](<Screenshot_20261007-180637_Logic Circuit Simulator Pro.png>)

### B. AND Gate Construction
Constructed an AND gate using two 2-input NAND gates. The first NAND gate performs the standard NAND function, and its output is fed into a second NAND gate configured as an inverter (both inputs tied together).
* **Configuration:** $A \cdot B = \overline{\overline{A \cdot B}}$
* **Output:** HIGH only when both inputs are HIGH.
![2-NAND AND Gate](<Screenshot_20261007-180644_Logic Circuit Simulator Pro.png>)

### C. OR Gate Construction
Constructed an OR gate using three 2-input NAND gates. Applying De Morgan's Law, the two inputs are first inverted using NAND gates, and those inverted outputs are fed into a third NAND gate.
* **Configuration:** $A + B = \overline{\overline{A} \cdot \overline{B}}$
* **Output:** HIGH when at least one input is HIGH.

![3-NAND OR Gate](<Screenshot_20261007-180657_Logic Circuit Simulator Pro.png>)
---

## 3. Day 02: Exclusive-OR (XOR) Gate Implementation

Constructed an XOR gate using 4 universal NAND gates to perform exclusive addition ($A \oplus B$).

### A. 4-NAND XOR Gate Construction
* **Boolean Expression:** $Y = A \oplus B = A\overline{B} + \overline{A}B = \overline{\overline{A \cdot \overline{A \cdot B}} \cdot \overline{B \cdot \overline{A \cdot B}}}$
* **Truth Table Verification:**
  * $A=0, B=0 \implies \text{Output } 0$ (OFF)
  * $A=0, B=1 \implies \text{Output } 1$ (ON)
  * $A=1, B=0 \implies \text{Output } 1$ (ON)
  * $A=1, B=1 \implies \text{Output } 0$ (OFF)

![4-NAND XOR Gate](<Screenshot_20261008-072815_Logic Circuit Simulator Pro.png>)

### B. Resistor Color Code & LED Current Limiting (Electrodoc)

Calculated theoretical resistor values for physical component identification and LED protection.

#### 1. Resistor Color Code Identification
* **Bands:** Brown (1), Black (0), Red ($\times 100$), Gold ($\pm 5\%$)
* **Decoded Value:** $1\text{ k}\Omega \pm 5\%$ ($950\,\Omega \text{ to } 1050\,\Omega$)

![Resistor Color Code](<Screenshot_20261008-075414_Electrodoc.png>)

#### 2. LED Series Resistor Calculation
* **Parameters:** Supply Voltage ($V_S$) = $9\text{ V}$, Forward Voltage ($V_F$) = $2\text{ V}$, Forward Current ($I_F$) = $20\text{ mA}$
* **Calculation:** $R = \frac{V_S - V_F}{I_F} = \frac{9\text{ V} - 2\text{ V}}{0.02\text{ A}} = 350\,\Omega$
* **Power Dissipation:** Resistor $P(R) = 140\text{ mW}$, LED $P(\text{LED}) = 40\text{ mW}$

![LED Resistor Calculation](<Screenshot_20261008-075403_Electrodoc.png>)

# Day 03: Basics of Circuit Simulation

## 1. Proto Simulation
- **Observations:** Current dots flowing clockwise. LED lit up without overcurrent.
  ![PROTO Circuit Simulation](Screenshot_20261009-073344_PROTO.png)

## Day 04:AC Circuits, and Universal Gates

### 1. Proto Simulation (AC Circuit & RC Filter)
![PROTO AC Circuit Simulation](Screenshot_20261010-064412_PROTO.png)

### 2. Logic Circuit Simulator Pro (NAND Gate as Inverter)

- **Input 0 $\rightarrow$ Output 1 (Bulb ON):**
  ![NAND Gate State 0](Screenshot_20261010-064837_Logic%20Circuit%20Simulator%20Pro.png)

- **Input 1 $\rightarrow$ Output 0 (Bulb OFF):**
  ![NAND Gate State 1](Screenshot_20261010-064841_Logic%20Circuit%20Simulator%20Pro.png)

## Day 05: Parallel Circuits, Rectifiers, and XOR Gates

### 1. ElectroDoc (Parallel Resistors & Power Calculation)
- **Equivalent Resistance Calculation:**
  ![ElectroDoc Resistance](Screenshot_20261011-062019_Electrodoc.png)

- **Total Power Calculation:**
  ![ElectroDoc Power](Screenshot_20261011-062030_Electrodoc.png)

### 2. Proto (AC Half-Wave Rectifier)
- **Observation:** The diode blocks the negative AC cycle, producing positive rectified voltage pulses across the load resistor.
  ![Proto Rectifier](Screenshot_20261011-064226_PROTO.png)

### 3. Logic Circuit Simulator Pro (XOR Gate)
- **Truth Table Verification:**
  | Input A | Input B | Output |
  |---|---|---|
  | 0 | 0 | 0 (OFF) |
  | 0 | 1 | 1 (ON)  |
  | 1 | 0 | 1 (ON)  |
  | 1 | 1 | 0 (OFF) |

- **XOR Gate Simulation (Inputs 0, 1 $\rightarrow$ Output ON):**
  ![XOR Gate Simulation](Screenshot_20261011-062213_Logic%20Circuit%20Simulator%20Pro.png)
## Day 06:Bridge Rectifiers, and SR Latches
### 2. Proto (Full-Wave Bridge Rectifier)
- **Observation:** The 4-diode bridge configuration successfully inverts all negative AC cycles into positive peaks, providing a continuous pulsating DC waveform across the load resistor.
  ![Proto Bridge Rectifier](Screenshot_20261012-165233_PROTO.png)

### 3. Logic Circuit Simulator Pro (SR Latch Memory Cell)
- **Observation:** Cross-coupled NOR gates form a feedback loop that retains (latches) its digital state even after input pushbuttons/switches return to 0.
  ![SR Latch Memory](Screenshot_20261012-085919_Logic%20Circuit%20Simulator%20Pro.png)

## Day 07: Clocked D-Latch and Filtered DC Power Supply

### 1. Proto (Capacitor Filter / Ripple Smoothing)
- **Observation:** Adding a parallel filter capacitor (10 µF) across the load resistor successfully smoothed the pulsating DC waveform from the bridge rectifier into a steady, continuous DC voltage rail with minimal ripple.
  ![Proto Filtered DC Power Supply](Screenshot_20261013-074835_PROTO.png)

### 2. Logic Circuit Simulator Pro (Clocked D-Latch)
- **Observation:** Integrated a clock/enable signal with gated NAND logic, allowing the circuit to selectively capture and hold data input ($D$) only when the clock is high, preventing illegal states and creating a stable memory register.
  ![Clocked D-Latch](Screenshot_20261013-073519_Logic%20Circuit%20Simulator%20Pro.png)

# Day 8: Master-Slave Edge-Triggered D Flip-Flop

## Overview
As part of my mobile-based Electronics and Communication Engineering (ECE) practical series, Day 6 focuses on transitioning from level-sensitive storage elements (latches) to edge-triggered sequential logic (flip-flops). Level-sensitive latches suffer from transparency issues and race conditions when clock signals are held high. To solve this, a **Master-Slave configuration** is implemented to ensure data is sampled and updated precisely on a specific clock edge.

---

## Objectives
- Design and simulate a Master-Slave D Flip-Flop using **Logic Circuit Simulator Pro** on mobile.
- Implement master-slave latch cascading to eliminate data transparency windows.
- Configure clock phase inversion to achieve precise edge-triggered synchronization.
- Verify the characteristic behavior where data is captured on the rising edge and held steady against input fluctuations.

---

## Circuit Simulation & Evidence
![Master-Slave D Flip-Flop Simulation](Screenshot_20261014-083522_Logic%20Circuit%20Simulator%20Pro.png)[cite: 4]

---

## Circuit Architecture & Design

### 1. Component Breakdown
* **Master Latch:** Built using cross-coupled NAND gates connected to the primary Data ($D$) input and the primary Clock ($CLK$) signal.
* **Slave Latch:** A second identical D-latch connected directly to the output of the master stage.
* **Clock Inversion:** The primary clock signal is fed directly into the master latch, while an inverted clock signal ($\overline{CLK}$) generated via a NOT gate drives the slave latch.

### 2. Data Flow Chain
[ Data Switch (D) ] ---> [ Master Latch ] ---> [ Slave Latch ] ---> [ Output LED (Q) ]


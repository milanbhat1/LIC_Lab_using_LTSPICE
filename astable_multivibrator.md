# Experiment 5 – Design and Analysis of Astable Multibrator Circuit

## Contents
- Aim, Components Required
- Theory of Differential Amplifier
- Circuit Diagram with Specifications
- Working Principle
- Steps for DC, Transient, and AC Analysis in LTSpice
- Analysis of Circuit Design
- Circuit Diagram Simulation Results
- Results, Inference, and Conclusion

---

## Part A: Basic Current Mirror Design

### Aim
To design a basic current mirror for the following specifications:
- **Supply Voltage (VDD):**  
- **Power Consumption (P):**   
- **Gain (Av):** 

**Analysis Performed:**
- DC Analysis
- Transient Analysis
- AC Analysis

---

### Components Required
- 555 Timer
- Voltage Supply
- Current Source
- Connecting Wires

---

### Theory

# Astable Multivibrator

An **astable multivibrator** is a continuously oscillating circuit with no stable states. It generates a square wave without requiring any external triggering and is commonly built using transistors, capacitors, and resistors.

- Two cross-coupled transistors alternately turn **on** and **off**, forming a regenerative feedback loop.
- Capacitors connected between each transistor's collector and the other's base cause time delays, setting the **oscillation frequency**.
- No stable states exist — both transistors continuously switch, creating a free-running oscillator.


![astable](https://github.com/user-attachments/assets/af8379a0-a902-4816-a30d-c1ec110189bd)


---


### Working Principle (Point-wise)

A 555 timer IC configured in **astable mode** continuously switches between high and low output states, generating a square wave without external triggering.

- Two internal comparators and a flip-flop control the timing cycle.
- External resistors **R1**, **R2**, and capacitor **C** set the output frequency and duty cycle.
- The capacitor charges through **R1 + R2** and discharges through **R2** only.
- Output toggles when capacitor voltage crosses 1/3 VCC (low threshold) and 2/3 VCC (high threshold).

**Key Timing Formulas:**


- **T_high**: Time output is HIGH
- **T_low**: Time output is LOW
- **f**: Output frequency
- **Duty Cycle (%)** = (T_high / T_total) × 100
---

## LTSpice Simulation Setup

### DC Analysis
1. Load the schematic.
2. Simulate > Edit Simulation Cmd > `.op`
3. Place `.op` command on schematic.
4. Verify all parameters.
5. Run simulation.

### Transient Analysis
1. Load schematic.
2. Simulate > Edit Simulation Cmd > `.tran 10m`
3. Add input pulse signal.
4. Run simulation.
5. Observe waveforms.

### AC Analysis
1. Simulate > Edit Simulation Cmd > `.ac dec 10 1 1T`
2. Set input source AC amplitude = 1.
3. Run simulation.
4. Analyze frequency response and -3dB bandwidth.

---

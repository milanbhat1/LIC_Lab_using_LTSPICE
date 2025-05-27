# Experiment 5: Monostable and Astable Multivibrators Using 555 Timer IC

## Contents
- [Aim](#aim)
- [Theory](#theory)
  - [Monostable Multivibrator](#monostable-multivibrator)
  - [Astable Multivibrator](#astable-multivibrator)
- [Working Principle](#working-principle)
- [Design Calculations](#design-calculations)
- [Circuit Diagrams](#circuit-diagrams)
- [Simulation Waveforms](#simulation-waveforms)
  - [Case 1](#case-1)
  - [Case 2](#case-2)
  - [Case 3](#case-3)
- [Inference](#inference)

---

## Aim
To design and analyze monostable and astable multivibrator circuits using a 555 timer IC to generate an output pulse width of 0.5 ms.

---

## Theory

### Monostable Multivibrator
A monostable multivibrator has only one stable output state. When a trigger pulse is applied, the output switches from the stable state (usually LOW) to a temporary HIGH state. This HIGH state persists for a specific duration defined by an external resistor (R) and capacitor (C), after which the output automatically returns to the original stable state. The duration (T) of the output pulse is given by:

```
T = 1.1 × R × C
```

This configuration is ideal for generating accurate, one-time pulses in response to an input trigger.

---

### Astable Multivibrator
An astable multivibrator continuously switches between HIGH and LOW states without requiring any external trigger. It behaves like an oscillator, generating a square wave output. The output frequency and duty cycle are determined by two resistors (Ra and Rb) and a capacitor (C). The ON time (T_high) and OFF time (T_low) are given by:

```
T_high = 0.693 × (Ra + Rb) × C  
T_low  = 0.693 × Rb × C
```

This configuration is commonly used for generating clock pulses.

---

## Working Principle

- **Monostable Mode**: When the trigger input (pin 2) is pulled below 1/3 Vcc, the 555 timer’s output switches HIGH for a fixed duration, during which the capacitor charges. Once the capacitor voltage exceeds 2/3 Vcc, the timer resets, pulling the output LOW.

- **Astable Mode**: The capacitor alternately charges and discharges through resistors Ra and Rb. This causes the output to toggle continuously between HIGH and LOW.

- **Edge Detection & Signal Conditioning**: A differentiator circuit is used to detect rising edges, and a negative clipper ensures only negative spikes are passed to trigger the monostable circuit.

---

## Design Calculations

### Monostable Multivibrator:
Given pulse width T = 0.5 ms and C = 0.1 µF,

```
T = 1.1 × R × C  
=> R = T / (1.1 × C)  
=> R = 0.5 ms / (1.1 × 0.1 µF)  
=> R ≈ 4.545 kΩ
```

---

## Circuit Diagrams

### Monostable Multivibrator:
![Monostable Circuit](https://github.com/user-attachments/assets/bb37f20b-66b4-4744-901d-e0262de2926d)

### Combined Astable → Differentiator → Clipper → Monostable System:
![Combined Circuit](https://github.com/user-attachments/assets/b07bcbbe-72dd-4548-a828-e1ff5dc9cebd)

---

## Simulation Waveforms

### Case 1
- **ON Time**: 0.2 ms  
- **OFF Time**: 0.3 ms  
![Waveform Case 1](https://github.com/user-attachments/assets/bdcbd7d8-b042-44d8-a02f-16989a367a90)

### Case 2
- **ON Time**: 0.1 ms  
- **OFF Time**: 0.05 ms  
- **Capacitor**: 0.1 µF  
![Waveform Case 2](https://github.com/user-attachments/assets/bb0dabe9-f63f-4be1-9e6b-fbbc78f23174)

### Case 3
- **Inverted Astable Output to achieve OFF > ON**  
![Waveform Case 3](https://github.com/user-attachments/assets/62330045-4a0a-422d-b977-9699a629bb00)  
![Inverted Signal](https://github.com/user-attachments/assets/5974cd20-b140-48e9-b307-9e661e8e4906)

---

## Inference

| Case | Configuration                        | Observations |
|------|--------------------------------------|--------------|
| 1    | Direct astable output                | Generated square waves with standard RC control. |
| 2    | Fast pulses using small R, C         | Demonstrated the need for precise, small-value components. |
| 3    | Output inversion using NOT gate      | Used inversion to meet OFF > ON requirement. |

**Key Takeaways**:
- 555 timer is limited in certain pulse width configurations.
- Signal shaping (differentiator & clipper) is crucial for clean triggering.
- Inversion allows flexibility in waveform control.

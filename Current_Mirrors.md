# Experiment 4 – Design and Analysis of Current Mirror Circuit

## Contents
- Aim, Components Required
- Theory of Differential Amplifier
- Circuit Diagram with Specifications
- Working Principle
- Steps for DC, Transient, and AC Analysis in LTSpice
- Analysis of Circuit Design
- Gain Calculation
- Circuit Diagram Simulation Results
- Results, Inference, and Conclusion

---

## Part A: Basic Current Mirror Design

### Aim
To design a basic current mirror for the following specifications:
- **Supply Voltage (VDD):** 1.8V  
- **Power Consumption (P):** ≤ 1mW  
- **Gain (Av):** -10 V/V

**Analysis Performed:**
- DC Analysis
- Transient Analysis
- AC Analysis
- Comparison between Circuit 1 and 2

---

### Components Required
- MOSFET (CMOSN)
- Voltage Supply
- Current Source
- Connecting Wires

---

### Theory

A current mirror is a key analog circuit block used to replicate a reference current across one or more branches. It comprises two or more MOSFETs, with one operating as a diode (gate connected to drain), setting a gate-source voltage (VGS) which is then mirrored to other transistors.

- The diode-connected MOSFET establishes **IREF**.
- Identical transistors ensure that **IOUT ≈ IREF** if mismatch and channel-length modulation are negligible.
- Used in biasing circuits, amplifiers, and analog signal paths.

**Cascode mirrors** improve output resistance and accuracy by shielding the output transistor from voltage variations but require additional headroom.

![Screenshot 2025-03-24 003654](https://github.com/user-attachments/assets/1b6d7118-2aad-46a0-a3e4-4c608eb9ac4f)

---


### Working Principle (Point-wise)

1. Diode-connected MOSFET (M1) sets up the reference current (IREF).
2. VGS of M1 is applied to M2 (mirror transistor).
3. Identical transistors → IOUT = IREF.
4. M2 must remain in saturation for constant output current.
5. Mismatch and CLM affect precision.
6. Cascode mirrors improve output resistance.
7. Widely used in analog designs.

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

## Design Calculation

**Given:**

    Given- Vdd=1.8V , P<=1mV
    So, Itotatl = P/Vdd
                = 1m/1.8
        Itotatl = 0.555mA
                
    W.K.T, Itotatl = Iref + Ix


### Circuit 1: 1:1 Current Mirror


    Itotatl = Iref + Ix
    Iref = Ix
    So, Iref = Itotatl/2
             = 0.555m/2
        Iref = 0.2775mA

<img width="650" alt="ckt1" src="https://github.com/user-attachments/assets/e93b4af4-b1d7-4389-9d2a-78698652176c" />

#### DC Analysis:
- L = 180nm, 500nm, 1μm respectively
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/9a4775a2-1450-46d6-a41c-0c69149a9210" />

<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/c405faa5-9296-4b7d-b1de-fa16865dc779" />

<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/c3f3ac39-ad31-4096-b4a6-9365542a7656" />

#### Transient Analysis:
- L = 180nm, 500nm, 1μm respectively
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/74843fba-d993-4ce2-8808-898e9d022a99" />

<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/3201c1fa-34b0-4563-8588-1d64a859cd0c" />

<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/c9b2b23b-7a19-4665-9b0c-fe7bafb78f0d" />


### AC Analysis:

<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/49cafc3f-7680-4869-a718-a980978926a9" />

    Gain,Av = 23.382dB
    Av(-3dB) = 20.382dB
    Bandwidth,B.W = 1.9352GHz

    
---

### Circuit 2: 1:2 Current Mirror

    Itotatl = Iref + Ix
    (2)*Iref = Ix
    So, Iref = Itotatl/3
             = 0.555m/3
        Iref = 0.185mA

        Ix = 0.370mA

<img width="650" alt="ckt1" src="https://github.com/user-attachments/assets/2be543dd-1383-4021-a322-dd0de23219c2" />


#### DC Analysis:
- L = 180nm, 500nm, 1μm respectively
<img width="600" alt="dc2" src="https://github.com/user-attachments/assets/efd4d4aa-8a90-4d27-9f93-8174a86e53ec" />

<img width="600" alt="500_2" src="https://github.com/user-attachments/assets/f041c81d-8b81-444f-9007-bd161a08f6d0" />
![500_2]()

<img width="600" alt="1u_2" src="https://github.com/user-attachments/assets/289cc8c4-8860-400a-9033-1aa1f6e31bc3" />




#### Transient Analysis:
- L = 180nm, 500nm, 1μm respectively
<img width="600" alt="tr2" src="https://github.com/user-attachments/assets/54db8572-167b-41f5-a17c-1b2ad6d73ce6" />

<img width="600" alt="500_2tr" src="https://github.com/user-attachments/assets/c64492d8-88e1-4c59-93cf-461980ef983f" />

<img width="600" alt="1u_2tr" src="https://github.com/user-attachments/assets/d6c5c743-e21b-4b58-816f-e1fbd82059b3" />



### AC Analysis:
<img width="600" alt="ac2" src="https://github.com/user-attachments/assets/53578d83-83eb-4389-9493-9464e69e73e3" />

    Gain,Av = 23.371dB
    Av(-3dB) = 20.404dB
    Bandwidth,B.W = 1.434GHz

--- 


## Inference

### 1:1 Current Mirror (Practical vs Theoretical)
| W/L (μm/nm)      | Iref (μA) | Ix (Expected) | Ix (Practical) | Vx (V)     | Vout (V)   |
|------------------|-----------|---------------|----------------|------------|------------|
| 3.577 / 180      | 277.5     | 277.5         | 277.545        | 0.542983   | 0.541344   |
| 9.150 / 500      | 277.5     | 277.5         | 277.545        | 0.542983   | 0.541344   |
| 16.073 / 1000    | 277.5     | 277.5         | 277.515        | 0.542983   | 0.541344   |

### 1:2 Current Mirror
| W1/L (μm/nm)     | W2,W3/L   | Ix (Expected) | Ix (Practical) | Vx (V)     | Vout (V)   |
|------------------|-----------|---------------|----------------|------------|------------|
| 2.340 / 180      | 4.79 /180 | 370           | 370.3          | 0.6936     | 0.74896    |
| 6.082 / 500      | 12.2 /500 | 370           | 370.0          | 0.6065     | 0.619375   |
| 10.718 / 1000    | 21.5 /1μm | 370           | 370.9          | 0.5434     | 0.533236   |

---

## Conclusion

### 1:1 Current Mirror
- **W/L Increase → Better Matching**  
- Suitable for **low-power analog systems**

### 1:2 Current Mirror
- **Output current scaled x2**  
- **Power consumption higher**  
- Slight mismatch due to **CLM & Vth variations**

### Summary Table

| Feature           | 1:1 Mirror       | 1:2 Mirror       |
|------------------|------------------|------------------|
| Current Ratio     | 1:1              | 1:2              |
| Output Current    | = Iref           | = 2 × Iref       |
| W/L Ratio         | Equal            | Output MOSFET ×2 |
| Power Consumption | Lower            | Higher           |
| Accuracy          | Higher           | Slightly Lower   |

---


## Part B: Differential Amplifier with Current Mirror

### Aim
To design a differential amplifier with:
- **VDD = 2.5V**, **P ≤ 3mW**
- **Vincm = 1.3V**, **VoutCM = 1.4V**
- **Vp = 0.5V**

**Analysis Performed:**
- DC, Transient, and AC Analysis
- Comparison between Circuit 1, 2, 3

---

### Components Required
- CMOSN (NMOS)
- Resistors: 1.83kΩ × 2, 416.66Ω
- Voltage Source
- Current Source
- Wires

---

### Theory

A differential amplifier with a current mirror uses a differential pair (M1, M2) and current mirror (M3, M4) for active loading. This boosts gain by redirecting current differences at the output without needing large resistors.

- **Current mirror acts as dynamic load**
- **Enhances gain and common-mode rejection**
- Used in op-amps, analog filters, signal processing blocks

---

### Design:

    Given- Vdd=1.8V , P<=1mV
    So, ISS = P/Vdd
                = 3m/2.5
        ISS = 1.2mA
                
    
Here we are making 1:1 Current Mirror ratio so, ISS = Iref.

     Iref = 1.2mA

---


Circuit Diagram:

<img width="650" alt="ac2" src="https://github.com/user-attachments/assets/9d01e6c5-aad3-46d7-80d0-9b97fd3caeae" />

---

### DC Analysis:

<img width="600" alt="ac2" src="https://github.com/user-attachments/assets/5a8a6913-74fb-4254-a966-c8b5a7a4b14a" />


### Transient Analysis:

<img width="600" alt="ac2" src="https://github.com/user-attachments/assets/500053d2-d25d-4c52-a9fd-5ba7b19f12b8" />

**Gain Calculation:**

    Gain,Av = Vout/VIn
            = (1.7018-0.8726)/(1.349-1.25)
            = 8.375
    Gain in dB = 20log(Av)
               = 20log(8.375)
               = 18.459

### AC Analysis:

<img width="600" alt="ac2" src="https://github.com/user-attachments/assets/2d3e7f4f-1c1e-4259-a870-55030041acc3" />

**Bandwidth of Av:**

      Bandwidth = 1MHz
      
**Bandwidth of -3dB gain:**

      Bandwidth = 7.9614GHz
---


## Inference:

  
**Node Values:**

| **Parameter**       | **Values**  |  
|---------------------|-------------|  
| **Vout1**          | 1.400V       |  
| **Vout2**          | 1.400V       |  
| **V(Vp)**          | 0.5009V      |  
| **Id(M1)**         | 0.000601 A   |  
| **Id(M2)**         | 0.000601 A   |  
| **Total Current (ISS)** | 0.001202 A  | 


**Each Transistor Width (W) and Length(L) values:**

| Transistor | Width (W) [μm] | Length (L) [nm] |
|------------|--------------|--------------|
| M1         |  7.7165       |    180     |
| M2         |  7.7165u       |   180       |
| M3         |  51.45       |    180      |
| M4         |  49.1       |     180    |
| M5         |  1.45395       |   180       |
| M6         |  1.45395       |   180       |

- **M1 & M2**: Used in the **differential amplifier**.
- **M3 & M4**: Part of the **current mirror**.
- **M5 & M6**: Additional transistors for circuit stability or gain adjustment.

  
**Compararison between Differential Amplifier with and Without Current Mirror:**

| **Parameter**            | **Without Current Mirror** | **With Current Mirror** | **Explanation** |  
|--------------------------|---------------------------|-------------------------|-----------------|  
| **Gain (Av)**           | Lower                      | Higher                  | A current mirror improves biasing, leading to better gain. |  
| **CMRR**                | Lower                      | Higher                  | Better current source improves common-mode rejection ratio. |  
| **Power Consumption**   | Higher                     | Lower                   | A current mirror reduces wasted current, improving efficiency. |  
| **Output Swing**        | Limited                    | Improved                 | A current mirror provides better bias stability, enhancing output range. |  

---

### **Conclusion**  

- **Improved Performance:** The use of a current mirror in a differential amplifier enhances gain, common-mode rejection, and stability.  

- **Better Power Efficiency:** A current mirror reduces power consumption by providing an efficient biasing technique.  

- **Enhanced Output Swing:** The output voltage range improves due to better bias stability and reduced variations.  

- **Higher CMRR:** The ability to reject common-mode signals increases significantly, making the circuit more reliable.  

- **Preferred for Precision Applications:** Due to improved performance, differential amplifiers with current mirrors are widely used in high-precision analog circuits like Operational Transconductance Amplifiers (OTA). 

---




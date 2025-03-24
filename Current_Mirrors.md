# Experiment 4 - Design and Analysis of Current Mirror Circuit

## Contents:
- Aim, Components Required
- Theory of Differential Amplifier
- Circuit Diagram with Specifications
- Working Principle
- Steps For DC Analysis,Transient Analysis and AC analysis in LTSPICE
- Analysis of Circuit Design
- Gain Calculation
- Circuit Diagram Simulation Results
- Results, Inferences, and Conclusion
  
# Part A:

### Aim:
To Design a basic Current Mirror for the following specification:
- Supply Voltage (VDD) = 1.8V
- Power Consumption (P) <= 1mW
- Gain,Av = -10V/V

#### Perform:
- DC Analysis
- Transient Analysis
- AC analysis
- Comparision between the Circuit 1,2

### Theory:

A current mirror is a fundamental circuit used in analog design to replicate a reference current with high accuracy. It consists of two MOSFETs: one configured as a diode-connected transistor, which sets a gate-source voltage (VGS) corresponding to the reference current (IREF), and another transistor that mirrors this current to an output. The principle relies on matching identical MOSFETs, ensuring that the output current closely follows the reference current if channel-length modulation is negligible. Current mirrors are widely used in biasing circuits, operational amplifiers, and analog signal processing due to their ability to provide a stable current source independent of temperature and process variations. However, mismatches between transistors and finite output resistance can introduce errors, requiring careful layout and design considerations.

![Screenshot 2025-03-24 003654](https://github.com/user-attachments/assets/1b6d7118-2aad-46a0-a3e4-4c608eb9ac4f)

To improve performance, cascode current mirrors are used, which incorporate an additional transistor to shield the output device from voltage variations, significantly increasing output resistance. This minimizes the effect of channel-length modulation, improving current matching and reducing deviations. However, cascode mirrors require additional voltage headroom, making them less suitable for low-voltage applications. To address this, low-voltage cascode techniques use special biasing methods to generate the required gate voltages while maintaining high output resistance. Advanced current mirrors, such as Wilson and regulated cascode mirrors, further enhance accuracy and stability. These techniques ensure better performance in precision analog circuits, including operational amplifiers, voltage references, and mixed-signal systems.

### Working Principle:

Working Principle of Current Mirror (Point-wise)

**1. Reference Current Generation –** A diode-connected MOSFET (M1) is used to establish a stable reference current (IREF).

**2. Voltage Mirroring –** The gate-source voltage (VGS) of M1 is applied to the second MOSFET (M2).

**3. Current Replication –** Since both MOSFETs have the same VGS and are identical, M2 mirrors IREF to its drain.

**4. Saturation Operation –** M2 operates in saturation region, ensuring a nearly constant output current.

**5. Accuracy Factors –** Mismatch, channel-length modulation, and temperature variations can affect precision.

**6. Improved Performance –** Cascode current mirrors enhance output resistance, reducing variations in VDS.

**7. Applications –** Used in biasing, amplifiers, and analog signal processing circuits.


### Steps For DC Analysis,Transient Analysis and AC analysis in LTspice:

#### Steps for DC Analysis:
1. Open LTspice and load the MOS differential amplifier circuit schematic.
2. Set Up the Simulation Command:
      - Click on Simulate > Edit Simulation Cmd.
      - In the DC op pnt tab, select .op (DC Operating Point Analysis).
      - Click OK, and place the generated command **.op** on the schematic.
3. Check the Component Parameters:
      - Ensure that the MOSFET models and resistor values match the given specifications.
      - Verify that the power supply voltages (Vdd, Vicm) are correctly set.
4. Run the Simulation:
      - Click on Run

#### Steps for Transient Analysis:

1. Open LTspice  and load the circuit schematic.
2. Set Up the Simulation Command:
   - Click on Simulate > Edit Simulation Cmd.
   - In the Transient tab, enter a stop time **e.g., 10ms** and a step time if needed.
   - Click OK, and place the generated command **.tran 10m** on the schematic.
3. Apply an Input Signal:
   - Set a pulse voltage source at the input nodes.
   - Define the frequency and amplitude of the input signal.
4. Run the Simulation:
   - Click on Run.
5. Analyze the Waveforms:
   - Observe the output waveforms at the differential output nodes.
   - Verify the response and note the phase shift and gain.
  
#### Steps for AC Analysis: 
1. Set Up the Simulation Command:
   - Click on Simulate > Edit Simulation Cmd.
   - In the AC Analysis tab, select Type of Sweep Decade.
   - Enter the number of points per decade and the frequency range **1Hz to 1THz**.
   - Click OK, and place the generated command **.ac dec 10 1 1T** on the schematic.
2. Set AC Parameters for Input Source:
   - Ensure the input voltage source is set with an AC amplitude (1).
3. Run the Simulation:
   - Click on Run.
5. Analyze the Frequency Response:
   - Observe the gain.
   - Calculate the Bandwidth for -3dB gain.
  
### Design:

    Given- Vdd=1.8V , P<=1mV
    So, Itotatl = P/Vdd
                = 1m/1.8
        Itotatl = 0.555mA
                
    W.K.T, Itotatl = Iref + Ix

#### For Circuit 1 with Current Mirror Ratio 1:1 :

    Itotatl = Iref + Ix
    Iref = Ix
    So, Iref = Itotatl/2
             = 0.555m/2
        Iref = 0.2775mA

<img width="650" alt="ckt1" src="https://github.com/user-attachments/assets/e93b4af4-b1d7-4389-9d2a-78698652176c" />

### DC Analysis:

#### For L = 180nm:
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/9a4775a2-1450-46d6-a41c-0c69149a9210" />

#### For L = 500nm:
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/c405faa5-9296-4b7d-b1de-fa16865dc779" />

### For L = 1μm:
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/c3f3ac39-ad31-4096-b4a6-9365542a7656" />

### Transient Analysis:

#### For L = 180nm:
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/74843fba-d993-4ce2-8808-898e9d022a99" />

#### For L = 500nm:
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/3201c1fa-34b0-4563-8588-1d64a859cd0c" />

### For L = 1μm:
<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/c9b2b23b-7a19-4665-9b0c-fe7bafb78f0d" />


### AC Analysis:

<img width="600" alt="ckt1" src="https://github.com/user-attachments/assets/49cafc3f-7680-4869-a718-a980978926a9" />

    Gain,Av = 23.382dB
    Av(-3dB) = 20.382dB
    Bandwidth,B.W = 1.9352GHz


#### For Circuit 2 with Current Mirror Ratio 1:2 :

    Itotatl = Iref + Ix
    (2)*Iref = Ix
    So, Iref = Itotatl/3
             = 0.555m/3
        Iref = 0.185mA

        Ix = 0.370mA

<img width="650" alt="ckt1" src="https://github.com/user-attachments/assets/2be543dd-1383-4021-a322-dd0de23219c2" />


### DC Analysis:

#### For L = 180nm:
<img width="600" alt="dc2" src="https://github.com/user-attachments/assets/efd4d4aa-8a90-4d27-9f93-8174a86e53ec" />

#### For L = 500nm:
<img width="600" alt="500_2" src="https://github.com/user-attachments/assets/f041c81d-8b81-444f-9007-bd161a08f6d0" />
![500_2]()


### For L = 1μm:
<img width="600" alt="1u_2" src="https://github.com/user-attachments/assets/289cc8c4-8860-400a-9033-1aa1f6e31bc3" />




### Transient Analysis:

#### For L = 180nm:
<img width="600" alt="tr2" src="https://github.com/user-attachments/assets/54db8572-167b-41f5-a17c-1b2ad6d73ce6" />

#### For L = 500nm:
<img width="600" alt="500_2tr" src="https://github.com/user-attachments/assets/c64492d8-88e1-4c59-93cf-461980ef983f" />

### For L = 1μm:
<img width="600" alt="1u_2tr" src="https://github.com/user-attachments/assets/d6c5c743-e21b-4b58-816f-e1fbd82059b3" />



### AC Analysis:
<img width="600" alt="ac2" src="https://github.com/user-attachments/assets/53578d83-83eb-4389-9493-9464e69e73e3" />

    Gain,Av = 23.371dB
    Av(-3dB) = 20.404dB
    Bandwidth,B.W = 1.434GHz

## Inference:

### **MOSFET Parameter Comparison for 1:1 Current Mirror:**



| W/L (μm/nm)      | Iref (μA) | Ix (Expected) (μA) | Ix (Practical) (μA) | Vx (V)   | Vout (V)  |
|------------------|------------|----------------|----------------|--------|--------|
| 3.577 / 180     | 277.5      | 277.5          | 277.545        | 0.542983 | 0.541344 |
| 9.150 / 500     | 277.5      | 277.5          | 277.545        | 0.542983 | 0.541344 |
| 16.07354 / 1000 | 277.5      | 277.5          | 277.515        | 0.542983 | 0.541344 |


### **MOSFET Parameter Comparison for 1:2 Current Mirror:**

| W1 (μm) / L (nm) | W2, W3 (μm) / L (nm) | Ix (Expected) (μA) | Ix (Practical) (μA) | Vx (V)  | V(vout) (V) |
|------------------|------------------|----------------|----------------|---------|------------|
| 2.3404 / 180    | 4.79 / 180       | 370            | 370.3          | 0.6936  | 0.74896    |
| 6.082 / 500     | 12.2 / 500       | 370            | 370            | 0.6065  | 0.619375   |
| 10.7185 / 1000  | 21.5 / 1000      | 370            | 370.9          | 0.5434  | 0.533236   |


## Conclusion:

### **1:1 Current Mirror**

1. **Effect of W/L Ratio:** Increasing the **W/L ratio** improves current matching accuracy and reduces output resistance variations, enhancing performance.
2. **Power Efficiency:** The circuit operates efficiently within a **1.8V supply**, making it suitable for **low-power analog applications**.


### **1:2 Current Mirror**
1. **Current Scaling:** The **output current is ideally twice the reference current**, as designed for a 1:2 current mirror ratio.
2. **Deviation from Ideal Ratio:** Minor mismatches are observed due to **process variations, threshold voltage differences, and channel-length modulation**.
3. **Higher Power Dissipation:** Since the output current is doubled, **power consumption is higher** compared to a 1:1 current mirror.


### **Difference Between 1:1 and 1:2 Current Mirrors**
| Feature               | 1:1 Current Mirror | 1:2 Current Mirror |
|----------------------|------------------|------------------|
| Current Ratio       | 1:1               | 1:2               |
| W/L Ratio          | Equal for both MOSFETs | Output MOSFET W/L is twice |
| Output Current     | Same as reference  | Twice the reference |
| Power Consumption  | Lower              | Higher due to increased current |
| Accuracy           | Higher             | More prone to mismatches |



# Part B:



    



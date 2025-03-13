# Experiment 3 - Differential Amplifier

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
  
### Aim:
To Design a basic diffrential amplifier for the following specification:
- Supply Voltage (VDD) = 2.5V
- Power Consumption (P) <= 3mW
- Input Common Mode Voltage (Vincm) = 1.3V
- Output Differential Common Mode Voltage (V0cm) = 1.4V
- Vp = 0.5V
  
#### Perform:
- DC Analysis
- Transient Analysis
- AC analysis
- Comparision between the Circuit 1,2,3

### Components Required:
- MOSFET (CMOSN)
- Resistors: 1.83 kΩ x 2, 416.66 Ω
- Voltage supply
- current Source
- Connecting wires

### Theory:
A MOS differential amplifier is a fundamental building block in analog circuits, extensively used in operational amplifiers and sensor interfaces. It consists of two MOSFETs sharing a common current source, allowing it to amplify the difference between two input signals while rejecting common-mode noise. This configuration enhances signal integrity and noise immunity, making it ideal for high-precision applications.

Differential amplifiers exhibit excellent common-mode rejection ratio (CMRR) and can function in different modes depending on the biasing and load conditions. Their small-signal and large-signal behavior significantly influence the overall system performance in communication and control circuits.

  ![Screenshot 2025-03-04 221738](https://github.com/user-attachments/assets/16304869-efe0-41fd-a6e9-fc6ea74af1a2)

#### Specification:
1.Transistors M1 and M2 : These are the NMOS transistors forming the differential pair.
2.Resistors Rd: These are the load resistors, typically used to convert the output current into a voltage.
3.Current Source Iss : Ensures a constant total current through M1 and M2.
4.Input Voltages (VINcm): VIN,cm is the common-mode input voltage.
5.Output Voltages (Vout1, Vout2): These are the output voltages at the drains of M1 and M2.

- Common mode signals = (V1 + V2) / 2
- Differential mode = V1 - V2

#### Working Principle:
1.When Vin1 and Vin2 are equal then Current thorough both M1 and M2 are equal.(Vin1=Vin2=Vcm).
2.If both sides of the perfectly matched the it can reject noise in Common mode.
3.There should be no mismatch in Circuit elements like MOSFETs(M1,M2),Power supply(Vdd) and resistors(Rd,Rss).
Vout1=(-gm X Rd X Vcm)/(1+2 X gm X Rs)
Vout2=(-gm X Rd X Vcm)/(1+2 X gm X Rs)

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

### Circuit 1:
<img width="700" alt="ckt1" src="https://github.com/user-attachments/assets/de21a903-5b44-49e3-9554-82ace46add7a" />


The Circuit components and their values-
- **Power Supply,VDD** = 2.5V
- **Input Common mode voltage (Vincm1 and Vincm2)** = 1.3V
- **Load Resistors (RD1 and RD2)** = 1.83kΩ
- **Current Source Resistor,R1(RSS)** = 416.66Ω

#### Design:
##### Calculation:
Determine ISS & Id-

    ISS=P/VDD
       =(3x10^-3)/2.5
    ISS=1.2mA
    Id1=Id2=Iss/2
       =0.6mA
    
Determine RD (Drain Resistance)-

    RD=(VDD-Vocm)/Id
      =(2.5-1.4)/0.6*10^-3
    RD=1.83kohm

Determine RSS -

    RSS=Vp/ISS
       =0.5/1.2*10^-3
    RSS=0.77kohm

### DC Analysis:
<img width="700" alt="dc1" src="https://github.com/user-attachments/assets/3dc720b7-a8a2-4974-9c87-a6e611efa558" />

### Transient Analysis:
<img width="700" alt="transient1" src="https://github.com/user-attachments/assets/051d10a1-fca6-4bb8-96be-b75ee3e38cf6" />


**Gain Calculation:**

    Gain,Av = Vout/VIn
            = (1.62-1.17)/(1.34-1.25)
            = 5
    Gain in dB = 20log(Av)
               = 20log(5)
               = 13.979


### AC Analysis:
<img width="700" alt="ac1" src="https://github.com/user-attachments/assets/7b5ec543-b319-43a4-9cb1-7fbdf610ee71" />


**Bandwidth of -3dB gain:**


      Bandwidth = 18.612GHz


    
### Circuit 2:
<img width="700" alt="ckt2" src="https://github.com/user-attachments/assets/e4069787-c5e9-4c99-ae8a-77087c899dfe" />

### DC Analysis:
<img width="700" alt="dc2" src="https://github.com/user-attachments/assets/eaeef6a3-d4d6-4740-8018-421bd27174f7" />

### Transient Analysis:
<img width="700" alt="trans2" src="https://github.com/user-attachments/assets/69090c88-faef-4e98-85b2-db6cf46b7013" />

**Gain Calculation:**

    Gain,Av = Vout/VIn
            = (1.62-1.17)/(1.34-1.25)
            = 5
    Gain in dB = 20log(Av)
               = 20log(5)
               = 13.979

### AC Analysis:
<img width="700" alt="ac2" src="https://github.com/user-attachments/assets/aa6b1bc0-d608-45d7-83cb-02cdcf056d6b" />



**Bandwidth of -3dB gain:**


      Bandwidth = 18.610GHz

      

### Circuit 3:
<img width="700" alt="ckt3" src="https://github.com/user-attachments/assets/e5dad326-2c12-4569-a2e9-5402d30fe99e" />

### DC Analysis:
<img width="700" alt="dc3" src="https://github.com/user-attachments/assets/781674fb-3ac2-47ef-9c72-dd84f11d1b60" />

### Transient Analysis:
<img width="700" alt="trans3" src="https://github.com/user-attachments/assets/9eb1a77c-5179-4e04-8e41-4a67e59c228a" />

**Gain Calculation:**

    Gain,Av = Vout/VIn
            = (1.62-1.17)/(1.34-1.25)
            = 5.0777
    Gain in dB = 20log(Av)
               = 20log(5)
               = 14.113


### AC Analysis:
<img width="700" alt="ac3" src="https://github.com/user-attachments/assets/d6c34e23-1cb4-45c3-9058-bdde960aa327" />



**Bandwidth of -3dB gain:**


      Bandwidth = 18.610GHz


## Results:

### Comparision between the Circuit 1,2,3:

| **Parameter** | **Circuit 1** | **Circuit 2** | **Circuit 3** |
|--------------|--------------|--------------|--------------|
| **Vout1**  | 1.4V  | 1.402V  | 1.40001V  |
| **Vout2**  | 1.4V  | 1.402V  | 1.40001V  |
| **V(Vp)** | 0.500902 | 0.501321V | 0.500903V |
| **Id(M1)** | 0.000601092 A | 0.0006 A | 0.000601089 A |
| **Id(M2)** | 0.000601092 A | 0.0006 A | 0.000601089 A |
| **Total Current(ISS)** | 0.0012 A | 0.000909 A | 0.00120218 A |

### Length(L) and Width(W) of M1, M2, M3 transistors :

| **Parameter** | **M1** | **M2** | **M3** |
|--------------|--------------|--------------|--------------|
| **Length(L)**  | 180nm  | 180nm  | 180nm  |
| **Width(W)**  | 7.7165μm  | 7.7165μm  | 35.091μm  |

### Variation Of Vincm to Circuit 1, 2 & 3:
#### For Circuit 1:
| **Vincm1 & Vincm2** | **Vout1 & Vout2** | **Gain1 & Gain2** |
|--------------|--------------|--------------|
| 1.3V  | 1.4V  | 1.076  |   
| 1.5V  |  1.11V | 0.74  |   
| 2V  | 0.865V  | 0.4325  |   
| 2.5V  |  0.842V | 0.3368  |   

#### For Circuit 2:
| **Vincm1 & Vincm2** | **Vout1 & Vout2** | **Gain1 & Gain2** |
|--------------|--------------|--------------|
| 1.3V  | 1.402V  | 1.078  |   
| 1.5V  |  1.402V | 0.934  |   
| 2V | 1.402V  | 0.701  |   
| 2.5V  |  1.402V | 0.5608  |  

#### For Circuit 3:
| **Vincm1 & Vincm2** | **Vout1 & Vout2** | **Gain1 & Gain2** |
|--------------|--------------|--------------|
| 1.3V  | 1.40001V  | 1.0769  |   
| 1.5V  |  1.2394V | 0.8262  |   
| 2V  | 1.16223V  | 0.58111  |  
| 2.5V  |  1.16223V | 0.46488  | 

## Inference:

| **Parameter**                  | **Circuit 1 (With RSS)**       | **Circuit 2 (With ISS - Current Mirror)** | **Circuit 3 (MOSFET Differential Pair)** | **Inference**  |
|--------------------------------|--------------------------------|--------------------------------|--------------------------------|---------------|
| **Common Mode Rejection Ratio (CMRR)** | **Lower** | **Higher than RSS circuit** | **Highest** | Using **ISS (current source)** and **MOSFETs** improves CMRR significantly. |
| **Power Consumption**          | **Higher**                     | **Lower than RSS**             | **Lowest**                     | **MOSFET-based circuit** is more power-efficient. |
| **Current Source Used**        | **Resistive (RSS)**            | **Active (ISS - Current Mirror)** | **MOSFET Current Source**      | Active current sources provide better biasing and stability. |
| **Output Common-Mode Voltage** | **Less Stable**                | **More stable**                | **Most Stable**                | **MOSFET-based ISS** gives the best output voltage stability. |
| **Frequency Response**         | **Limited Bandwidth**          | **Improved Bandwidth**         | **Widest Bandwidth**           | **MOSFET differential pair** extends the bandwidth. |

- **Tail Current Stability:**

    **Circuit 1 & 2:** ISS current is determined by passive resistors, leading to potential fluctuations.

    **Circuit 3:** Incorporates M3 as a current source, ensuring stable and regulated tail current.

- **Common-Mode Voltage (Vp):** Minor variations observed across circuits; however, Circuit 3 exhibits the most stable Vp due to the active current source.

- **Output Voltage Matching:** All circuits show closely matched output voltages, indicating effective differential performance.

## Conclusion:
- **Circuit 3** performs the best in terms of gain, power efficiency, and common-mode rejection, making it the most optimized design.
- **Circuit 2** improves upon Circuit 1 with better gain, reduced mismatch, and improved bandwidth, but still falls short of Circuit 3.
- **Circuit 1** is functional but has the lowest gain and slightly higher power consumption compared to the other two.

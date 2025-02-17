EXPERIMENT - 1

Design 1
AIM:
To do the DC analysis,Transient and AC analysis of a CS amplifier circuit and extract the various parameters associated using LT Spice.

:COMPONENTS REQUIRED:

N Mosfet(nmos4 ,pmos4 ), Resistor(22k), voltage supply(1.8V,0.9V) and connecting wires.

THEORY:
Mostfet is one of the most important compontent in electronics .

This importance is due to the fact of its compact design , low power consumption ,simple geometry and compatibilty in VLSI technology.

There are three different configurations in which the mosfet can be connected (namely common drain,gate and source) the most popular being common source and common drain configurations.

The Mosfet acts as an amplifier in the saturation region of operation where Vgs > Vth,Vgd < Vth and Vds>=Vov for an N channel mosfet. In the common source configuration there is a 180 degree phase shift between input and output.
There is very high input impedance (Ig=0) ideally infinite.

The drain current
Id = 1/2*kn*(Vov)^2 ; Vov=Vgs-Vth and kn=un*Cox*(W/L)

Output is taken from the drain end rather than simply across the resistor to maintain the common ground referance.

DC Analysis:
This is done ensure the mosfet operates in saturation and to calculate the DC operationg point of the transistor. This prevents signal distortion .
This helps in the determination of the biasing resistors.
This helps in getting a correct operating point despite the fluctuation in the other parameters.

Transient Analysis:
This to done to analyse the response of the circuit to time varying signals.

This is helpful to determine the signl distorton, DC shift between the input and the output. This plays key role in detecting issues like phase distortion.This is essential for high speed applications like communication systems.

AC Analysis:

This is nothing but the small signal analysis of the circuit.This is done to determine the Gain of the amplifier circuit.
This also helps to analyze the Frequency Reponse of the amplifier circuit. the gain is given by Av = -gm Rd

PROCEDURE:
1.Create a new folder and name it as project file.Save the LT spice file in this folder.

2.Name the mosfet as CMOSN and the length as 180nm and width as 3um initially.

3.For the pmos name it as CMOSP and set the length as 180nm and width as 3um respectively

4.DC Analysis: Set up the circuit as per the circuit diagram with proper connections ensuring valid circuit for further analysis. Apply the DC voltage of Vdd=1.8V and Vgs = 0.9 V . Go to simulate option in the tab and click on DC analysis and press ok.(.op) Click on Run to get the DC operating point ,Vout and Id.

5.Transient Analysis: Apply a sine wave input of Vgs=0.9V with an amplitude of 50mV and frequency of 1kHz by going to advanced menu in the voltage setting option.go to simulate option and click on transient analysis and give the stop time as 10m and click ok.(.tran 10m) Now Run to visualise the response of the circuit to a time varying signal.

6.AC Analysis: Go to spice directive and give the library file path for the simulator to access the data through the path . Go to simulate option in the tab , edit simulation command , click on AC analysis and mention the time of sweep as decade , no of points as 20 and frequency as .1Hz to 1THzand click on ok.Now Run to analyze the gain and frequency response of the circuit.(.ac dec 20 .1 1T)


CKT 1
![Screenshot 2025-02-17 001225](https://github.com/user-attachments/assets/a607b1ec-5268-4ab1-b97b-3fd00c1ad73b)

Calculation :


Power = 100uW

Loop Equation: Vdd=Vds+Id*Rd

P=I*V (Id=55.55 uA , Vdd=1.8V)

clearly Vds=Vout; Vds>=Vgs-Vth


Widhth=0.3um(Vary width to get the current)

Vds=0.543

gain=-20dB(from AC analysis)

Q point is (0.543,55.55uA)

Tabular Column :

| Width |	Current(Id) |	Vout  |

|---|---|---|

| 1um	  |   74.2uA	   | 0.122  |

| 0.8um |  72.7uA	      | 0.155  |

| 0.7um |  71.65uA	   | 0.18   |

| 0.3um |	 55.55uA	   | 0.543  |

RESULTS:

1. DC Analysis:
   ![Screenshot 2025-02-17 002748](https://github.com/user-attachments/assets/7447c126-dc9b-434c-8d5c-31190cf0892f)

   
Id=55.55uA


Vout=0.543V


Width=0.3um


DC Operating point : (0.543,55uA) is obtained for 0.3um Width and 180nm Length.

2. Transient Analysis:
   ![Screenshot 2025-02-16 224308](https://github.com/user-attachments/assets/2a6e86df-18a4-4405-beab-79da3536ecfc)

There is 180 degree phase shift between input and output or the DC level shift.

3. AC Analysis:
   ![Screenshot 2025-02-17 093256](https://github.com/user-attachments/assets/f525de3e-8024-404c-addf-81cbb1ef23a8)


   
INFERENCE:


1. Current is directly Propotional to the Width of the Mosfet and the current varies with the change in width.

2. Mosfet saturation ensures the mosfet works as an amplifier and produces the desired negative gain as per the equation Av=-gm*Rd.

3. Q point stability is attained in saturation region thus helping in attaining linear amplification .

4. The Mosfet gain is increased in mid band frequency range (small signal analysis).

5. The Transient analysis reveleas the response of the circuit to time domain ssignal and determines how quickly the circuit responds to variation.
This is essential in high speed applications.

6. AC Analysis helps in designing circuits with desired gain and helps in impedance matching.
Also helps in understanding the frequency response and small signal behaviour of the circuit.


Circuit 2:


Theory :


A Diode connected mosfet transistor always is in saturation and acts as a constant current source and acts as a amplifier. The different type of analysis are DC Analysis, AC Analysis and Transient analysis. The drain current obtained is given by the formula
Id = 1/2*kn*(Vov)^2 ; Vov=Vgs-Vth and kn=unCox*(W/L)

DC Analysis:


This is done ensure the mosfet operates in saturation and to calculate the DC operationg point of the transistor. This prevents signal distortion .
This helps in the determination of the biasing resistors.
This helps in getting a correct operating point despite the fluctuation in the other parameters.

Transient Analysis:


This to done to analyse the response of the circuit to time varying signals.

This is helpful to determine the signl distorton, DC shift between the input and the output. This plays key role in detecting issues like phase distortion.This is essential for high speed applications like communication systems.

AC Analysis:


This is nothing but the small signal analysis of the circuit.This is done to determine the Gain of the amplifier circuit .
This also helps to analyze the Frequency Reponse of the amplifier circuit. the gain is given by Av = -gm Rd


PROCEDURE:


1.Create a new folder and name it as project file.Save the LT spice file in this folder.

2.Name the mosfet as CMOSN and the length as 180nm and width as 3um initially.

3.For the pmos name it as CMOSP and set the length as 180nm and width as 3um respectively

4.DC Analysis: Set up the circuit as per the circuit diagram with proper connections ensuring valid circuit for further analysis. Apply the DC voltage of Vdd=1.8V and Vgs = 0.9 V . Go to simulate option in the tab and edit simulation command, click on DC analysis and press ok.(.op) Click on Run in the tab menu to get the DC operating point ,Vout and Id.

5.Transient Analysis: Apply a sine wave input of Vgs=0.9V with an amplitude of 50mV and frequency of 1kHz by going to advanced menu in the voltage setting option.go to simulate option in tab ,edit simulation command , click on transient analysis and give the stop time as 3m and click ok.(.tran 3m) Now Run to visualise the response of the circuit to a time varying signal.

6.AC Analysis: Go to spice directive and give the library file path for the simulator to access the data through the path . Go to simulate option in the tab , edit simulation command , click on AC analysis and mention the time of sweep as decade , no of points as 20 and frequency as .1Hz to 1THzand click on ok.Now Run to analyze the gain and frequency response of the circuit.(.ac dec 20 .1 1T).

Calculation:

Power = 100mW

P = V*I ; ( V= 1.8 V)

That implies Id = 55.55uA

V out/sub> = 1.658 V

Length= 180nm

Width=2um

Vds = Vout

Tabular Column:


| Width |	Current(Id) |	Vout  |


| 1.0um |	22.72uA     |	1.65  |


| 1.2um |	32.66uA     |	1.658 |


| 1.5um |	40.83uA     |	1.658 |


| 2.0um |	55.55uA     |	1.658 |


Simulation Result:

1. DC Analysis:

   *image
2. Transient Analysis:
   *image
3. AC Analysis:
  *image


INFERENCE:

1.The Current Id is dependent on width and hence it changes when the width changes whereas the remaining parameters remain constany.

2.DC Analysis ensures proper biasing and hence the mosfet operates in saturation and Q point stability is attained.

3.The Transient analysis reveleas the response of the circuit to time domain ssignal and determines how quickly the circuit responds to variation.
This is essential in high speed applications.

4.AC Analysis helps in designing circuits with desired gain and helps in impedance matching.
Also helps in understanding the frequency response and small signal behaviour of the circuit.

5.Together all the analysis helps in designing and opyimising an amplifier.

# EXPERIMENT-02---4NI24EC154---CS-AMPLIFIER\

### Objective

This work presents a comparative study of Source Degenerated, Cascode, and Diode-Connected Common Source amplifiers implemented using TSMC 180 nm technology in LTSpice. The goal is to evaluate the amplifier configurations and confirm the accuracy of theoretical calculations by comparing them with simulation outcomes.

#### Given Specifications :
VDD = 1.2 V
Power constraint: 𝑃≤0.4mW
Load capacitance: 𝐶𝐿=0.5pF
Channel length: L=360nm

### Project Goals

#### The main goals of this work are to:
1.Develop the amplifier design based on analytical (theoretical) calculations.
2.Identify the appropriate transistor dimensions and sizing.
3.Perform circuit simulation in LTSpice to evaluate performance.
4.Compare the calculated gain with the simulated gain values.
5.Examine and explain the differences between theoretical predictions and practical simulation results.

## CIRCUIT DESCRIPTION 

<img width="1282" height="936" alt="EXP 2A CKT" src="https://github.com/user-attachments/assets/9bf55269-5b47-4309-8807-7d7514467271" />

The circuit includes the following components:

1.An NMOS transistor that serves as the main amplifying element
2.A PMOS transistor functioning as an active load
3.A source degeneration resistor (Rs) connected at the source terminal
4.A bias voltage (VB) used to properly bias the circuit
5.The output taken from the drain terminal

##### Configuration:
The circuit is arranged as a Common Source amplifier with a PMOS active load, where the input signal is applied to the gate of the NMOS transistor.

### 3. Theory

A Common Source (CS) MOS amplifier is one of the most widely used basic configurations in analog circuit design. It is commonly employed because it provides significant voltage amplification and simple implementation.

#### Key Features
1.Provides large voltage gain
2.Produces 180° phase inversion between input and output
3.The overall gain mainly depends on the transconductance of the transistor and the output resistance of the device

### MOSFET Saturation Current Equation
When a MOSFET operates in the saturation region, the drain current is expressed as:
ID=(1/2)kn′(W/L)(VOV)2
Where: 𝑘𝑛′=𝜇𝑛𝐶𝑜𝑥
𝑉𝑂𝑉=𝑉𝐺𝑆−𝑉𝑇𝐻

#### Transconductance
The transconductance of the MOS transistor is given by: 
𝑔𝑚=2𝐼𝐷 / 𝑉𝑂𝑉

### Output Resistance
The output resistance of the transistor can be written as:
𝑟𝑜=1/𝜆𝐼𝐷
​
### Voltage Gain
For a source degeneration amplifier, the voltage gain is represented as:
𝐴𝑣=−𝑔𝑚(𝑟𝑜1∥𝑟𝑜2)1+𝑔𝑚𝑅𝑠

### 4. Design Calculations
Step 1: Maximum Drain Current Based on Power Constraint
The maximum drain current is determined from the power limitation:
𝑃 ≤ 𝑉𝐷𝐷.𝐼𝐷
𝐼𝐷=𝑃/𝑉𝐷𝐷​
𝐼𝐷=0.4𝑚𝑊/1.2𝑉
𝐼𝐷=0.33𝑚𝐴
ID=330μA

### Step 2: Output Voltage Selection
To achieve a symmetrical output voltage swing, the output voltage is selected as:
𝑉𝑜𝑢𝑡=𝑉𝐷𝐷/2+𝑉𝑅𝑆​
Vout=0.6+0.2
Vout=0.8V

### Step 3: Overdrive Voltage
Assuming:
𝑉𝑂𝑉=0.25
𝑉𝑇𝐻=0.366

The gate-to-source voltage becomes:
𝑉𝐺𝑆=𝑉𝑂𝑉+𝑉𝑇𝐻
𝑉𝐺𝑆=0.25+0.366
𝑉𝐺𝑆=0.61𝑉

### Step 4: Gate Voltage
The required gate voltage is calculated as:
𝑉𝐺=𝑉𝐺𝑆+𝐼𝐷.𝑅𝑆

Assuming:
𝑉𝑅𝑆=0.2𝑉
𝑉𝐺=0.61+0.2
𝑉𝐺=0.81𝑉

### Step 5: Source Resistor
The source degeneration resistor value is obtained from:
𝑅𝑆=𝑉𝑅𝑆/𝐼𝐷
𝑅𝑆=606Ω

### 5. NMOS Width Calculation
Using the MOSFET drain current equation:
𝐼𝐷=(1/2)𝑘𝑛′(𝑊/𝐿)(𝑉𝑂𝑉)2
Where:
𝑘𝑛′=𝜇𝑛𝐶𝑜𝑥
𝜇𝑛=273.81𝑐𝑚2/𝑉𝑠
𝐶𝑜𝑥=𝜀𝑜𝑥/𝑡𝑜𝑥
𝜀𝑜𝑥=8.854×10−12×3.9
𝑡𝑜𝑥=4.1×10−9
𝑘𝑛′=2.306×10−4
	
Solving the equation for transistor width:
𝑊≈16.48𝜇𝑚
Therefore, 𝑊1=16.48𝜇𝑚

### 6. PMOS Width Calculation
For the PMOS device, the drain current relation becomes:
𝐼𝐷=(1/2)𝜇𝑝𝐶𝑜𝑥(𝑊/𝐿)(𝑉𝑂𝑉)2

Assume: 
𝑉𝑇𝑃=0.39𝑉
𝑉𝑂𝑉=0.25𝑉

Reason for Selecting 
𝑉𝑂𝑉=0.25𝑉

The overdrive voltage 𝑉𝑂𝑉=𝑉𝐺𝑆−𝑉𝑇𝐻 is chosen as 0.25 V to ensure proper MOSFET biasing in the saturation region, particularly when operating with a low supply voltage of 𝑉𝐷𝐷=1.2𝑉.

### Several design considerations influence this choice:

1.Saturation Region Operation
A moderate overdrive voltage keeps the transistor operating in the saturation region, which is essential for achieving stable and predictable amplification.

2.Low Power Requirement
Using a relatively small 𝑉𝑂𝑉 helps reduce the drain current, allowing the circuit to remain within the specified power constraint.

3.Better Transconductance Efficiency
For analog amplifier design, 𝑉𝑂𝑉 values typically lie between 0.2 V and 0.3 V, as this range provides good transconductance efficiency (gm/ID).

4.Voltage Headroom
Because the supply voltage is limited to 1.2 V, selecting a smaller overdrive voltage preserves sufficient voltage headroom for the remaining nodes of the circuit.

Hence, 𝑉𝑂𝑉=0.25𝑉 is a practical and commonly used assumption in low-voltage CMOS amplifier design.

## PMOS Bias Voltage

𝑉𝑆𝐺=𝑉𝑂𝑉+∣𝑉𝑇𝑃∣
𝑉𝑆𝐺=0.25+0.39

Since 
𝑉𝑆𝐺=𝑉𝑆−𝑉𝐺 and 𝑉𝑆=𝑉𝐷𝐷 then 𝑉𝑆𝐺=𝑉𝐷𝐷−𝑉𝐺
	​
Therefore the bias voltage is:
𝑉𝐵=1.2−0.64
𝑉𝐵=0.56𝑉

## PMOS Width Result
Solving the current equation for PMOS transistor sizing gives:
𝑊2=39.05𝜇𝑚


#DC OPERATING POINT

<img width="960" height="651" alt="EXP 2A OPERATING POINT" src="https://github.com/user-attachments/assets/075e371c-bbff-4109-94ee-a4f37ff1f08e" />

### Design Summary and Simulation Comparison
Condition	             W₁ (µm)	 W₂ (µm) 	 Drain Current(ID)        Output Voltage 
                                                       (µA)                 Vout(V)
Initial Design 
Estimate	              16.48	      39.05	             145	                0.14
Modified Dimensions      	75	        95	          323.33	                 0.83

###Current Evaluation

The circuit was originally designed targeting a drain current of:
                                                                   𝐼𝐷𝑑𝑒𝑠𝑖𝑔𝑛 = 300𝜇𝐴

However, simulation results from LTSpice indicate:
                                                     𝐼𝐷𝑠𝑖𝑚𝑢𝑙𝑎𝑡𝑒𝑑 = 323.33 𝜇𝐴

###Deviation in Current
The variation between expected and obtained current is:
                                                        Δ𝐼𝐷 = 323.33 − 300 = 23.33 𝜇𝐴

###Percentage Variation


Percentage Deviation=(23.33/300)×100 ≈ 7.77%

###Interpretation of Results

The observed increase in drain current compared to the theoretical value is expected due to practical device behavior. While manual calculations rely on ideal MOSFET assumptions, simulation tools incorporate more realistic conditions.

##Factors Contributing to Variation
1.Channel Length Modulation (λ effect) :
Causes a slight rise in current as drain voltage increases.

2.Advanced Device Modeling:
LTSpice includes second-order effects like mobility reduction and short-channel behavior.

3. Parameter Estimation Errors
Values such as threshold voltage (VTH) and overdrive voltage (VOV) are approximated during hand calculations.

4.Increase in Transistor Width (W)
Enlarging W₁ and W₂ directly enhances current conduction capability.

###Final Observation

The simulated drain current is moderately higher than the calculated value, with a deviation of about 7.77%, which is acceptable in practical CMOS design. This confirms that the circuit operates close to the intended design with improved performance after resizing.

#TRANSIENT ANALYSIS :

FROM THE INPUT TRANSIENT WAVEFORM :

<img width="1901" height="444" alt="EXP 2A INPUT HIGH" src="https://github.com/user-attachments/assets/b30cb3a0-3e66-43fe-b281-c7438781db6f" />


<img width="1905" height="462" alt="EXP 2A INPUT LOW" src="https://github.com/user-attachments/assets/18c49b32-90f4-4f11-be6e-2a16af0becf1" />

FROM THE OUTPUT TRANSIENT WAVEFORM :

<img width="1913" height="503" alt="EXP 2A OUTPUT HIGH" src="https://github.com/user-attachments/assets/4d0ccf49-02c9-48d9-93ea-524b229588c8" />

<img width="1918" height="469" alt="EXP 2A OUTPUT LOW" src="https://github.com/user-attachments/assets/fd689a94-d5b8-4acf-91a0-bdfe30e8a370" />






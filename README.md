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

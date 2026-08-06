## Purpose, Objectives, Constraints

The purpose of this project is to create an automated test fixture capable of verifying the continuity of 92 electrical connections on a manufactured component. The component under test contains two connector interfaces: a board-mounted header (J1) and an HDMI connector (J2).

The fixture evaluates predefined combinations of pins between J1 and J2 to determine whether each connection passes continuity requirements. A connection is classified as:

Open Circuit: Resistance > 80 kΩ
Short Circuit: Resistance < 2 Ω

The primary objectives and design constraints are summarized below.

| Metric   | Objective        | Constraint                             |
|-----------|-----------------|----------------------------------------|
| Speed     | 3 seconds total | Faster than current device (2 minutes) |
| Accuracy  | 1% accuracy     | ±10% accuracy                          |

## Architecture

The core concept of the system is essentially to inject a known current into the DUT, then measure the voltage difference between the DUT terminals to find the resistance. The design can be split into the FORCE and SENSE paths - the force path carries the current, while the sense path reads the voltage difference. The sense path's traces are high impedance, meaning it does not carry meaningful current or impact the force path.
The core measurement principle is based on sourcing a known current through the Device Under Test (DUT) and measuring the resulting voltage drop across the DUT terminals. Resistance is then calculated using Ohm's Law

The system is divided into two independent signal paths:
- Force Path: Applies a precise current through the DUT.
- Sense Path: Measures the voltage across the DUT terminals.

<p align = "center"><img width="884" height="642" alt="image" src="https://github.com/user-attachments/assets/2b196152-3e04-43bc-bb4a-a2fbb2d054b5" /></p>  

<p align = "center"><em>Figure 1: Functional block diagram of my test fixture circuit.</em></p>

## Force pathway
A precision voltage reference from the ADC (2.5 V) is buffered by an operational amplifier and combined with precision resistors to generate a known excitation current.
Two programmable current ranges are implemented using load switches and selectable resistor values. This allows the system to accommodate both high- and low-resistance measurements while preventing op-amp saturation.
The output current is routed through a relay matrix controlled by a Darlington transistor array. The matrix connects the excitation source to any desired pair of DUT terminals, enabling programmable selection of test points under firmware control.

<img width="1130" height="692" alt="image" src="https://github.com/user-attachments/assets/d4e6c8ff-6d3a-4d04-b326-83bbf9ff86a7" />
<p align = "center"><em>Figure 2: Schematic Visualization of the force pathway. The yellow ports represent the two ends of the DUT terminal pin headers.</em></p>

## Sense pathway
Once a known current has been applied through the DUT, the voltage across the DUT terminals is measured to determine resistance.The sensing subsystem uses a 32-bit precision ADC configured for differential voltage measurements. The ADC inputs are connected to two 16-channel analog multiplexers, allowing direct access to the DUT terminals. By programming the multiplexer channel selection, the microcontroller can measure the voltage across any desired pair of DUT pins. This architecture separates current sourcing from voltage measurement, reducing error caused by switch resistance and PCB trace resistance.

## Programmable control
All major subsystems are controlled by a microcontroller running custom firmware.

The MCU is responsible for:
- Configuring the ADC and acquiring measurement data
- Controlling the relay matrix that routes excitation current
- Selecting channels on the sense multiplexers
- Executing automated continuity test sequences
- Recieving ready inputs and reporting test results to the user

The ADC, relay drivers, and analog multiplexers are all interfaced directly to the MCU and operated through custom-developed firmware.
## Supporting Hardware
An LCD screen is used for user I/O, an ST-Link Debugger header is used for debugging/programming, and 3 LEDs are for easy power-rail checking.

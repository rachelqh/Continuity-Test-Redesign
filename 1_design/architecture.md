## Purpose, Objectives, Constraints

The purpose of this project is to create a test fixture which will check the continuity of 92 connections on a manufatured component. The component has two arrays of pins; one on J1 -  a board mount header, and another array on J1, a HDMI connector. The purpose of the fixture is to probe several connections (combinations of pins on j1 and j2) to check if there is an OPEN CIRCUIT (>80kohm trace) or a SHORT CIRCUIT (<2ohm trace).

Listed in the table below are the objectives and constraints for this project.

| Metric   | Objective        | Constraint                             |
|-----------|-----------------|----------------------------------------|
| Speed     | 3 seconds total | Faster than current device (2 minutes) |
| Accuracy  | 1% accuracy     | ±10% accuracy                          |

## Architecture

The core concept of the system is essentially to inject a known current into the DUT, then measure the voltage difference between the DUT terminals to find the resistance. The design can be split into the FORCE and SENSE paths - the force path carries the current, while the sense path reads the voltage difference. The sense path's traces are high impedance, meaning it does not carry meaningful current or impact the force path.

<p align = "center"><img width="884" height="642" alt="image" src="https://github.com/user-attachments/assets/2b196152-3e04-43bc-bb4a-a2fbb2d054b5" /></p>  

<p align = "center"><em>Figure 1: Functional block diagram of my test fixture circuit.</em></p>

## Force pathway
The buffer op-amp uses the precise 2.5V reference pin from the ADC, along with resistors, to create a known current. Two different values of resistors, which are toggleable in code via load switches, are used for both ends of measurement to prevent the op-amp from oversaturation. Two pin headers, each connected to one terminal of 13 DUTs, are linked to the output of the op amp via relay matrix, which is programmable via darlington transistor array. Therefore, a specific pair of DUTs can be chosen to have current sent through them.

<img width="1130" height="692" alt="image" src="https://github.com/user-attachments/assets/d4e6c8ff-6d3a-4d04-b326-83bbf9ff86a7" />
<p align = "center"><em>Figure 1: Schematic Visualization of the force pathway. The yellow ports represent the two ends of the DUT terminal pin headers.</em></p>

## Sense pathway
Since the force pathway has provided a known current, measuring the two terminals at the DUT pins can provide resistance. A 32-bit precision ADC is used for highly accurate resistance values, with it's differential input connected to 2x 16 channel multiplexers which are connected directly at the DUT terminals. Therefore, the sense multiplexers programmable by the MCU are can be to control which pair of DUTs the ADC is reading at any given time. 

## Programmable control
All major components are directly linked to the MCU for firmware programming. The ADC, relay drivers and sense mux are all programmed and use (custom firmware)[REPLACE LATER]. 

## Misc
An LCD screen is used for user I/O, an ST-Link Debugger header is used for debugging/programming, and 3 LEDs are for easy power-rail checking.

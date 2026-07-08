## Purpose, Objectives, Constraints

The purpose of this project is to create a test fixture which will check the continuity of 92 connections on a manufatured component. The component has two arrays of pins; one on J1 -  a board mount header, and another array on J1, a HDMI connector. The purpose of the fixture is to probe several connections (combinations of pins on j1 and j2) to check if there is an OPEN CIRCUIT (>80kohm trace) or a SHORT CIRCUIT (<2ohm trace).

Listed in the table below are the objectives and constraints for this project.

| Metric   | Objective        | Constraint                             |
|-----------|-----------------|----------------------------------------|
| Speed     | 3 seconds total | Faster than current device (2 minutes) |
| Accuracy  | 1% accuracy     | ±10% accuracy                          |

## Architecture

The core concept of the system is essentially to inject a known current into the DUT, then measure the voltage difference between the DUT terminals to find the resistance. The design can be split into the FORCE and SENSE paths - the force path carries the current, while the sense path reads the voltage difference. A block diagram shown below, and the architecture will be explained more in detail.

<img width="884" height="642" alt="image" src="https://github.com/user-attachments/assets/2b196152-3e04-43bc-bb4a-a2fbb2d054b5" />
Figure 1: Functional block diagram of my test fixture circuit.

## Force pathway

The buffer op-amp uses the precise 2.5V reference pin from the ADC, along with resistors, to create a known current. Two different values of resistors, which are toggleable in code, are used for both ends of measurement; the short circuit (2

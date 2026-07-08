# Design Decisions
This document outlines major design decisions and why they were chosen

## 4 Wire Kelvin sense
4 Wire Kelvin sensing was chosen despite its complexity to increase accuracy and rigour. Since the board needs to measure 2ohm DUTs to 10% accuracy (0.2ohms) trace resistances, on resistances of components and other unknown resistances could easily overblow the error budget. This approach was 4 wire kelvin sensing implemented to measure the voltages as close as possible to the DUT pins.

## Choosing to use Relays over switching ICs
Relays were selected to carry the force current because of their low leakage current and low on resistance.  On resistances and leakage current may impact the current running through the DUTs, which would cause the known current used to calculate Ohm's law to be inaccurate. As opposed to load switches, muxes or other integrated circuits, whose other traces and pads may cause noise or leakage, the mechanical switching creates a highly isolated connection more akin to a trace.

Assuming a 5 ms relay switching time, the complete 91-connection test sequence requires approximately 455 ms, which was considered acceptable for the application.

## Using Muxes for the Sense Path, not Relays
A low leakage, low on resistance mux was chosen for the sense path because the ADC's differential inputs are high impedance, meaning a negligible amount of current runs through those traces. Therefore, the leakage current or on resistance of ICs would not significantly impact accuracy. While the design originally included relays for both the force and sense paths, switching to a hybrid approach reduced complexity, size and improved the layout of the board significantly.

## Precision current source
An op-amp + precision resistor system was used to create a known current source which, with the differential voltage from the two DUT pins, could be used to find resistance. This was chosen to reduce costs and operator complexity, as requiring one bench power source per test fixture would limit future scalability.


## Firmware Architecture
While the original architecture opted to slowly print out the rests of each test individually, this test fixture runs all tests in a very short amount of time (<2secs) and then only prints out the tests that failed at the end. The original test fixture as well printed all the tests out slowly without user input, making it easy for an operator to miss failed tests. This design decision was improved by displaying the failed tests at the end, where the user can scroll through them.


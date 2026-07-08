# Design Decisions
This document outlines major design decisions and why they were chosen

## 4 Wire Kelvin sense
4 Wire Kelvin sensing was chosen despite it's complexity to increase accuracy and rigour. Since the board needs to measure 2ohm DUTs to 10% accuracy (0.2ohms) trace resistances, on-resistances of components and other unknown resistances could easily overblow the error budget. 4 wire kelvin sensing is implemented to measure the voltages directly at the DUT pins.

## Relay Selection
Relays were selected to carry the force current because of their low leakage current and low on resistance. As opposed to load switches, muxes or other integrated circuits, whose other traces and pads may cause noise or leakage, the mechanical switching creates a connection much more akin to a trace. On resistances and leakage current may impact the current running through the DUTs, which would cause the known current used to calculate Ohm's law to be innacurate. 

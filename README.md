# Continuity-Test-Redesign
The employees of the PFC Flexible Circuits has to perform thousands of continuity tests per month to ensure quality. To improve efficency, commonly produced components have unique test fixtures to probe the continuity of up to hundreds of traces quickly. 

PFC has requested the Summer 2026 Interns to improve the existing test fixtures, which are slow, inefficient, and unreliable.


My approach to improving this design has been to redesign it from scratch - the circuit is a 4-wire Kelvin sense continuity test board, which injects current into a force path. The two ends of the DUTs are measured by a precision 32 bit ADC to read voltage; this, along with a known current, can calculate resistance, and therefore continuity.

Hardware Requirements Specification


<img width="884" height="642" alt="image" src="https://github.com/user-attachments/assets/2b196152-3e04-43bc-bb4a-a2fbb2d054b5" />
Figure 1: Functional block diagram of my test fixture circuit.

# Continuity-Test-Redesign
The employees of the PFC Flexible Circuits has to perform thousands of continuity tests per month to ensure quality. To improve efficency, commonly produced components have unique test fixtures to probe the continuity of up to hundreds of traces quickly. 

PFC has requested the Summer 2026 Interns to improve the existing test fixtures, which are slow, inefficient, and unreliable.

The system injects a precision current through a force path and measures the voltage across the device under test (DUT) using a high-resolution 32-bit ADC. By applying Ohm's Law to the measured voltage and known current, the system accurately calculates trace resistance and determines continuity. This approach increases accuracy while significantly reducing the operation time.

<img width="884" height="642" alt="image" src="https://github.com/user-attachments/assets/2b196152-3e04-43bc-bb4a-a2fbb2d054b5" />
Figure 1: Functional block diagram of my test fixture circuit.




A detailed documentation of all aspects of this project are provided in this repository.

- An interactive schematic viewer with screenshots of the schematics is in `/schematic`
- An interactive layout viewer with screenshots of the layout is in `/layout`
- Design documents are in `/docs`, and includes:
   - `architecture.md` explains project scope, requirements, circuit architecture and how it works
   - `design decisions.md` explains componenent & architecture selection
   - `error estimations.md` provides error estimations
- User documents are in `/userdocuments` and includes:
   - `usermanual.md` which provides an operator-end user manual
   - `futureupdates.md` which provides details on how to change the board for the future. This is especailly useful for future interns/employees of PFC who would like to update the other test fixtures to use this design.
  
If there are any additional questions, feel free to email me at rachelq.huang@mail.utoronto.ca (or if it's been a long time and I've graduated, rachelhuang082@gmail.com).

# Continuity-Test-Redesign
The employees of the PFC Flexible Circuits has to perform thousands of continuity tests per month to ensure quality. To improve efficency, commonly produced components have unique test fixtures to probe the continuity of up to hundreds of traces quickly. 

PFC has requested the Summer 2026 Interns to improve the existing test fixtures, which are slow, inefficient, and unreliable.

The system injects a precision current through a force path and measures the voltage across the device under test (DUT) using a high-resolution 32-bit ADC. By applying Ohm's Law to the measured voltage and known current, the system accurately calculates trace resistance and determines continuity. This approach increases accuracy while significantly reducing the operation time.

## Results
PLACEHOLDER: PLEASE PUT THE HERO IMAGE/FINSIHED PROJECT HERE

Write some stats on the success of the project
  - Decrease of time used from 2min to ~1sec, saving the company up to ____$ per year
  - Accuracy up to ___ohms, ___%
    
A detailed documentation of all aspects of this project are provided in this repository.

## Documentation Legend
To navigate more details on how this project was designed, please refer to the following documents:
*Please ignore /docs. It is used to generate the interactive schematic & layout viewers and is not part of the showcase.

- An interactive schematic viewer with screenshots of the schematics is in [/schematic](./schematic/)
- An interactive layout viewer with screenshots of the layout is in [/layout](./layout)
- Design documents are in [/design](./design), and includes:
   - `architecture.md` explains project scope, requirements, circuit architecture and how it works
   - `design decisions.md` explains componenent & architecture selection
- User documents are in [/userdocuments](./userdocuments) and includes:
   - `usermanual.md` which provides an operator-end user manual
   - `futureupdates.md` which provides details on how to change the board for the future. This is especailly useful for future interns/employees of PFC who would like to update the other test fixtures to use this design.
- Firmware is uploaded in [/firmware](./firmware) and includes all parts of the code, which includes:
   - STM32CUBEmx generated code
   - ST7789 LCD screen driver, which is downloaded from [Floyd-Fish on Github](https://github.com/Floyd-Fish/ST7789-STM32)
   - Custom ADC driver
   - Main continuity test circuit
   - 
If there are any additional questions, feel free to email me at rachelq.huang@mail.utoronto.ca (or if it's been a long time and I've graduated, rachelhuang082@gmail.com).

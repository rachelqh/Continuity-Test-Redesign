# Continuity-Test-Redesign
OSI Electronics performs thousands of continuity tests each month to ensure product quality. Existing test fixtures were slow, inefficient, and unreliable, creating an opportunity to improve testing throughput and measurement accuracy.

As part of the Summer 2026 internship program, I redesigned the existing continuity testing system to improve its performance and reliability.

The redesigned system uses 4-wire kelvin sensing by injecting a precision current through a force path and measuring the resulting voltage across the device under test (DUT) using a high-resolution 32-bit ADC. Using Ohm's law, the system calculates accurate trace resistance and determines continuity, enabling faster and more accurate testing across multiple traces. 

The redesigned fixture was successfully received and is now under development for permanent deployment within the company.
A detailed documentation of all aspects of this project are provided in this repository.

## Results
<img width="2160" height="2880" alt="image" src="https://github.com/user-attachments/assets/3ce62d22-e58d-4532-9cd1-da4f7c1bc640" />

- Decrease of time used from 2min to ~5sec, a 95% reduction, saving the company up to 7000$ per year.
- Accurate low-ohm measurements around the < 2ohm range.

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

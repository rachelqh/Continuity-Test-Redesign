# Future Updates

## Implementing other test fixtures with more DUT pins
Future interns at PFC Flexible Circuits may be tasked with replacing the rest of the test fixtures. The existing design can be reused with more relays and more sense muxes to support more DUT connections, while keeping the general architecture similar. With more DUT terminals, it's possible that a GPIO expander or control mux might be necessary to control a higher scale of connections. 

## Designing Class 2 Test Fixtures
Class 2 test fixtures which lower accuracy requirements may be better designed without the sense mux, with an ADC reading directly at the two force power rails. While this reduces accuracy, it significantly reduces complexity, keeping projects more manageable. The more complicated test fixtures that require tighter accuracy bounds are better suited for this architecture.

## Input buttons, on/off switches, reset buttons
Future designs could be improved with more input buttons, a reset button that connects directly to the STM32, and an on/off power switch.

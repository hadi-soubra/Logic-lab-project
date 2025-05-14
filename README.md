# Logic-lab-project



#Purpose:
This project demonstrates a fully discrete, microcontroller-free lamp mapping system that dynamically captures and preserves the activation order of four independent switches. Using only fundamental digital components (D‑flip‑flops, multiplexers, decoders, comparators, and a 555 monostable timer), the design encodes the sequence of switch activations into a 2‑bit state, latches the assignment for each lamp, and ensures reliable timed resets. A bonus feature shows how a scrolling 7‑segment display can report status.


#Setup and Usage:

Prerequisites:
Intel Quartus II (version 18.0 or later)
Standard TTL components and a 555 timer IC on a breadboard

Opening the Project:
Launch Quartus II and open the .qpf.
Inspect the block diagram and open simulation  to verify timing.

Hardware Assembly:
Wire four SPST switches to the falling‑edge detectors (D‑flip‑flop inputs) as shown in schematics
Connect outputs of the order counter and sequence lookup network to the lamp decoders and D‑flip‑flops.
implement the 555 monostable timer to generate the 4 s reset pulse.

Running and Testing:
Apply +5 V power, toggle switches in any order, and observe that each activated lamp lights in the recorded sequence.
After 4 s, the monostable reset returns the system to the idle state.

Viewing the Scrolling Display (optional):
Open seven-segment.pdf and seven-segment.vwf in Quartus to simulate the bonus 7‑segment feature.

#Design Insights:

1.Discrete vs. Microcontroller: Choosing TTL logic over a microcontroller emphasizes fundamental digital design principles and avoids firmware complexity.

2.Edge Detection: Each switch off‑pulse is reliably captured using a simple RC differentiator feeding a D‑flip‑flop, ensuring only clean, single‑shot events.

3.Sequence Encoding: A 2‑bit up‑counter records the activation order; combined with a dual multiplexer, it generates the lamp ID without additional decoding logic.

4.Timed Reset: Early ripple‑counter–comparator resets proved imprecise. Replacing them with a 555 monostable yields a stable, exact 4 s pulse regardless of logic delays.

5.Modular Layout: Separating architecture into clear stages (edge detect → order counter → lookup → latch → decode) simplifies debugging and allows easy future expansion.

Bonus Feature: The scrolling 7‑segment display demonstrates how the same sequence bits can feed additional user‑feedback modules without altering core map logic.

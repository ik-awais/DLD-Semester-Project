# DLD Semester Project — 2-Way Autonomous Traffic Signal with 7-Segment Display

## Overview
A fully autonomous 2-way traffic light system with an embedded 7-segment display, built as a Digital Logic Design (DLD) semester project. Once powered, the system operates independently with no manual intervention required.

## Features
- 2-way autonomous traffic signal control
- Embedded 7-segment display (countdown/state indicator)
- No manual handling after battery input
- Simulated and verified in Multisim

## Approach / Methodology
The system is built entirely from digital ICs rather than a microcontroller, keeping the logic transparent and easy to trace.

- **Clock generation:** A 555 Timer IC is used to continuously generate clock pulses. The pulse rate is set using resistors and capacitors around the timer.
- **Sequencing:** These pulses drive a CD4017 decade counter, which steps through its 10 outputs one at a time — turning off the current output and turning on the next with every incoming pulse.
- **Uneven signal timing:** Since Red and Green need to stay on longer than Yellow, diodes are used to group several CD4017 outputs together per color. This gives Red and Green a longer combined ON-time while Yellow stays on only briefly, just like a real signal.
- **2-way coordination:** The two roads are positioned so they're always in opposite states — when one road's Red is active, the other road's Green is active, and both roads pass through Yellow together during the transition. This ensures only one direction has right-of-way at any moment, using a single counter and diode network to control both roads.
- **Countdown display:** A 74LS192 up/down decade counter feeds a CD4511 BCD-to-seven-segment decoder/driver, which drives a 7-segment display through current-limiting resistors on each segment. The display counts down roughly 3 seconds per light, completing one full 10-second Red-Yellow-Green cycle before restarting — giving a clear numeric cue of the time left before the signal changes.

Together, the timer, counter, diode network, and decoder work in a closed loop with no external control needed once power is applied.

## Repository Contents

| File | Description |
|---|---|
| `DLD Project Proposal.docx` | Updated project proposal (2-way traffic system with 7-segment display) |
| `2wayTrafficSignal.ms14` | Multisim simulation file (2-way system) |
| `Project Demo.mp4` | Demo video of the completed hardware project |
| `TrafficSignalMultisimImplementation.mp4` | Screen recording of the Multisim implementation |
| `README.md` | Project's Description |


## Team
- **[@ik-awais](https://github.com/ik-awais)** — Multisim circuit design, hardware implementation
- **[@waleeja07-wk](https://github.com/waleeja07-wk)** — Project proposal, debugging support, hardware implementation

## Project Evolution
The original proposal covered a 1-way traffic signal. The instructor extended the scope to a 2-way system with an integrated 7-segment display. Both the simulation and physical hardware were completed successfully.

## Tools Used
- NI Multisim
- Logic gates, 7-segment display, LEDs (hardware)
- Battery-powered hardware prototype

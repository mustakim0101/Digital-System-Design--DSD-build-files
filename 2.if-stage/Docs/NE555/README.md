# NE555 Clock Notes for IF Stage

## Overview
This note documents the NE555 timer setup used to generate clock pulses for IF-stage hardware timing.

The goal was stable repeatable clocking for D flip-flop based PC updates, especially where manual pulse generation caused unstable triggering.

## Purpose
NE555 in this project is used to:
- generate repeating hardware clock pulses
- improve practical stability over manual toggling
- support step-by-step PC updates in IF-stage hardware

This is separate from Arduino EEPROM programming.

## Astable Connection Used
Reported practical connection in this project:
- pin 8 -> VCC
- pin 4 -> VCC
- pin 1 -> GND
- pin 7 -> R1 (10k ohm) -> VCC
- pin 7 -> R2 (100k ohm) -> pins 2 and 6
- pins 2 and 6 shorted
- pins 2/6 -> 10uF capacitor -> GND
- pin 5 -> 0.01uF capacitor -> GND
- pin 3 -> clock output

## Components
- NE555 timer IC
- 10k ohm resistor
- 100k ohm resistor
- 10uF capacitor
- 0.01uF capacitor
- breadboard and jumper wires
- power supply

## Pin Table
| NE555 Pin | Connection |
|---|---|
| Pin 1 | GND |
| Pin 2 | short to pin 6 |
| Pin 3 | clock output |
| Pin 4 | VCC |
| Pin 5 | 0.01uF capacitor to GND |
| Pin 6 | short to pin 2 |
| Pin 7 | resistor network (R1, R2) |
| Pin 8 | VCC |

## External Component Table
| Part | Connection |
|---|---|
| R1 = 10k ohm | between VCC and pin 7 |
| R2 = 100k ohm | between pin 7 and pins 2/6 |
| C = 10uF | between pins 2/6 and GND |
| 0.01uF capacitor | between pin 5 and GND |

## Text Wiring Diagram
```text
VCC ---- R1 (10k ohm) ---- Pin 7
Pin 7 ---- R2 (100k ohm) ---- Pins 2 and 6
Pins 2 and 6 ---- 10uF capacitor ---- GND
Pin 5 ---- 0.01uF capacitor ---- GND
Pin 4 ---- VCC
Pin 8 ---- VCC
Pin 1 ---- GND
Pin 3 ---- Clock Output
```

## Practical Notes
- hardware timing can differ from Proteus timing
- keep jumper wires short to reduce noise
- check 10uF capacitor polarity
- keep pin 4 tied HIGH to avoid reset
- use pin 3 as the clock output source

## Common Issues
1. hardware and simulation pulse behavior mismatch
2. manual pulse edges causing unstable trigger behavior
3. timing-sensitive flip-flop operation
4. resistor/capacitor value mismatch before final correction

## Key Files in This Folder
- `ne555_marked.png`
- `BUILD_NE555.txt`

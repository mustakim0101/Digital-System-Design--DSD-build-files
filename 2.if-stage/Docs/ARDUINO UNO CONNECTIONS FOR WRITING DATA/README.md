# Arduino EEPROM Writer Notes (28256 / 27256 / AT28C16)

## Overview
This note explains how Arduino Uno was used to write/read EEPROM data for instruction/program loading and verification.

The workflow was moved from manual write pulsing to Arduino automation because manual `WE` pulsing was slow and error-prone.

## Important Clarification
In this setup, Arduino Uno is used only for EEPROM programming/verification.

Arduino does **not**:
- generate the NE555 hardware clock
- control datapath D flip-flop timing
- act as the processor itself

## EEPROM Context
Design discussion used 28256/27256 style workflow.

Practical constraints noted in project files:
- 28256/27256 were not always easy to collect in local hardware market
- AT28C16 was available and used in hardware
- in Proteus, 27256 was used when 28256 model availability was limited

## Simplified Addressing Used for Early Tests
- Arduino-controlled address lines: `A0` to `A3`
- higher address lines: tied LOW
- effective tested range: `0x0` to `0xF`

## Example Arduino-to-EEPROM Pin Mapping
| Function | EEPROM Pin | Arduino Pin |
|---|---:|---|
| Address A0 | 9 | D2 |
| Address A1 | 8 | D3 |
| Address A2 | 7 | D4 |
| Address A3 | 6 | D5 |
| Address A4-A14 | higher address pins | GND |
| Data D0 | 11 | D6 |
| Data D1 | 12 | D7 |
| Data D2 | 13 | D8 |
| Data D3 | 15 | D9 |
| Data D4 | 16 | D10 |
| Data D5 | 17 | D11 |
| Data D6 | 18 | D12 |
| Data D7 | 19 | D13 |
| CE | 20 | A0 |
| OE | 22 | A1 |
| WE | 27 | A2 |
| VCC | 28 | 5V |
| GND | 14 | GND |

For AT28C16, exact pin count/address width differs, but the same write/read principle is followed.

## Text Wiring Diagram
```text
Arduino Uno          EEPROM (28256 / 27256 / AT28C16)
-----------          -------------------------------
D2   ------------->  A0
D3   ------------->  A1
D4   ------------->  A2
D5   ------------->  A3

GND  ------------->  higher unused address lines

D6   ------------->  D0
D7   ------------->  D1
D8   ------------->  D2
D9   ------------->  D3
D10  ------------->  D4
D11  ------------->  D5
D12  ------------->  D6
D13  ------------->  D7

A0   ------------->  CE
A1   ------------->  OE
A2   ------------->  WE

5V   ------------->  VCC
GND  ------------->  GND
```

## Write Flow
1. Set address on `A0-A3`.
2. Set data on `D0-D7`.
3. `CE = LOW`, `OE = HIGH`.
4. Pulse `WE` LOW then HIGH.
5. Wait write-cycle delay (about 10 ms in this note flow).

## Read Flow
1. Set address on `A0-A3`.
2. Configure data pins as input.
3. `CE = LOW`, `OE = LOW`, `WE = HIGH`.
4. Read data and verify in serial output.

## Proteus Note (Important)
In simulation, wiring alone is not enough.

You must also load the correct HEX/program file into the EEPROM/ROM model in Proteus. Without loading the program file, expected instruction/data output will not appear.

## Common Issues Observed
1. Manual write pulsing is tedious.
2. EEPROM write timing must be respected.
3. Address/data pin mapping errors are common.
4. Proteus model availability differs from hardware reality.
5. Keep Arduino programming role separate from datapath clocking role.

## Key Files in This Folder
- `eeprom_readwrite_28256_27256_at28c16.ino`
- `eeprom_readwrite_28256_27256_at28c16.c`
- `eeprom_readwrite_28256_27256_at28c16.txt`
- `Arduino uno-pinout.png`
- `Arduino readwrite setup-front.jpg`
- `Arduino readwrite setup-back.jpg`
- `Arduino readwrite setup-IC placement demo.jpg`

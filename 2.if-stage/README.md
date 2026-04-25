# Instruction Fetch (IF) Stage

## Overview
This folder contains the Instruction Fetch (IF) stage design for a simple processor using TTL ICs, EEPROM, and a hardware clock source.

Core IF-stage responsibilities:
- hold current instruction address in Program Counter (PC)
- increment PC for next fetch
- read instruction from memory
- forward fetched instruction to the next stage

## Quick Start
1. Read this README for architecture and constraints.
2. Open `Summary_of_Implemented_IF_Stage.txt`.
3. Open `proteus/IFstgMUSAfina6116butreally2816.pdsprj`.
4. Check supporting docs in `Docs/`:
   - Arduino EEPROM programming flow
   - NE555 clock connection

## Main Functional Blocks
1. Program Counter register
2. PC increment unit
3. Instruction memory
4. Clock generation circuit

## Components Used
- `74LS174` (PC register)
- `74LS83` / `7483` (PC increment adder)
- `AT28C16` EEPROM (instruction memory)
- `NE555` timer (clock generation)
- `74LS04` (clock inversion where needed)
- Arduino UNO (EEPROM programming only)

## How It Works
### 1) Program Counter
- PC state is held in flip-flops (`74LS174`).
- On each clock update, PC moves to next address.

### 2) PC Increment
- `74LS83` adder increments PC (effectively `PC + 1` in this build scale).

### 3) Instruction Memory
- EEPROM stores instruction bytes.
- Program bytes are written beforehand.
- EEPROM output provides instruction at current PC address.

### 4) Clock
- NE555 provides repeating clock pulses.
- `74LS04` can provide inverted timing when needed for stability.

## Addressing Method
Current simplified addressing:
- active lines: `A0` to `A3`
- higher address lines: tied LOW
- effective small instruction space (for example, first 16 locations)

## Inputs and Outputs
### Inputs
- clock pulse
- reset/initialization state
- pre-programmed EEPROM contents

### Outputs
- current PC address
- fetched instruction byte

## Fetch Sequence
1. PC holds current address.
2. Address goes to EEPROM.
3. EEPROM outputs instruction byte.
4. Adder computes next address.
5. On next clock, PC updates.
6. Sequence repeats.

## EEPROM Programming Notes
Arduino UNO is used only for EEPROM write/read verification.

Important clarification:
- Arduino is **not** the processor clock source for datapath timing.
- Arduino is **not** controlling IF-stage flip-flop execution logic.
- NE555 + hardware datapath remain separate from Arduino programming flow.

Also in Proteus:
- the EEPROM/ROM model must have the correct program file loaded
- in this repo, the memory program file is `27C256.hex`
- without loading the HEX/program file in Proteus, expected outputs will not appear

## Common Implementation Issues
- timing/edge behavior differences between hardware and simulation
- carry/constant wiring mistakes in PC increment
- unstable or too-fast clock pulses
- EEPROM control pin wiring (`CE`, `OE`, `WE`) errors
- address/data mapping mistakes during programming

## Key Files
- `Summary_of_Implemented_IF_Stage.txt`
- `27C256.hex`
- `images/if stage final design using 6116.png`
- `images/ifsatgetable.png`
- `proteus/IFstgMUSAfina6116butreally2816.pdsprj`
- `proteus/If_stage_Write_Code_2816.txt`
- `Docs/ARDUINO UNO CONNECTIONS FOR WRITING DATA/README.md`
- `Docs/NE555/README.md`

## External Tutorial Reference
SRAM6116 tutorial link (as kept from project notes):
- https://youtu.be/ayEx26BPP4M?si=8L577QQGfqZQNsOo

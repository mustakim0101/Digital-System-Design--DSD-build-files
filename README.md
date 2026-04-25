# Digital-System-Design--DSD-build-files

## Overview
This repository contains stage-by-stage build files for a student CPU datapath project using TTL ICs, Proteus simulation, and hardware-oriented notes.

Recommended reading order:
1. [1. 1-bit-ALU](./1.%201-bit-ALU/README.md)
2. [2.if-stage](./2.if-stage/README.md)
3. [4.ex--mem-wb-stage](./4.ex--mem-wb-stage/README.md)

The **ID stage is not included yet** and will be added later by another contributor.

## Repository Structure
```text
Digital-System-Design--DSD-build-files/
|-- README.md
|-- demo_cpu_stages_combined.jpg
|-- 1. 1-bit-ALU/
|   |-- README.md
|   `-- Prototype/
|       `-- README.md
|-- 2.if-stage/
|   |-- README.md
|   `-- Docs/
|       |-- ARDUINO UNO CONNECTIONS FOR WRITING DATA/
|       |   `-- README.md
|       `-- NE555/
|           `-- README.md
`-- 4.ex--mem-wb-stage/
    `-- README.md
```

## Which Files to Follow
Use this path for the cleanest onboarding:

1. Start with [1. 1-bit-ALU/README.md](./1.%201-bit-ALU/README.md) for ALU base design.
2. Then read [1. 1-bit-ALU/Prototype/README.md](./1.%201-bit-ALU/Prototype/README.md) for the earlier prototype context.
3. Continue with [2.if-stage/README.md](./2.if-stage/README.md) for instruction fetch design and EEPROM flow.
4. Use the IF supporting docs:
   - [Arduino EEPROM writing README](./2.if-stage/Docs/ARDUINO%20UNO%20CONNECTIONS%20FOR%20WRITING%20DATA/README.md)
   - [NE555 clock README](./2.if-stage/Docs/NE555/README.md)
5. Finish with [4.ex--mem-wb-stage/README.md](./4.ex--mem-wb-stage/README.md) and follow its sequential build order.

## Implementation Videos, Lab Reports, and Extra Files
Use this exact link for external implementation materials:

https://drive.google.com/drive/folders/1-2rGLCHgIih2sUCrsEitGa2uKAypPHLt?usp=sharing

Local extra file in this repo:
- `demo_cpu_stages_combined.jpg`

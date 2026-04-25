# 1-Bit ALU Prototype

## Overview
This folder contains the prototype version of the 1-bit ALU built using logic gates, digital ICs, and multiplexer-based output selection.

This prototype was used as a base idea for later CPU stages (IF, ID, EX, MEM, WB planning context).

## Objectives
- understand ALU behavior at gate level
- build a working 1-bit ALU
- support multiple arithmetic and logic functions in one unit
- use selector bits to choose output operation
- prepare for future multi-bit expansion

## Inputs and Outputs
### Inputs
- `A`: first 1-bit operand
- `B`: second 1-bit operand
- `Cin`: carry-in / borrow-in input
- `S3 S2 S1 S0`: 4-bit selector lines

### Outputs
- `F`: selected function output
- `Cout`: carry-out / borrow-out (operation-dependent)

## Operation Table
| Selector | Operation |
|---|---|
| `0000` | ADD |
| `0001` | SUBTRACT |
| `0010` | MULTIPLY |
| `0011` | LEFT SHIFT |
| `0100` | RIGHT SHIFT |
| `0101` | ROTATE LEFT |
| `0110` | ROTATE RIGHT |
| `0111` | AND |
| `1000` | OR |
| `1001` | XOR |
| `1010` | XNOR |
| `1011` | NAND |
| `1100` | NOR |
| `1101` | GREATER THAN |
| `1110` | EQUAL |
| `1111` | LESS THAN |

## Main Design Method
The prototype was built by generating operation outputs in separate blocks and selecting one output through a multiplexer.

### Build blocks
1. adder block
2. subtractor block
3. logic operation blocks
4. comparator block
5. shift/rotate/multiply outputs
6. output multiplexer

## Arithmetic Equations Used
### Addition
`S = A xor B xor Cin`

`Cout = AB + ACin + BCin`

### Subtraction
`D = A xor B xor Bin`

`Bout = BBin + A'B + A'Bin`

In this design, `Cin` is used as borrow input during subtraction mode.

## Important Prototype Observations
Some operations are limited in 1-bit form:
- multiply behaves the same as AND for 1-bit inputs
- shift-left and shift-right become trivial for a single bit
- rotate-left and rotate-right return the same bit in 1-bit form
- 1-bit compare is simple, but multi-bit magnitude compare needs additional logic strategy

## Hardware Practical Note
The original design idea expected 16 operation selection with a 16:1 MUX concept.

During practical collection, 8:1 MUX availability affected hardware planning, so selection implementation required practical adjustment.

## Notes for Future 8-Bit Expansion
### Operations that replicate more naturally
- ADD
- SUBTRACT
- AND
- OR
- XOR
- XNOR
- NAND
- NOR

### Operations that need extra design work
- shift operations (need cross-bit wiring)
- rotate operations (need wrap-around connections)
- multiply (needs dedicated multiplier approach)
- GT / EQ / LT for wider values (needs proper multi-bit comparison logic)

## Suggested Reading Path
1. Read this prototype summary.
2. Open the prototype Proteus and image files.
3. Compare with the optimized ALU version in `../README.md`.

## Key Files in This Folder
- `proteus/1-bit-alu-final-design-musa.pdsprj`
- `images/1-bit-alu-final-design-musa.png`
- `images/1-bit-alu-final-design-musa-musamarked-ic-number.png`
- `images/shifting circuit.jpg.png`

## Learning Direction
This prototype helped clarify ALU block composition and scaling issues before larger datapath integration.

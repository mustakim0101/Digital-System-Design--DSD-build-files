# EX / MEM / WB Stage

## Overview
This folder contains the build progression for the Execution (EX), Memory Access (MEM), and Write Back (WB) path of the project datapath using Proteus and TTL-based design logic.

The structure preserves the actual step-by-step build history from smaller subcircuits to the final WB-connected version.

## Quick Start
1. Follow the sequence in `docs/sequential built files/` in order.
2. For each step, read `.txt` notes first.
3. Then open the matching `.pdsprj` file in Proteus.
4. Use image/PDF snapshots for visual verification.

## Repository Layout
```text
4.ex--mem-wb-stage/
|-- README.md
|-- control_rom_32.hex
|-- docs/
|   |-- Ex-MEM-WB Stage H_W.pdf
|   |-- 4 bit regFile/
|   |-- 8 bit regFile/
|   `-- sequential built files/
|       |-- 1.alu control unit/
|       |-- 2.reg file with 2 read port/
|       |-- 3.connect regfile with decoder/
|       |-- 4.input B (signextender or rt)+regwrite/
|       |-- 5.COMBINED WITH ALU/
|       |-- 6.final/
|       |-- 7.Write back path connection/
|       `-- others/
|-- images/
`-- proteus/
```

## Build Sequence (Actual Folder Order)
### 1) `1.alu control unit`
- `docs/sequential built files/1.alu control unit/alu control unit.txt`
- `docs/sequential built files/1.alu control unit/AlU_controlUNIT.pdsprj`

### 2) `2.reg file with 2 read port`
- `docs/sequential built files/2.reg file with 2 read port/8bit regfile with two read port.txt`
- `docs/sequential built files/2.reg file with 2 read port/8bit regfile with 2readports.pdsprj`
- `docs/sequential built files/2.reg file with 2 read port/control_rom_32.hex`

### 3) `3.connect regfile with decoder`
- `docs/sequential built files/3.connect regfile with decoder/connecting regfile to decoder.txt`
- `docs/sequential built files/3.connect regfile with decoder/starting_regfile_addresslogic _forallOPcodes.pdsprj`

### 4) `4.input B (signextender or rt)+regwrite`
- `docs/sequential built files/4.input B (signextender or rt)+regwrite/sign extendor.txt`
- `docs/sequential built files/4.input B (signextender or rt)+regwrite/left out regfile connection with idstage.txt`
- `docs/sequential built files/4.input B (signextender or rt)+regwrite/tables and euations.txt`
- `docs/sequential built files/4.input B (signextender or rt)+regwrite/without ALU part.pdsprj`
- `docs/sequential built files/4.input B (signextender or rt)+regwrite/if+id+controlsig+aluselec+regfile+signext.pdsprj`

### 5) `5.COMBINED WITH ALU`
- `docs/sequential built files/5.COMBINED WITH ALU/tables and euations.txt`
- `docs/sequential built files/5.COMBINED WITH ALU/various operating table .txt`
- `docs/sequential built files/5.COMBINED WITH ALU/control_rom_32.hex`
- `docs/sequential built files/5.COMBINED WITH ALU/code_for_regFile_readport_check.hex`
- `docs/sequential built files/5.COMBINED WITH ALU/ID_COMBINED_WITH_ALU+REGFILE.pdsprj`

### 6) `6.final`
- `docs/sequential built files/6.final/new LI tables and euations.txt`
- `docs/sequential built files/6.final/making_immediatiateCHOOSEbtn.pdsprj`
- `docs/sequential built files/6.final/224c2f2b-27c7-4f2f-b287-574a98956b3d.jpg`

### 7) `7.Write back path connection`
- `docs/sequential built files/7.Write back path connection/WBinregfilecompleted.pdsprj`

### Supplemental: `others`
- `docs/sequential built files/others/1bit_alu_replication.pdsprj`
- `docs/sequential built files/others/updated_idstage_according_to_EX.pdsprj`

## Which Files to Follow
If you only want the core path, follow these in order:
1. Step folders `1` to `7` in `docs/sequential built files/`
2. Inside each step: `.txt` first, `.pdsprj` second
3. Then compare with final artifacts:
   - `images/8bit_EXstage_design.jpeg`
   - `images/8bit_EXstage_design.PDF`
   - `proteus/WBinregfilecompleted.pdsprj`

## Stage Responsibilities (Project Context)
- **EX stage:** ALU/control-based arithmetic-logic processing, input selection, and address-related calculations.
- **MEM stage:** memory-related path behavior tied to combined design/control flow.
- **WB stage:** route selected final value back into register file write path.

## Additional References
- `docs/Ex-MEM-WB Stage H_W.pdf`
- `docs/4 bit regFile/` (historical build context)
- `docs/8 bit regFile/` (historical build context)
- `control_rom_32.hex`

## Note About ID Stage
Some files in `others/` reference ID-stage alignment work. The full standalone ID-stage integration is treated separately in the overall repository progression.

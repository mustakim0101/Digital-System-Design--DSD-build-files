

\---



\# EX / MEM / WB Stage Design Using TTL ICs and Proteus



\## Overview



This repository contains the design progression of the \*\*Execution (EX), Memory Access (MEM), and Write Back (WB)\*\* stages of a simple processor datapath built in \*\*Proteus\*\* using TTL ICs and manually designed subcircuits.



This stage was developed step by step by combining:



\- ALU control logic

\- manual register file

\- two read ports

\- opcode-based register address selection

\- sign extension and ALU input-B selection

\- ALU integration

\- immediate / LI support

\- write-back path connection



The folder is organized to preserve the \*\*actual build order\*\*, so the project can be understood gradually from smaller working blocks up to the final combined design.

\---



\## What This Repository Contains



This repository mainly focuses on:



\- building the datapath after IF and ID stages

\- connecting the register file to the EX stage

\- selecting ALU inputs properly

\- supporting R-type, `lw`, `sw`, `beq`, and `li` style instruction flow

\- generating ALU outputs and memory-related paths

\- building the write-back path into the register file



It includes both:



\- \*\*supporting documents and notes\*\*

\- \*\*Proteus design files\*\*

\- \*\*screenshots / design images\*\*

\- \*\*final combined stage files\*\* 



\---



\## Main Folder Structure



```text

4.ex--mem-wb-stage

├── docs

│   ├── 4 bit regFile

│   ├── 8 bit regFile

│   └── sequential built files

│       ├── 1.alu control unit

│       ├── 2.reg file with 2 read port

│       ├── 3.connect regfile with decoder

│       ├── 4.input B (signextender or rt)+regwrite

│       ├── 5.COMBINED WITH ALU

│       ├── 6.final

│       └── 7.Write back path connection

├── images

├── proteus

├── BUILD.md

└── necessary.txt

````



This structure is taken directly from the current repository tree you shared. 



\---



\## Design Flow



The EX / MEM / WB stage was not built in one step. It was developed in a sequence.



\### 1. ALU Control Unit



The first step was building the ALU control logic, which generates the ALU selector outputs from opcode-derived control signals and funct bits. This part is stored in:



\* `docs/sequential built files/1.alu control unit/` 



\### 2. 8-Bit Register File With Two Read Ports



The datapath then needed a manual register file with two read outputs. This was built and stored in:



\* `docs/sequential built files/2.reg file with 2 read port/` 



\### 3. Register File Address Logic



After that, the register file was connected with decoder/address logic so that different opcodes could select the proper read and write addresses.



\* `docs/sequential built files/3.connect regfile with decoder/` 



\### 4. Input-B Selection and Sign Extension



The next step was selecting the second ALU input between register data and sign-extended immediate/offset data.



\* `docs/sequential built files/4.input B (signextender or rt)+regwrite/` 



\### 5. Combined EX Stage With ALU



Then the ALU was integrated with the previous datapath blocks to build the working EX stage.



\* `docs/sequential built files/5.COMBINED WITH ALU/` 



\### 6. Final Refinement



A later folder contains the final adjusted version, including immediate/LI related update files.



\* `docs/sequential built files/6.final/` 



\### 7. Write Back Path



Finally, the WB connection was completed so the computed result could be sent back into the register file.



\* `docs/sequential built files/7.Write back path connection/` 



\---



\## Important Files



Some important files in this repo are:



\### Notes / Text Files



\* `alu control unit.txt`

\* `8bit regfile with two read port.txt`

\* `connecting regfile to decoder.txt`

\* `left out regfile connection with idstage.txt`

\* `sign extendor.txt`

\* `tables and euations.txt`

\* `new LI tables and euations.txt`

\* `various operating table .txt`

\* `necessary.txt` 



\### Proteus Files



\* `AlU\_controlUNIT.pdsprj`

\* `8bit regfile with 2readports.pdsprj`

\* `starting\_regfile\_addresslogic \_forallOPcodes.pdsprj`

\* `if+id+controlsig+aluselec+regfile+signext.pdsprj`

\* `ID\_COMBINED\_WITH\_ALU+REGFILE.pdsprj`

\* `making\_immediatiateCHOOSEbtn.pdsprj`

\* `WBinregfilecompleted.pdsprj` 



\### Final / Supporting Artifacts



\* `8bit\_EXstage\_design.PDF`

\* `control\_rom\_32.hex`

\* screenshots and JPEG images inside the sequential folders

\* separate `images/` and `proteus/` top-level folders 



\---



\## What the EX Stage Does



The EX stage is responsible for actual data processing in the datapath.



It performs:



\* arithmetic operations

\* logical operations

\* address calculation for memory instructions

\* comparison support for branch-type instructions

\* selection of ALU input sources



This stage uses information already decoded in the ID stage and applies the operation to register/immediate data before passing the result forward. The repository structure shows that ALU control, sign extension, register read selection, and ALU integration were all built as separate steps before being combined. 



\---



\## What the MEM Stage Does



The MEM stage uses the computed address and control signals to handle memory-related instructions such as:



\* memory read

\* memory write



In this project flow, memory-related behavior is tied closely with the EX stage datapath and write-back routing, rather than being isolated as a completely separate early folder. The later combined designs and WB connection files reflect this integration path. 



\---



\## What the WB Stage Does



The WB stage sends the correct final value back into the register file.



This usually means selecting between:



\* ALU result

\* memory output



The final WB connection work in this repo is represented by:



\* `docs/sequential built files/7.Write back path connection/WBinregfilecompleted.pdsprj` 



\---



\## How to Study This Repository



The best way to understand this project is to follow the files in build order, not randomly.



Recommended order:



1\. `1.alu control unit`

2\. `2.reg file with 2 read port`

3\. `3.connect regfile with decoder`

4\. `4.input B (signextender or rt)+regwrite`

5\. `5.COMBINED WITH ALU`

6\. `6.final`

7\. `7.Write back path connection`



That order matches the actual design progression preserved in the repository tree. 



\---



\## Repository Notes



This repository also contains supporting register-file history folders:



\* `docs/4 bit regFile/`

\* `docs/8 bit regFile/`



These are useful for understanding how the manual register file design evolved, but the main EX/MEM/WB flow is inside the sequential build folders. 



\---



\## Suggested Usage



If you are opening this repo for the first time:



\* read the note files first

\* then open the matching Proteus design files

\* then compare them with the final screenshots / PDF

\* finally open the WB-completed project file



This makes the design easier to follow than jumping directly to the final combined circuit. 



\---



\## Repository Structure 





4.ex--mem-wb-stage/

│

├── README.md

├── BUILD.md

├── necessary.txt

├── docs/

│   ├── 4 bit regFile/

│   ├── 8 bit regFile/

│   └── sequential built files/

├── images/

└── proteus/

\---



\---



\## Which Files to Follow



This repository contains many intermediate notes, screenshots, and Proteus files. To understand the design properly, follow the files in the same order the hardware/datapath was built.



\### Recommended order



1\. \*\*ALU Control Unit\*\*

&#x20;  - `docs/sequential built files/1.alu control unit/alu control unit.txt`

&#x20;  - `docs/sequential built files/1.alu control unit/AlU\_controlUNIT.pdsprj`



2\. \*\*8-Bit Register File With Two Read Ports\*\*

&#x20;  - `docs/sequential built files/2.reg file with 2 read port/8bit regfile with two read port.txt`

&#x20;  - `docs/sequential built files/2.reg file with 2 read port/8bit regfile with 2readports.pdsprj`



3\. \*\*Register File Address Logic\*\*

&#x20;  - `docs/sequential built files/3.connect regfile with decoder/connecting regfile to decoder.txt`

&#x20;  - `docs/sequential built files/3.connect regfile with decoder/starting\_regfile\_addresslogic \_forallOPcodes.pdsprj`



4\. \*\*Input-B Selection, Sign Extension, and Remaining ID-to-EX Logic\*\*

&#x20;  - `docs/sequential built files/4.input B (signextender or rt)+regwrite/sign extendor.txt`

&#x20;  - `docs/sequential built files/4.input B (signextender or rt)+regwrite/left out regfile connection with idstage.txt`

&#x20;  - `docs/sequential built files/4.input B (signextender or rt)+regwrite/if+id+controlsig+aluselec+regfile+signext.pdsprj`



5\. \*\*Combined EX Stage With ALU\*\*

&#x20;  - `docs/sequential built files/5.COMBINED WITH ALU/tables and euations.txt`

&#x20;  - `docs/sequential built files/5.COMBINED WITH ALU/various operating table .txt`

&#x20;  - `docs/sequential built files/5.COMBINED WITH ALU/ID\_COMBINED\_WITH\_ALU+REGFILE.pdsprj`

&#x20;  - `docs/sequential built files/5.COMBINED WITH ALU/8bit\_EXstage\_design.PDF`



6\. \*\*Final Refinement / Immediate Support\*\*

&#x20;  - `docs/sequential built files/6.final/new LI tables and euations.txt`

&#x20;  - `docs/sequential built files/6.final/making\_immediatiateCHOOSEbtn.pdsprj`



7\. \*\*Write Back Path Completion\*\*

&#x20;  - `docs/sequential built files/7.Write back path connection/WBinregfilecompleted.pdsprj`



\### Supporting files



These are useful as background/reference:



\- `docs/4 bit regFile/`

\- `docs/8 bit regFile/`

\- `control\_rom\_32.hex`

\- screenshots and images in the sequential folders

\- `necessary.txt`



\### Best approach



Read the `.txt` explanation file first, then open the matching `.pdsprj` file in Proteus.  

That gives the clearest understanding of how the datapath was built step by step.

````



\---






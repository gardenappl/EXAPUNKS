# 9: SFCTA Highway Sign #4902 (Remote Access Interface)

<div align="center"><img src="EXAPUNKS - SFCTA Highway Sign #4902 (151, 15, 1, 2024-06-23-16-37-16).mp4" /></div>

## Instructions
> Write EMBER-2's message (file 300) to the highway sign. The file contains one character value for each position on the sign from left to right, top to bottom.
> 
> For more information see "Hardware Hacks: Electronic Highway Signs" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
MARK ROW_LOOP
  COPY 9 T
  MARK COL_LOOP
    COPY X #DATA
    SUBI 9 T #DATA
    SUBI T 1 T
    COPY F #DATA
    TJMP COL_LOOP
  ADDI X 1 X
  TEST X < 3
  TJMP ROW_LOOP
WIPE
HALT

    
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 151    | 15   | 1        |

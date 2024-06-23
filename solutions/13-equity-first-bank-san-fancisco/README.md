# 13: Equity First Bank (San Fancisco)

<div align="center"><img src="EXAPUNKS - Equity First Bank (1461, 36, 10, 2024-06-23-16-39-28).mp4" /></div>

## Instructions
> Dispense all available cash from all connected ATMs.
> 
> For more information see "Network Exploration: Equity First Bank" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 800
LINK 800
COPY 7 T
MARK COPIES
  SUBI T 1 T
  ADDI 800 T X
  FJMP DO_THING
  REPL DO_THING
  JUMP COPIES

MARK DO_THING
  LINK X
  COPY #CASH X
  MARK DISP_BIG
    TEST X < 10
    TJMP DISP_SMALL
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    COPY 20 #DISP
    SUBI X 10 X
    JUMP DISP_BIG
  MARK DISP_SMALL
    TEST X < 1
    TJMP END
    COPY 20 #DISP
    SUBI X 1 X
    JUMP DISP_SMALL
MARK END
  HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1461   | 36   | 10       |

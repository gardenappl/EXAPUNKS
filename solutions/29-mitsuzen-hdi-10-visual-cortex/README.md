# 29: Mitsuzen HDI-10 (Visual Cortex)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (1498, 56, 10, 2024-06-23-17-31-48).gif" /></div>

## Instructions
> Read a value from each of the optic nerves present and write the correct value to the nerve that runs deeper into your visual cortex (V-CTX). To determine the value that should be written, count the number of values read that are greater than -55, multiply that count by 5, and then subtract 75. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL SPAWN_COL
LINK 1
COPY 3 X
REPL SPAWN_COL
REPL GO_VCTX
LINK 1
COPY 6 X
MARK SPAWN_COL
  REPL FROM_OPTIC
  LINK -3
  ADDI X 1 X
  REPL FROM_OPTIC
  LINK -3
  ADDI X 1 X
MARK FROM_OPTIC
  TEST #NERV > -55
  COPY T X
  COPY 7 T
  MARK OPTIC_WAIT1
    NOOP
    SUBI T 1 T
    TJMP OPTIC_WAIT1
  COPY X M
  COPY 7 T
  MARK OPTIC_WAIT2
    NOOP
    SUBI T 1 T
    TJMP OPTIC_WAIT2
  VOID M
  JUMP FROM_OPTIC

MARK GO_VCTX
  LINK 3
MARK TO_VCTX
  COPY 0 X
  @REP 9
  ADDI M X X
  @END
  MULI X 5 X
  SUBI X 75 #NERV
  @REP 9
  COPY @{0,1} M
  @END
  JUMP TO_VCTX


```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1498   | 56   | 10       |

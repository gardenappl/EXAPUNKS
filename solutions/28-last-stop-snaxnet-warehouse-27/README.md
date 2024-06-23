# 28: Last Stop Snaxnet (Warehouse 27)

<div align="center"><img src="EXAPUNKS - Last Stop SNAXNET (177, 92, 7, 2024-06-23-17-30-43).mp4" /></div>

## Instructions
> An array of five Zippe-type gas centrifuges, ZGC0 through ZGC4, are connected in a cascade configuration.
> 
> Read each of the #ZGCX registers and determine which centrifuge currently has the highest pressure. Then disable that centrifuge's regulator by writing a value of 0 to its #POWR register. Repeat this process until all five regulators have been disabled.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL ZGC0_GO
LINK 799
MAKE
COPY 5 F
MARK GET_MAX
  COPY 0 F
  COPY #ZGC0 X
  @REP 4
  TEST X < #ZGC@{1,1}
  FJMP NOT_MAX_@{1,1}
    COPY #ZGC@{1,1} X
    SEEK -1
    COPY @{1,1} F
  MARK NOT_MAX_@{1,1}
  @END
  SEEK -1
  COPY F X
  SEEK -2
  SUBI F 1 T
  @REP 5
  COPY X M
  @END
  FJMP DIE_GET_MAX
  SEEK -1
  COPY T F
  JUMP GET_MAX
  MARK DIE_GET_MAX
    WIPE
    HALT


MARK ZGC0_GO
  LINK 798
@REP 4
  REPL ZGC@{1,1}_GO
  JUMP CENTRI_WAIT
MARK ZGC@{1,1}_GO
  COPY @{1,1} X
  LINK 800
@END
MARK CENTRI_WAIT
  MAKE
  COPY 0 F
  SEEK -1
  MARK WAIT_SIGNAL
    TEST M = X
    FJMP AFTER_SIGNAL
    COPY 0 #POWR
  MARK AFTER_SIGNAL
    ADDI F 1 T
    SEEK -1
    COPY T F
    SEEK -1
    TEST T = 5
    TJMP DIE_CENTRI
    @REP 4
    NOOP
    @END
    FJMP WAIT_SIGNAL
  MARK DIE_CENTRI
    WIPE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 177    | 92   | 7        |

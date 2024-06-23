# 24: King's Ransom Online (US West Realm)

<div align="center"><img src="EXAPUNKS - King's Ransom Online (41, 36, 25, 2024-06-23-17-25-18).gif" /></div>

## Instructions
> ﻿Reset the ownership of all castles and sub-buildings to ‗P00000‗ (file 300), the player ID for unowned buildings.
> 
> To ensure that there are no witnesses you must first disconnect all connected players. Terminate every EXA in every host before changing any castle or sub-building files anywhere in the network. If you leave an EXA alive in one host while changing a file in another you will fail the task.
> 
> For more information see "Network Exploration: King's Ransom Online" in the second issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
GRAB 300
COPY F X
DROP
LINK 800
REPL REPL2
REPL REPL3

MARK REPL1
  COPY 800 T
  REPL GO
  COPY 801 T
  JUMP GO

MARK REPL2
  COPY 802 T
  REPL GO
  COPY 803 T
  JUMP GO

MARK REPL3
  COPY 804 T
  REPL GO
  COPY 805 T
MARK GO
  LINK T
  @REP 3
  KILL
  @END
  COPY 200 T

MARK MODIFY
  GRAB T
  SEEK 2
  COPY X F
  MARK MODIFY_SUB
    COPY F T
    REPL MODIFY
    TEST EOF
    FJMP MODIFY_SUB
  HALT
  
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 41     | 36   | 25       |

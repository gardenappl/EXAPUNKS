# 22: Alliance Power and Light (Streetsmarts GIS Database)

<div align="center"><img src="EXAPUNKS - Alliance Power and Light (37, 31, 40, 2024-06-23-17-23-21).mp4" /></div>

## Instructions
> Locate the two hosts with the specified hostnames (file 300), which correspond to the target power grid substations. When you've found them, cut the power by writing a value of 0 to #POWR.
> 
> For more information see "Network Exploration: Geographic Information Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
REPL START_FIND
COPY F X
DROP

MARK START_FIND
  LINK 800
  REPL START_FIND_R
  LINK 800
  REPL FIND
  LINK 800
  JUMP FIND
MARK START_FIND_R
  REPL FIND
  LINK 802
  REPL FIND
  LINK 802
MARK FIND
  HOST T
  TEST X = T
  TJMP DISABLE
    LINK 801
    JUMP FIND
  MARK DISABLE
    @REP 5
    NOOP
    @END
    COPY 0 #POWR
    HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 37     | 31   | 40       |

# 19: Emerson's Guide (Streetsmarts GIS Database)

<div align="center"><img src="EXAPUNKS - Emerson's Guide (52, 40, 6, 2024-06-23-17-12-33).gif" /></div>

## Instructions
> Each host contains a list of restaurants and their ratings, from one to five stars (file 200). Locate the entry that corresponds to the Last Stop on Eddy Street and change its rating from one to five stars.
> 
> The name of the target restaurant and its location within the GIS grid is available in file 300. The first coordinate is the number of times to move east, while the second coordinate is the number of times to move north (positive) or south (negative).
> 
> For more information see "Network Exploration: Geographic Information Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
SEEK 1
COPY F T
LINK 800
MARK EAST
  FJMP EAST_DONE
  LINK 801
  SUBI T 1 T
  JUMP EAST
MARK EAST_DONE
COPY F X
MARK NORTH_SOUTH
  TEST X < 0
  TJMP SOUTH
  TEST X = 0
  TJMP FOUND
    LINK 800
    SUBI X 1 X
    JUMP NORTH_SOUTH
  MARK SOUTH
    LINK 802
    ADDI X 1 X
    JUMP NORTH_SOUTH
MARK FOUND
  SEEK -3
  COPY F X
  WIPE
  GRAB 200
  MARK WRITE
    TEST F = X
    TJMP WRITE_STARS
      SEEK 5
      JUMP WRITE
    MARK WRITE_STARS
      COPY F X
      @REP 4
      COPY X F
      @END
      HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 52     | 40   | 6        |

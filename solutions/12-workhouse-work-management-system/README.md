# 12: Workhouse (Work Management System)

<div align="center"><img src="EXAPUNKS - WorkHouse (344, 58, 2, 2024-06-23-16-38-30).mp4" /></div>

## Instructions
> Locate EMBER-2's user file in the *users* host and overwrite it so that the sum of the values is the same but no individual value exceeds $75. All values, except for the last, must be the maximum value ($75). You will need to add additional values to accomplish this.
> 
> EMBER-2's username is available in file 300.
> 
> Note that the sum of the values in EMBER-2's account will always be less than $10,000.
> 
> For more information see "Network Exploration: Workhouse" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
WIPE
LINK 800
GRAB 199
MARK READ_NAMES
  TEST F = X
  TJMP READ_NAMES_END
  SEEK 2
  JUMP READ_NAMES
MARK READ_NAMES_END
  SEEK 1
  COPY F X
  DROP
LINK 799
GRAB X
COPY 0 X
SEEK 2
MARK READ_FILE
  ADDI X F X
  SEEK -1
  VOID F
  TEST EOF
  FJMP READ_FILE
MARK WRITE_FILE
  TEST X < 1500
  TJMP SMALL
  SUBI X 1500 X
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  COPY 75 F
  JUMP WRITE_FILE
MARK SMALL
  TEST X < 75
  TJMP REMAINDER
  SUBI X 75 X
  COPY 75 F
  JUMP WRITE_FILE
MARK REMAINDER
  COPY X F
  DROP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 344    | 58   | 2        |

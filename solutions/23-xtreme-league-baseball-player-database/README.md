# 23: Xtreme League Baseball (Player Database)

<div align="center"><img src="EXAPUNKS - Xtreme League Baseball (308, 53, 1, 2024-06-23-17-24-34).mp4" /></div>

## Instructions
> The hosts *active* and *penalty* contain files that correspond to extreme baseball players (files 200-299), along with a directory file that contains a list of those files' IDs (file 199). Each player file contains their name and the following statistics in this order: BA, ZA, APB, WRT, OI, OD, PC, and PS.
> 
> Create a file in your host with the name of the player with the highest score using EMBER-2's algorithm:
> 
> SCORE = (BA + ZA + APB) / 3 + ( WRT \* OI ) / OD + (PC - PS) \* 20
> 
> Players in the *penalty* host should be ignored, as they are currently banned from the game.

## Solution

### [XA](XA.exa) (local)
```asm
LINK 800
GRAB 199
MARK READ_ENTRIES
  COPY F X
  REPL COUNT
  TEST EOF
  VOID M
  FJMP READ_ENTRIES
MARK READ_END
  MODE
  COPY 1 M
  HALT
MARK COUNT
  GRAB X
  SEEK 1
  COPY F T
  ADDI T F T
  ADDI T F T
  DIVI T 3 X
  COPY F T
  MULI T F T
  DIVI T F T
  ADDI X T X
  COPY F T
  SUBI T F T
  MULI T 20 T
  ADDI X T X
  MODE
  COPY 0 M
  COPY X M
  COPY X M
  SEEK -9999
  COPY F M
  MODE
  COPY 1 M
  DROP
```

### [MX](MX.exa) (global)
```asm
COPY -9999 X
MAKE
MARK TRACK
  COPY M T
  TJMP TRACK_END
  TEST M > X
  TJMP NEW_MAX
    VOID M
    VOID M
    JUMP TRACK
  MARK NEW_MAX
    COPY M X
    COPY M F
    SEEK -1
    JUMP TRACK
MARK TRACK_END
  DROP
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 308    | 53   | 1        |

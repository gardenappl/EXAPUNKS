# 21: Sawayama Wonderdisc (Drive Controller)

<div align="center"><img src="EXAPUNKS - Sawayama WonderDisc (8291, 54, 63, 2024-06-23-17-18-15).gif" /></div>

## Instructions
> Modify your WonderDisc, which normally only plays SSEA region games, to play games from any region.
> 
> The SSEA region code is available in file 300.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Hardware Hacks: Sawayama WonderDisc" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
DROP
LINK 800
COPY 8 #AUTH
COPY 0 #AUTH
COPY 3 #AUTH
COPY 2 #AUTH
COPY 7 #AUTH
COPY 1 #AUTH
COPY 0 #AUTH
COPY 4 #AUTH
COPY 9 #AUTH
COPY 5 #AUTH
COPY 1 #AUTH
COPY 2 #AUTH
COPY 5 #AUTH
COPY 2 #AUTH
COPY 6 #AUTH
REPL READ

LINK 800
MARK WRITE
  MAKE
  MARK WRITE_FILE
    COPY M T
    TJMP WRITE_DAT
    COPY M T
    TJMP WRITE_CODE
  MARK WRITE_END
    DROP
    JUMP WRITE
  MARK WRITE_DAT
    COPY M F
    JUMP WRITE_FILE
  MARK WRITE_CODE
    COPY X F
    JUMP WRITE_FILE

MARK READ
  COPY #TRAK T
  LINK 801
  GRAB T
  MARK READ_FILE
    TEST F > -9999
    COPY T M
    SEEK -1
    COPY F M
    TEST EOF
    FJMP READ_FILE
  MARK READ_END
    COPY 0 M
    COPY 0 M
    DROP
    LINK -1
  JUMP READ
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 8291   | 54   | 63       |

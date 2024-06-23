# 18: TEC EXA-Blaster Modem (Radio Stations)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster™ Modem (246, 62, 22, 2024-06-23-17-03-33).mp4" /></div>

## Instructions
> ﻿Connect to each radio station and replace every song in the playlist (file 200) with ‗CAN'T (NOT) GET OVER YOU‗ by ‗ME2U‗ (file 300). Each song in a playlist consists of two keywords: the song name and the artist name.
> 
> A list of phone numbers for the radio stations is available in file 301.
> 
> Note that EXAs in global mode can only communicate if there is a path of links connecting them.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
GRAB 300
SEEK 1
COPY F X
LINK 800
DROP
LINK -1
GRAB 301
LINK 800
COPY 8 T
MARK NUM_LOOP
  @REP 11
  COPY F #DIAL
  @END
  REPL WRITE_NAME
  REPL WRITE_ART
  SUBI T 1 T
  @REP 2
  NOOP
  @END
  COPY -1 #DIAL
  TJMP NUM_LOOP
LINK -1
DROP
LINK 800
GRAB 300
LINK -1
HALT

MARK WRITE_NAME
  GRAB 300
  COPY F X
  DROP
  LINK 800
  GRAB 200
  MARK NAME_LOOP
    COPY X F
    SEEK 1
    TEST EOF
    TJMP NAME_END
    JUMP NAME_LOOP
  MARK NAME_END
  COPY 1 M
  HALT

MARK WRITE_ART
  LINK 800
  VOID M
  GRAB 200
  SEEK 1
  MARK ART_LOOP
    COPY X F
    SEEK 1
    TEST EOF
    TJMP ART_END
    JUMP ART_LOOP
  MARK ART_END
  HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 246    | 62   | 22       |

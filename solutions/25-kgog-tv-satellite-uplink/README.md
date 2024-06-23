# 25: KGOG-TV (Satellite Uplink)

<div align="center"><img src="EXAPUNKS - KGOG-TV (375, 89, 8, 2024-06-23-17-25-48).mp4" /></div>

## Instructions
> Align the satellite dish with the target satellite by setting the azimuth, elevation, and frequency. Then transmit the data from EMBER-2's video (file 301) after encrypting it using the TV station's encryption key (file 199).
> 
> The azimuth, elevation, and frequency of the target satellite are available in file 300.
> 
> Note that you must align the satellite dish before transmitting any data.
> 
> For more information see "Look to the Stars with Satellite Uplink Systems" in the second issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
GRAB 300
LINK 800
LINK 799
SEEK 1
COPY F X
REPL AZIMUTH
SEEK 1
COPY F X
SEEK 1
COPY F T
WIPE
MARK FREQ_ELEVATION
  COPY T #FREQ
  LINK 801
  TEST #ELEV = X
  TJMP ELEV_DONE
  TEST #ELEV < X 
  TJMP ELEV_LOW
  MARK ELEV_HIGH
    COPY -1 #MOTR
    TEST #ELEV = X
    FJMP ELEV_HIGH
    JUMP ELEV_DONE
  MARK ELEV_LOW
    COPY 1 #MOTR
    TEST #ELEV = X
    FJMP ELEV_LOW
  MARK ELEV_DONE
    LINK -1
    COPY 1 M
    HALT
MARK AZIMUTH
  LINK 800
  TEST #AZIM = X
  TJMP AZIM_DONE
  TEST #AZIM < X
  TJMP AZIM_LOW
  MARK AZIM_HIGH
    COPY -1 #MOTR
    TEST #AZIM = X
    FJMP AZIM_HIGH
    JUMP AZIM_DONE
  MARK AZIM_LOW
    COPY 1 #MOTR
    TEST #AZIM = X
    FJMP AZIM_LOW
  MARK AZIM_DONE
    LINK -1
    COPY 1 M
    HALT
```

### [XB](XB.exa) (local)
```asm
GRAB 301
LINK 800
REPL READ_KEY
LINK 799
VOID M
VOID M
MODE
SEEK 1
MARK WRITE_DATA
  COPY 0 M
  SUBI F 9999 X
  ADDI X M X
  TEST X > 0
  TJMP WRAP
    ADDI X 9999 #DATA
    TEST EOF
    FJMP WRITE_DATA
    JUMP DATA_END
  MARK WRAP
    SUBI X 1 #DATA
    TEST EOF
    FJMP WRITE_DATA
  MARK DATA_END
    COPY 1 M
    WIPE
    HALT
MARK READ_KEY
  GRAB 199
  MODE
  MARK SEND_KEY
    COPY M T
    TJMP KEY_END
    COPY F M
    TEST EOF
    FJMP SEND_KEY
    SEEK -9999
    JUMP SEND_KEY
  MARK KEY_END
    HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 375    | 89   | 8        |

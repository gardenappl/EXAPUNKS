# 11: UC Berkeley (EECS Department)

<div align="center"><img src="EXAPUNKS - UC Berkeley (128, 48, 7, 2024-06-23-16-38-02).mp4" /></div>

## Instructions
> ﻿Locate the specified host (either *tape-1*, *tape-2*, or *tape-3*), and then locate the specified entry (‗ПАСЬЯНС‗) in the tape backup file in that host (file 200). Create a file in your host containing the entry's data.
> 
> The names of the target host and entry are available in file 300.
> 
> For more information see "Accessing Data in Legacy Storage Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
LINK 800
LINK 800
HOST X
TEST X = F
TJMP SEND
SEEK -1
LINK 800
LINK 800
HOST X
TEST X = F
TJMP SEND
SEEK -1
LINK 800
LINK 800
VOID F
MARK SEND
  COPY F X
  WIPE
  GRAB 200
  SEEK 9999
  SEEK -3
  MARK READ_ENTRY
    TEST F = X
    TJMP FOUND_ENTRY
    SEEK -4
    JUMP READ_ENTRY
  MARK FOUND_ENTRY
    COPY F X
    COPY F T
    COPY T M
    SEEK -9999
    SEEK X
    MARK SEND_X
      COPY F M
      SUBI T 1 T
      TJMP SEND_X
DROP
HALT
```

### [XB](XB.exa) (global)
```asm
COPY M T
MAKE
MARK RECV_X
  COPY M F
  SUBI T 1 T
  TJMP RECV_X
DROP
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 128    | 48   | 7        |

# 15: Trash World News (Unknown Context)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (563, 36, 3, 2024-06-23-16-40-29).gif" /></div>

## Instructions
> ﻿Find and replace the keywords in the target message (file 212) as directed by EMBER-2.
> 
> A list of keyword pairs indicating which words should be found and what they should be replaced with is available in file 300. For example, the keyword ‗AI‗ should be replaced with the keyword ‗COLLECTIVE‗. Each keyword will only occur once, but may occur in any order.
> 
> Also, move file 200 to the *outbox*.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
REPL OUTBOX
LINK 799
COPY F X
REPL MODIFY_FILE

MARK READ_MAP
  COPY F M
  TEST EOF
  COPY T M
  TJMP READ_MAP_END
    COPY F M
    JUMP READ_MAP
  MARK READ_MAP_END
    WIPE
    HALT
  
MARK MODIFY_FILE
  GRAB 212
  MARK CHECK_WORD
    TEST F = X
    FJMP CHECK_WORD
    SEEK -1
    COPY M F
    COPY M T
    TJMP MODIFY_END
      SEEK -9999
      COPY M X
      JUMP CHECK_WORD
    MARK MODIFY_END
      DROP
      HALT
  
MARK OUTBOX
  GRAB 200
  LINK 800
  DROP
  HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 563    | 36   | 3        |

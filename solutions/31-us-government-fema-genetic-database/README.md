# 31: US Government (Fema Genetic Database)

<div align="center"><img src="EXAPUNKS - U.S. Government (809, 126, 45, 2024-06-24-00-10-23).mp4" /></div>

## Instructions
> ﻿Overwrite the genetic sequence of ‗SEN WALKER CAINE JR‗ with the genetic sequence of ‗PRES WALKER CAINE‗ so that it looks like the younger politician is actually a clone of the older politician.
> 
> The names of these two politicians are available in file 300.
> 
> Note that you may need to overwrite a data chunk with another data chunk from the same file.
> 
> For more information see "Accessing Data in Legacy Storage Systems" in the first issue of the zine.

## Solution

### [FS](FS.exa) (global)
```asm
GRAB 300
LINK 800
COPY F X
DROP
LINK 801
GRAB 200
MARK FIND_SRC
  TEST F = X
  TJMP FOUND_SRC
  SEEK 10
  JUMP FIND_SRC
MARK FOUND_SRC
  COPY 10 T
  MARK COPY_SRC
    COPY 0 M
    COPY F M
    SUBI T 1 T
    TJMP COPY_SRC
  DROP
  LINK -1
  GRAB 300
  SEEK 1
  COPY F X
  WIPE
  LINK 801
  GRAB 200
  COPY 1 M
MARK FIND_DEST
  TEST F = X
  TJMP FOUND_DEST
  SEEK 10
  JUMP FIND_DEST
MARK FOUND_DEST
  COPY 10 T
  MARK COPY_DEST
    COPY 0 M
    COPY F M
    SUBI T 1 T
    TJMP COPY_DEST
MARK END
  COPY 1 M
```

### [RW](RW.exa) (global)
```asm
LINK 800
MAKE
MARK READ_SRC
  COPY M T
  TJMP READ_DONE
  COPY M X
  SWIZ X 0003 T
  ADDI T 800 T
  LINK T
  MODE
  REPL READ_CHUNK
  @REP 10
  COPY M F
  @END
  MODE
  LINK -1
  JUMP READ_SRC
  
MARK READ_CHUNK
  SWIZ X 0002 T
  ADDI T 200 T
  GRAB T
  MODI X 10 T
  MULI T 10 T
  SEEK T
  @REP 10
  COPY F M
  @END
  HALT

MARK READ_DONE
  SEEK -9999
MARK WRITE_DEST
  COPY M T
  TJMP WRITE_DONE
  COPY M X
  SWIZ X 0003 T
  ADDI T 800 T
  LINK T
  MODE
  REPL WRITE_CHUNK
  @REP 10
  COPY F M
  @END
  MODE
  LINK -1
  JUMP WRITE_DEST
  
MARK WRITE_CHUNK
  SWIZ X 0002 T
  ADDI T 200 T
  GRAB T
  MODI X 10 T
  MULI T 10 T
  SEEK T
  @REP 10
  COPY M F
  @END

MARK WRITE_DONE
  WIPE
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 809    | 126  | 45       |

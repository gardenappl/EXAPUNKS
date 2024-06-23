# 26: Equity First Bank (San Francisco - ATMs Offline)

<div align="center"><img src="EXAPUNKS - Equity First Bank (142, 49, 2, 2024-06-23-17-26-46).gif" /></div>

## Instructions
> ﻿Move EMBER-2's new account (file 300) into *checking*. Then iterate over the checking accounts listed in the directory (file 199) and, in that order, transfer $1.00 from each target account to EMBER-2's account. Finally, add the file ID of EMBER-2's account file to the end of the directory.
> 
> The keywords ‗CREDIT‗ and ‗DEBIT‗ are available in file 301.
> 
> For more information see "Network Exploration: Equity First Bank" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 301
COPY F X
COPY F T
DROP
GRAB 300
LINK 800
LINK 800
REPL DIR
MARK CREDIT
  COPY M T
  TJMP CREDIT_END
  COPY M T
  COPY F M
  SEEK 9999
  COPY T F
  COPY X F
  COPY 1 F
  COPY 0 F
  SEEK -9999
  JUMP CREDIT
MARK CREDIT_END
  HALT

MARK DIR
  COPY T X
  GRAB 199
  MARK DIR_READ
    COPY F T
    REPL DEBIT
    COPY 0 M
    TEST EOF
    MODE
    VOID M
    MODE
    FJMP DIR_READ
  MARK DIR_END
    COPY 1 M
    COPY 300 F
    HALT

MARK DEBIT
  GRAB T  
  COPY F M
  SEEK 9999
  COPY M F
  COPY X F
  COPY 1 F
  COPY 0 F
  MODE
  COPY 1 M
  HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 142    | 49   | 2        |

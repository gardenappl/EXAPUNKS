# 8: Zebros Copies (Point-Of-Sale System)

<div align="center"><img src="EXAPUNKS - Zebros Copies (80, 32, 2, 2024-06-23-16-37-01).gif" /></div>

## Instructions
> Erase Ghast's debt to the copy shop by zeroing out his balance in the customer database (file 200) and appending a payment to the payment log (file 201) with today's date and the exact amount of his prior balance.
> 
> Ghast's customer ID is available in file 300.
> 
> For more information see "Network Exploration: Digicash Point-of-Sale Systems" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
COPY F X
WIPE
LINK 800
REPL READ_DATE
  GRAB 200
  MARK READ_LINE
    TEST F = X
    TJMP FOUND
      SEEK 2
      JUMP READ_LINE
    MARK FOUND
      COPY F X
      SEEK -1
      COPY 0 F
      COPY F T
      SEEK -1
      COPY 0 F
      DROP
  GRAB 201
  SEEK 9999
  COPY M F
  COPY M F
  COPY X F
  COPY T F
  DROP
  HALT
MARK READ_DATE
  LINK 801
  COPY #DATE M
  COPY X M
  HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 80     | 32   | 2        |

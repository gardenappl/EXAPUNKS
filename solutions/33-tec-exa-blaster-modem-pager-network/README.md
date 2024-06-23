# 33: TEC EXA-Blaster Modem (Pager Network)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster™ Modem (805, 52, 9, 2024-06-24-01-39-51).gif" /></div>

## Instructions
> Connect to each pager and copy EMBER-2's message (file 300) to the screen (#DATA). Then activate all of the pagers at exactly the same time by writing a value to each #PAGE register in the same cycle.
> 
> A list of phone numbers for the pagers is available in file 301.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [DI](DI.exa) (global)
```asm
GRAB 301
LINK 800
COPY 8 X

; 100 CYCLES PER ITER
MARK DIAL
  @REP 11
  COPY F #DIAL
  @END
  SUBI X 1 X
  REPL ENTER
  COPY 41 T
  ; 82 CYCLES
  MARK DIAL_WAIT
    SUBI T 1 T
    TJMP DIAL_WAIT
  NOOP
  COPY -1 #DIAL
  TEST X > 0
  TJMP DIAL
WIPE
HALT
  
MARK ENTER
  LINK 800
  MARK RECV_MSG
    COPY M #DATA
    COPY M T
    FJMP RECV_MSG
  MULI X 50 T
  FJMP RESONATE
  ; 100*N CYCLES
  MARK ENTER_WAIT
    SUBI T 1 T
    TJMP ENTER_WAIT
  MARK RESONATE
    COPY 1 #PAGE
  
  
```

### [MS](MS.exa) (global)
```asm
GRAB 300
COPY 8 X
MARK SEND_MSGS
  MARK SEND_MSG
    COPY F M
    TEST EOF
    COPY T M
    FJMP SEND_MSG
  SEEK -9999
  SUBI X 1 X
  TEST X > 0
  TJMP SEND_MSGS
  
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 805    | 52   | 9        |

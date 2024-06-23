# 27: TEC EXA-Blaster Modem (Dataphone Network)

<div align="center"><img src="EXAPUNKS - TEC EXA-Blaster™ Modem (1355, 67, 9, 2024-06-23-17-28-17).gif" /></div>

## Instructions
> Using your modem, connect to each dataphone so that EMBER-2 will have a list of valid phone numbers.
> 
> Each dataphone contains a list of the owner's contacts (file 200). The phone number of one of these dataphones is in your host (file 300), while the rest are in the contact list of another dataphone.
> 
> Note that each dataphone (aside from the first) will appear in exactly one other dataphone's contact list, in such a way that you can find them all without getting stuck in a loop.
> 
> For more information see "Hacker Skills: Modem Control at the Direct Level" in the second issue of the zine.

## Solution

### [CL](CL.exa) (global)
```asm
GRAB 300
LINK 800

MARK ENTER_NUM
  @REP 11
  COPY F #DIAL
  @END
  REPL GET_NUMS
  SEEK -9999
  @REP 11
  VOID F
  @END
  TEST MRD
  FJMP ENTER_NUM
  VOID M
  SEEK 9999
  ADDI X 1 X
  TEST X = 8
  COPY T M
  TJMP CLEANUP
  MARK ADD_NUM
    TEST MRD
    FJMP END_NUM
    VOID M
    @REP 11
    COPY M F
    @END
    JUMP ADD_NUM
  MARK END_NUM
    SEEK -9999
    COPY -1 #DIAL
    JUMP ENTER_NUM

MARK GET_NUMS
  LINK 800
  GRAB 200
  COPY 1 M
  COPY M T
  TJMP END
  MARK SEND_YO
    COPY F M
    JUMP SEND_YO
MARK CLEANUP
  WIPE
MARK END
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1355   | 67   | 9        |

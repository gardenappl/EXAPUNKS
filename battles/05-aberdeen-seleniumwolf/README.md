# 5: Aberdeen (selenium_wolf)

<div align="center"><img src="EXAPUNKS - Aberdeen (2024-06-23-17-32-48).gif" /></div>

## Instructions
> To win this battle you must occupy a majority of the hosts for as long as possible. You occupy a host if you have more EXAs in it than your opponent.
> 
>      Gain one point every cycle you occupy more hosts than your opponent.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> Writing any value to the #NUKE register will destroy all EXAs in that host, including the EXA that triggered it.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
REPL GO_COVE

MARK MAIN
  REPL GO_YARD
;  JUMP MAIN
  JUMP STAY

MARK GO_YARD
  LINK 800
MARK YARD
  REPL GO_801
  REPL GO_802
 ; REPL GO_801
;  REPL GO_802
  JUMP STAY

@REP 3
MARK GO_@{800,1}
  LINK @{800,1}
MARK STAY_@{800,1}
  REPL STAY
  REPL GO_800
  JUMP STAY

@END

MARK GO_COVE
  LINK 800
  LINK 801
  LINK 799
  JUMP STAY

MARK STAY
;  REPL STAY
  JUMP STAY
```


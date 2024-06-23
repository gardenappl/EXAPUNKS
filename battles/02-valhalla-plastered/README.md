# 2: Valhalla (=Plastered)

<div align="center"><img src="EXAPUNKS - Valhalla (2024-06-23-17-12-46).mp4" /></div>

## Instructions
> To win this battle you must control a majority of the hosts for as long as possible. 
> 
> To take control of a host, write any value to its #CTRL register. Reading from a #CTRL register will tell if you (1) or your opponent (-1) controls the host.
> 
>      Gain one point every cycle you control more hosts than your opponent.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
MARK MAIN
  @REP 8
  REPL GO_@{8,-1}
  @END
  JUMP MAIN
@REP 8
MARK GO_@{8,-1}
LINK 800
@END
MARK WRITE
  COPY 1 #CTRL
  JUMP WRITE
```


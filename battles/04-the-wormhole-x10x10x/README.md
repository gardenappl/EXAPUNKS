# 4: The Wormhole (X10X10X)

<div align="center"><img src="EXAPUNKS - The Wormhole (2024-06-23-17-27-22).mp4" /></div>

## Instructions
> To win this battle you must fill the network's hosts with as many of your EXAs as you can. Note that each pair of test runs has its own unique network layout, with bi-directional links between hosts that use the prime numbers between 2 and 13 as link IDs (2, 3, 5, 7, 11, and 13).
> 
>      Gain one point for every EXA you control in the network at the end of the battle.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
COPY 800 X

MARK GO
  LINK X
  REPL TRY_5_7
  REPL TRY_11_13
MARK TRY_2_3
  COPY 2 X
  REPL GO
  COPY 3 X
  REPL GO
  JUMP WAIT2
MARK TRY_5_7
  COPY 5 X
  REPL GO
  COPY 7 X
  REPL GO
  JUMP WAIT1
MARK TRY_11_13
  COPY 11 X
  REPL GO
  COPY 13 X
  REPL GO
  JUMP WAIT
MARK WAIT2
  NOOP
MARK WAIT1
  NOOP
MARK WAIT
  REPL WAIT
  JUMP WAIT
```


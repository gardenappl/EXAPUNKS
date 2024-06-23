# 1: KGOG-TV (Programming Hub)

<div align="center"><img src="EXAPUNKS - KGOG-TV (2024-06-23-16-41-03).mp4" /></div>

## Instructions
> To win this battle you must make your movies play for longer than your opponent's. A movie will play when that movie's file is the only movie file sitting in a *channel* host.
> 
>      Gain one point every cycle for each of your movies that is playing (files 210 and 211).
> 
>      Lose one point every cycle that a movie file that isn't yours (files 230, 231, and 265) is held by an EXA you control or is sitting in your host.
> 
>      Lose one point every time one of your EXAs executes a KILL instruction.
> 
> Note that you may only battle your Steam friends after beating the NPC opponent. To view the list of possible opponents, click the "SELECT OPPONENT" button above.
> 
> For more information see "Hacker Battle Domination" in the second issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK ATTACK
  GRAB 210
  LINK 828
  DROP
  REPL DEFEND
  LINK -1
  GRAB 211
  LINK 867
  DROP
  REPL DEFEND
  LINK -1
  LINK 809
  REPL DEFEND
  LINK -1


MARK DEFEND
  RAND 230 232 X
  TEST X < 232
  TJMP AWAY
  COPY 265 X
  MARK AWAY
    GRAB X
    LINK -1
    WIPE
    HALT
```


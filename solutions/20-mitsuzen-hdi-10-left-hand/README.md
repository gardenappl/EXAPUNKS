# 20: Mitsuzen HDI-10 (Left Hand)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (99, 38, 263, 2024-06-23-17-13-50).mp4" /></div>

## Instructions
> There are three nerve signals that need to be relayed: muscle control (M), which runs from your central nervous system (CNS) to your hand (HND), and heat (H) and pressure (P), which run the other direction.
> 
> For each signal, read a value from the input nerve and relay it to the output nerve. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL HP
MARK M
  @REP 2
  LINK -3
  @END
  MARK M_READ
    COPY #NERV X
    REPL M_WRITE
    JUMP M_READ
  MARK M_WRITE
    @REP 4
    LINK 3
    @END
    COPY X #NERV
    HALT
MARK HP
  @REP 3
  LINK 3
  @END
  MARK HP_READ
    COPY #NERV X
    LINK 3
    COPY #NERV T
    LINK -3
    REPL HP_WRITE
    JUMP HP_READ
  MARK HP_WRITE
    @REP 6
    LINK -3
    @END
    COPY X #NERV
    LINK -3
    COPY T #NERV
    HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 99     | 38   | 263      |

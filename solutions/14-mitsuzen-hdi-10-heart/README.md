# 14: Mitsuzen HDI-10 (Heart)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (85, 30, 7, 2024-06-23-16-39-48).gif" /></div>

## Instructions
> Read a value from the nerve connected to your central nervous system (CNS) and make your heart beat by writing a sequence of values to your sinoatrial (SA-N) and atrioventricular (AV-N) nodes as indicated in the HDI-10 I/O log when holding the "SHOW GOAL" button. The length of each sequence of values should be equal to the value from the CNS divided by -10. Repeat _ad infinitum_.
> 
> It is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK LISTEN
  DIVI #NERV -10 X
  COPY X M
  COPY X M
  JUMP LISTEN
```

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 1
LINK 1
MARK SAN
  COPY 40 #NERV
  COPY -70 #NERV
  SUBI M 2 T
  MARK REST
    COPY -70 #NERV
    SUBI T 1 T
    TJMP REST
  JUMP SAN
```

### [XC](XC.exa) (global)
```asm
LINK 800
LINK 3
LINK 3
MARK AVN
  COPY -70 #NERV
  COPY 40 #NERV
  SUBI M 2 T
  MARK REST
    COPY -70 #NERV
    SUBI T 1 T
    TJMP REST
  JUMP AVN
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 85     | 30   | 7        |

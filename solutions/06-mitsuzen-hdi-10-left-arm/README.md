# 6: Mitsuzen HDI-10 (Left Arm)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (184, 24, 5, 2024-06-23-16-36-14).gif" /></div>

## Instructions
> Read a value from the nerve connected to your central nervous system (CNS) and relay it to the nerve connected to your arm (ARM), clamping the value so that it never goes below -120 or above 50. Repeat _ad infinitum_.
> 
> Since this task takes place inside a network you control— that is, your own body— it is not necessary to leave no trace. Your EXAs should be written to operate indefinitely.
> 
> Note that #NERV is a _hardware register_, not a file. You can use it directly in your code like any other register.
> 
> For more information about the phage see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
REPL READ_LOOP
 LINK 1
 LINK 1
 LINK 1
 LINK 1
 MARK WRITE_LOOP
  COPY M X
  TEST X > 50
  TJMP WRITE_HIGH
   COPY X #NERV
   JUMP WRITE_LOOP
  MARK WRITE_HIGH
   COPY 50 #NERV
   JUMP WRITE_LOOP
MARK READ_LOOP
 COPY #NERV X
 TEST X < -120
 TJMP READ_LOW
  COPY X M
  JUMP READ_LOOP
 MARK READ_LOW
  COPY -120 M
  JUMP READ_LOOP

```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 184    | 24   | 5        |

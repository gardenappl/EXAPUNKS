# 16: TEC Redshift (Development Kit)

<div align="center"><img src="EXAPUNKS - TEC Redshift™ (6951, 26, 4, 2024-06-23-16-42-51).mp4" /></div>

## Instructions
> There is an unknown three-digit code (such as 4-7-3) that, when entered one digit at a time into #PASS, will unlock the link between *debug* and *secret*. Find the three-digit code and create a file in your host that contains the code as a sequence of three values, followed by the development kit's RDK ID.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
MARK LOOP
  SWIZ X 0003 #PASS
  SWIZ X 0002 #PASS
  SWIZ X 0001 #PASS
  REPL TRY
  ADDI X 1 X
  TEST MRD
  FJMP LOOP
VOID M
HALT
MARK TRY
  LINK 800
  COPY 1 M
  GRAB 199
  COPY F T
  DROP
  LINK -1
  LINK -1
  MAKE
  SWIZ X 0003 F
  SWIZ X 0002 F
  SWIZ X 0001 F
  COPY T F
  DROP
  HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 6951   | 26   | 4        |

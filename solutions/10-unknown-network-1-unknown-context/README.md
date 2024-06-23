# 10: Unknown Network 1 (Unknown Context)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 1 (35, 19, 27, 2024-06-23-16-37-30).gif" /></div>

## Instructions
> Find file 276 in the network and bring it back to your host.
> 
> Note that an EXA cannot grab a file that is being held by another EXA.

## Solution

### [XA](XA.exa) (global)
```asm
COPY 4 T
COPY 800 X
MARK GO
  LINK X
  SUBI T 1 T
  FJMP GET
  COPY 800 X
  REPL GO
  COPY 801 X
  JUMP GO
MARK GET
  KILL
  GRAB 276
  LINK -1
  LINK -1
  LINK -1
  LINK -1
  DROP
  HALT
  
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 35     | 19   | 27       |

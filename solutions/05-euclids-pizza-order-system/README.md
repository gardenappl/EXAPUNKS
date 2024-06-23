# 5: Euclid's Pizza (Order System)

<div align="center"><img src="EXAPUNKS - Euclid's Pizza (29, 29, 1, 2024-06-23-16-35-59).gif" /></div>

## Instructions
> Append your order (file 300) to the end of the order list (file 200).
> 
> Note that all orders, including yours, will consist of exactly five keywords.

## Solution

### [XA](XA.exa) (global)
```asm
GRAB 300
LINK 800
COPY F X
COPY F T
DROP
GRAB 200
SEEK 9999
COPY X F
COPY T F
DROP
GRAB 300
SEEK 2
COPY F X
COPY F T
DROP
GRAB 200
SEEK 9999
COPY X F
COPY T F
DROP
GRAB 300
SEEK 4
COPY F X
WIPE
GRAB 200
SEEK 9999
COPY X F
DROP
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 29     | 29   | 1        |

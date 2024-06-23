# 4: Trash World News (Tutorial 4)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (306, 13, 2, 2024-06-23-16-35-34).gif" /></div>

## Instructions
> File 200 contains exactly one number, N. Create a new file in the *outbox* containing the numbers N through 0 in decreasing order. When you are finished, delete file 200.
> 
> For help completing this task see "Ghast Walks U Thru It" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
GRAB 200
COPY F T
WIPE
LINK 800
MAKE
MARK WRITE
COPY T F
SUBI T 1 T
TJMP WRITE
COPY 0 F
DROP
HALT

```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 306    | 13   | 2        |

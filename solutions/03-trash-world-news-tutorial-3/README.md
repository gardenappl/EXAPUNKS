# 3: Trash World News (Tutorial 3)

<div align="center"><img src="EXAPUNKS - TRASH WORLD NEWS (11, 15, 4, 2024-06-23-16-35-20).mp4" /></div>

## Instructions
> File 199 contains exactly two values: a keyword and a number. Create a new file in the *outbox* and copy those two values to it, swapping their order so that the number is first. When you are finished, delete file 199.
> 
> For help completing this task see "Ghast Walks U Thru It" in the first issue of the zine.

## Solution

### [XA](XA.exa) (global)
```asm
LINK 800
LINK 799
GRAB 199
COPY F X
COPY F M
COPY X M
WIPE
HALT
```

### [XB](XB.exa) (global)
```asm
LINK 800
LINK 800
MAKE
COPY M F
COPY M F
DROP
HALT
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 11     | 15   | 4        |

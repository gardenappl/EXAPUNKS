# 32: Unknown Network 2 (Unknown Context)

<div align="center"><img src="EXAPUNKS - UNKNOWN NETWORK 2 (108, 74, 53, 2024-06-24-00-38-18).gif" /></div>

## Instructions
> Terminate all other EXAs and bring any files they were holding back to your host. Only EXAs in the central host will be holding files, and their file IDs will always be between 200 and 299, inclusive.
> 
> Note that some links may become non-traversable as a result of your actions.

## Solution

### [XA](XA.exa) (global)
```asm
@REP 5
LINK 800
@END
@REP 6
KILL
@END
COPY 20 T
REPL TRY_FILES_2
REPL TRY_FILES_3
REPL TRY_FILES_4
REPL TRY_FILES_5
MARK TRY_FILES_1
  SUBI T 1 T
  ADDI T 200 X
  REPL TRY_FILE
  TJMP TRY_FILES_1
  HALT
MARK TRY_FILES_2
  SUBI T 1 T
  ADDI T 220 X
  REPL TRY_FILE
  TJMP TRY_FILES_2
  HALT
MARK TRY_FILES_3
  SUBI T 1 T
  ADDI T 240 X
  REPL TRY_FILE
  TJMP TRY_FILES_3
  HALT
MARK TRY_FILES_4
  SUBI T 1 T
  ADDI T 260 X
  REPL TRY_FILE
  TJMP TRY_FILES_4
  HALT
MARK TRY_FILES_5
  SUBI T 1 T
  ADDI T 280 X
  REPL TRY_FILE
  TJMP TRY_FILES_5
MARK RETURN
  @REP 3
  LINK -1
  REPL DESTROY_@{1,1}
  @END
  LINK -1
  JUMP DESTROY_4
@REP 3
MARK DESTROY_@{1,1}
  NOOP
  NOOP
@END
MARK DESTROY_4
  KILL
  KILL
  HALT

MARK TRY_FILE
  GRAB X
  @REP 5
  LINK -1
  @END
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 108    | 74   | 53       |

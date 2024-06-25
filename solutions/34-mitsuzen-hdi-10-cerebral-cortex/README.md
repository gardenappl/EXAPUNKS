# 34: Mitsuzen HDI-10 (Cerebral Cortex)

<div align="center"><img src="EXAPUNKS - Mitsuzen HDI-10 (1619, 141, 89, 2024-06-26-00-58-07).gif" /></div>

## Instructions
> Create a file in your host containing the hostname and hardware register value of each neuron exactly once, sorted as pairs from lowest to highest hostname.
> 
> Note that each test run has its own unique network layout.
> 
> For more information see "Debugging the Phage" in the first issue of the zine.

## Solution

### [XA](XA.exa) (local)
```asm
LINK 800
MAKE
COPY 1 F
JUMP TEST_DIRS

MARK TRY_DIR
  LINK X
  MULI X -1 T
  LINK T
  COPY 1 M
  MAKE
  MARK RECV_PATH
    COPY M F
    COPY M T
    FJMP RECV_PATH
  COPY X F
  LINK X
MARK TEST_DIRS
  COPY -3 X
  MARK TEST_DIR
    MULI X -1 T
    SEEK -1
    TEST F = T
    TJMP TEST_NEXT_DIR
    REPL TRY_DIR
    NOOP
    NOOP
    NOOP
    TEST MRD
    FJMP TEST_NEXT_DIR
    VOID M
    SEEK -9999
    MARK SEND_PATH
      COPY F M
      TEST EOF
      COPY T M
      FJMP SEND_PATH
  MARK TEST_NEXT_DIR
    ADDI X 2 X
    TEST X = 5
    FJMP TEST_DIR
  REPL TRY_GET_INFO
  JUMP GET_INFO

MARK TRY_GET_INFO
  COPY #NERV M
  HALT

MARK GET_INFO
  TEST MRD
  FJMP END
  HOST F
  COPY M F
  SEEK -3
  COPY F X
MARK RETURN
  MULI X -1 T
  LINK T
  SEEK -1
  VOID F
  SEEK -1
  COPY F X
  TEST X > -9999
  TJMP RETURN
MARK SEND_INFO
  COPY 1 M
;NOW LOCAL COMM
MODE
MARK SEND_HOST
  SEEK -9999
  COPY F M
  COPY M T
  FJMP SEND_HOST
MARK SEND_VALUE
  COPY F M
MARK END
  WIPE
  HALT
```

### [RW](RW.exa) (local)
```asm
MAKE
MARK READ_VALUES
  COPY 40 X
  MARK WAIT_FOR_MORE
    TEST MRD
    TJMP READ_VALUE
    SUBI X 1 X
    TEST X > 0
    TJMP WAIT_FOR_MORE
    HALT
  MARK READ_VALUE
    VOID M

;NOW LOCAL COMM
MODE
COPY M X
SEEK -9999
MARK WRITE_HOST
  TEST EOF
  TJMP INSERT_HERE
  TEST X < F
  TJMP INSERT_MOVE
  SEEK 1
  JUMP WRITE_HOST
MARK INSERT_MOVE
  SEEK -1
  COPY F X
  SEEK -1
  COPY -9999 F
  MARK MOVE_HOSTS
    SEEK 1
    TEST EOF
    TJMP INSERT_MOVE2
    COPY F T
    SEEK -1
    COPY X F
    COPY T X
    JUMP MOVE_HOSTS
MARK INSERT_MOVE2
  COPY X F
  MARK FIND_TMP
    SEEK -3
    TEST F = -9999
    FJMP FIND_TMP
  COPY F X
  MARK MOVE_VALUES
    SEEK 1
    TEST EOF
    TJMP INSERT_MOVE3
    COPY F T
    SEEK -1
    COPY X F
    COPY T X
    JUMP MOVE_VALUES
MARK INSERT_MOVE3
  COPY X F
  SEEK -1
  MARK FIND_TMP2
    SEEK -3
    TEST F = -9999
    FJMP FIND_TMP2
  ;WRITE NEW VALUE
  SEEK -1
MARK INSERT_HERE
  COPY 0 M
  COPY M F
  COPY 1 M
  COPY M F
MODE
JUMP READ_VALUES
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 1619   | 141  | 89       |

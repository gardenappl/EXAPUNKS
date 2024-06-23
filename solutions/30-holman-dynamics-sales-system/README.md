# 30: Holman Dynamics (Sales System)

<div align="center"><img src="EXAPUNKS - Holman Dynamics (5619, 130, 3, 2024-06-23-19-54-33).mp4" /></div>

## Instructions
> Create a file in your host containing the contiguous 16-value sequence from the garbage file (file 199) that is a valid credit card number. There will be exactly one such sequence.
> 
> For more information see "How to Validate Credit Card Numbers" in the second issue of the zine.

## Solution

### [SD](SD.exa) (global)
```asm
LINK 800
LINK 802
LINK 799
GRAB 199
MARK READ_ODD1
  TEST EOF
  TJMP READ_END1
  COPY F X
  TEST X = -9999
  TJMP RESET1
  MULI X 2 X
  TEST X > 9
  FJMP SEND_ODD1
    SUBI X 9 X
  MARK SEND_ODD1
  COPY 0 M
  COPY X M
MARK READ_EVEN1
  TEST EOF
  TJMP READ_END1
  COPY F X
  TEST X = -9999
  TJMP RESET1
  COPY 0 M
  COPY X M
  COPY M T
  FJMP END
  JUMP READ_ODD1
MARK RESET1
  COPY 1 M
  JUMP READ_ODD1
MARK READ_END1
  COPY 1 M
  SEEK -9999
MARK READ_SKIP_1ST
  TEST EOF
  TJMP READ_END2
  COPY F X
  TEST X = -9999
  TJMP READ_SKIP_1ST
MARK READ_ODD2
  TEST EOF
  TJMP READ_END2
  COPY F X
  TEST X = -9999
  TJMP RESET2
  MULI X 2 X
  TEST X > 9
  FJMP SEND_ODD2
    SUBI X 9 X
  MARK SEND_ODD2
  COPY 0 M
  COPY X M
MARK READ_EVEN2
  TEST EOF
  TJMP READ_END2
  COPY F X
  TEST X = -9999
  TJMP RESET2
  COPY 0 M
  COPY X M
  COPY M T
  FJMP END
  JUMP READ_ODD2
MARK RESET2
  COPY 1 M
  JUMP READ_SKIP_1ST
MARK READ_END2
;SHOULD NOT REACH THIS
MARK END
  SEEK -16
  COPY 16 T
  MARK END_COPY
    COPY F M
    SUBI T 1 T
    TJMP END_COPY
```

### [CK](CK.exa) (global)
```asm
MAKE
MARK INIT
  COPY 16 X
  MARK INIT_WRITE
    COPY M T
    TJMP RESET
    COPY M F
    COPY M T
    TJMP RESET
    COPY M F
    SUBI X 2 X
    TEST X > 0
    FJMP INIT_WROTE
    COPY 1 M
    JUMP INIT_WRITE
  MARK INIT_WROTE
  SEEK -9999
  COPY 16 T
  MARK INIT_COUNT
    ADDI X F X
    SUBI T 1 T
    TJMP INIT_COUNT
MARK ROLLING
  SWIZ X 0001 T
  COPY T M
  FJMP FOUND
  ; REMOVE 2 DIGITS
  COPY M T
  TJMP RESET
  SEEK -9999
  SUBI X F X
  SUBI X F X
  SEEK -2
  VOID F
  VOID F
  ; ADD N+1 DIGIT
  SEEK 9999
  COPY M T
  COPY T F
  ADDI X T X
  ; ADD N+2 DIGIT
  COPY M T
  TJMP RESET
  COPY M T
  COPY T F
  ADDI X T X
  JUMP ROLLING
MARK RESET
  WIPE
  MAKE
  JUMP INIT
MARK FOUND
  SEEK -9999
  COPY 16 T
  MARK END_COPY
    COPY M F
    SUBI T 1 T
    TJMP END_COPY
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 5619   | 130  | 3        |

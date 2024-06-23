# 17: Digital Library Project (Patron Access System)

<div align="center"><img src="EXAPUNKS - Digital Library Project (307, 32, 74, 2024-06-23-17-02-21).mp4" /></div>

## Instructions
> Books are stored in the host corresponding to the first digit of their call number, while a book's file ID is 200 plus the last two digits of the call number. For example, book 512 would be stored in the host *500-599* as file 212.
> 
> Duplicate each of the books requested by EMBER-2 and bring them back to your host.
> 
> The call numbers for the books EMBER-2 wants are available in file 300.
> 
> Note that EMBER-2 will never request more than one book from the same host.

## Solution

### [XA](XA.exa) (local)
```asm
GRAB 300
MARK BOOK_IDS
  COPY F X
  REPL GET_BOOK
  JUMP BOOK_IDS

MARK GET_BOOK
  LINK 800
  SWIZ X 0003 T
  MARK FIND
    LINK 800
    SUBI T 1 T
    TJMP FIND
  SWIZ X 0021 T
  ADDI T 200 T
  GRAB T
  REPL WRITE_BOOK
  MARK READ_BOOK
    COPY F M
    JUMP READ_BOOK

MARK WRITE_BOOK
  MAKE
  MARK RECEIVE_BOOK
    COPY M F
    NOOP
    TEST MRD
    TJMP RECEIVE_BOOK
  SWIZ X 0003 T
  MARK FIND_BAK
    LINK -1
    SUBI T 1 T
    TJMP FIND_BAK
  LINK -1
```

#### Results
| Cycles | Size | Activity |
|--------|------|----------|
| 307    | 32   | 74       |

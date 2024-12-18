# My first attempt at a custom CPU architecture, assembler, and emulator.

## CPU Instruction Set

### Opcodes (5 bit codes)

| NAME  | DESCRIPTION                                       | USAGE                         | BINARY FORM |
|-------|---------------------------------------------------|-------------------------------|-------------|
| H     | Halts the program execution                       | H                             | 00000       |
| LI    | Load immediate value into $DR                    | LI $DR 16                      | 00001       |
| LR    | Load register value into $DR                     | MV $DR RX                      | 00010       |
| J     | Jump unconditionally                              | J $LINE                       | 00011       |
| JE    | Jump if comparison is equal                       | J $LINE RX RY                 | 00100       |
| JNE   | Jump if comparison is not equal                   | J $LINE RX RY                 | 00101       |
| JL    | Jump if comparison is lesser than                 | JL $LINE RX RY                | 00110       |
| JG    | Jump if comparison is greater than                | JG $LINE RX RY                | 00111       |
| ADDR  | Adds two registers into $DR                       | ADDR $DR RX RY                | 01000       |
| ADDI  | Adds immediate and register into $DR             | ADDI $DR RX 15                 | 01001       |
| SUBR  | Subtracts two registers into $DR                 | SUBR $DR RX RY                 | 01010       |
| SUBI  | Subtracts immediate from register into $DR       | SUBI $DR RX 15                 | 01011       |
| MULR  | Multiplies two registers into $DR                | MULR $DR RX RY                 | 01100       |
| MULI  | Multiplies immediate and register into $DR       | MULI $DR RX 15                 | 01101       |
| DIVR  | Divides two registers into $DR                   | DIVR $DR RX RY                 | 01110       |
| DIVI  | Divides register by immediate into $DR           | DIVI $DR RX 15                 | 01111       |

### Registers (5 bit codes, 32bit size)

| NAME  | DESCRIPTION                                      | BINARY FORM |
|-------|--------------------------------------------------|-------------|
| PC    | Program Counter                                 | 00000       |
| r0    | General purpose register                        | 00001       |
| r1    | General purpose register                        | 00010       |
| r2    | General purpose register                        | 00011       |
| r3    | General purpose register                        | 00100       |
| r4    | General purpose register                        | 00101       |
| r5    | General purpose register                        | 00110       |
| r6    | General purpose register                        | 00111       |
| r7    | General purpose register                        | 01000       |

### Useful details and information

All immediate values are 32bits in length and can be s32 or u32

| KEY   | VALUE                              |
|-------|------------------------------------|
| $DR   | Destination Register              |
| $LINE | Line location in the program      |

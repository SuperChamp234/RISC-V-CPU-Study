# Introduction to RISC-V Architecture

## Base Model

### Registers

-   There are 31 General Purpose Registers x1-x31 in RISC-V CPU, which hold fixed point values.
-   The Register x0 is hardwired to hold the constant 0.
-   There are also two special user-visible registers defined in the architecture.
-   The program counter `pc` register holds the address of the address of the current instruction, while the `fsr` register contains the operating mode and the exeption status of the floating point unit.

### Instruction length encodings

-   The base instructions of RISC-V are 32-bit instructions alligned to 32-bit boundaries.
    -   Such Instructions have their lowest bits set to 11. xxxxxxxxxxxxxxxx | xxxxxxxxxxxbbb11
-   The RISC-V Encoding scheme also allows for variable length instructions, where any number of 16-bit instruction parcels are aligned on 16-bit boundaries.
- 
# Logic Gates

![[Pasted image 20220817200558.png | Might not be visible in Dark Mode]]
Might not be visible in Dark Mode

![[Pasted image 20220817200617.png]]
Full Adder circuit

## TL - Verilog Syntax

Parenthesis can be used to group expressions into more complex logic functions.

If a statement is extended across multiple lines, then these lines should have more indentation than the first line.

TL-Verilog is an indentation sensitive! Each Indentation is three spaces wide.

### Signal Name Regulations

-   Must start with `$`
-   Must be composed of tokens delimited by underscores, tokens consisting of lower case alphabets and ending with zero or multiple digits.
-   Must begin with at least 2 or more alphabetic characters.

![[Pasted image 20220817200910.png | {width=50%}]]

### Vectors

A collection of `N` wires can hold $2^N$ possible values. We can also hold the sign of the vector innit.

Operations like `+, -, >, == , <` can be performed on them.

---

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
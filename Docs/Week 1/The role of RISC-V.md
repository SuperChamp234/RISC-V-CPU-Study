The ISA defines a human-readable form of every instruction, as well as the mapping of those human-readable _assembly instructions_ into bits. In addition to producing binary files, compilers can generate _assembly code_. An _assembler_ can compile the assembly code into a binary file. In addition to providing visibility to compiler output, assembly programs can also be written by hand. This is useful for hardware tests and other situations where direct low-level control is needed.

### Role of RISC-V

RISC-V is also popular for its simplicity and extensibility, in fact, stands for “reduced instruction set computing” and contrasts with “complex instruction set computing” (CISC). RISC-V (pronounced “risk five”) is the fifth in a series of RISC ISA from UC Berkeley.

Like other RISC (and even CISC) ISA, RISC-V is a _load-store architecture_. It contains a register file capable of storing up to 32 values (well, actually 31). Most instructions read from and write back to the register file. Load and store instructions transfer values between memory and the register file.

RISC-V instructions might provide the following fields:

- **Opcode:** provides a general classification for the instruction, over which the rest of the fields build upon.
- **Function field:** Specifies the exact function performed by the instruction, if not fully specified by the opcode.
- **Registers:** (0-31) Identifying the registers in the register file containing the source operand values.
- **Intermediate:** A value contained within the instruction bits themselves. This value may provide an offset for indexing into memory or a value upon which to operate.

![](https://i.imgur.com/yMYI4VS.png)

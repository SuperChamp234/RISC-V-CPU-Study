2## Instruction Memory

- A note on wire vs. reg: The left-hand-side of an assign statement must be a net type (e.g., wire), while the left-hand-side of a procedural assignment (in an `always` block) must be a variable type (e.g., reg). These types (wire vs. reg) have nothing to do with what hardware is synthesized, and are just syntax left over from Verilog's use as a hardware simulation language. 
- Non-blocking assignment statements are **allowed to be scheduled without blocking the execution of the following statements and is specified by a (`<=`) symbol**. The same symbol is used as a relational operator in expressions, and as an assignment operator in the context of a non-blocking assignment. http://www.asic-world.com/tidbits/blocking.html
- Implementation of clock in test bench.
	```verilog
	reg clk;
	initial clk = 0;
	always #10 clk = ~clk;
  ```
- Errors are caused when the circuit is mixed of unsynchronized sequential and combinational logic.
- **Latching:** When the output is to be a net but to be assigned inside a sequential circuit, the output is latched in a register, and then assigned to the wire outside the sequential circuit.
---
## Decode Logic

![](Types-of-instructions.png)

#### R-Type Instructions

![R-Type](R-Type.png)

#### I-Type Instructions

![I-Type](I-Type.png)

#### S-Type Instructions

![](S-Type.png)

#### B-Type Instructions

![](B-Type.png)

#### U-Type Instructions

![](U-Type.png)

#### J-Type Instructions

![](J-Type.png)

#### Misc.

![](Misc.png)

---
## Bus between Decoder and CU

| bus[i] | instr    |
| ------ | -------- |
| 0      | `add`    |
| 1      | `sub`    |
| 2      | `xor`    |
| 3      | `or`     |
| 4      | `and`    |
| 5      | `sll`    |
| 6      | `srl`    |
| 7      | `sra`    |
| 8      | `slt`    |
| 9      | `sltu`   |
| 10     | `addi`   |
| 11     | `xori`   |
| 12     | `ori`    |
| 13     | `andi`   |
| 14     | `slli`   |
| 15     | `srli`   |
| 16     | `srai`   |
| 17     | `slti`   |
| 18     | `sltiu`  |
| 19     | `lb`     |
| 20     | `lh`     |
| 21     | `lw`     |
| 22     | `lbu`    |
| 23     | `lhu`    |
| 24     | `sb`     |
| 25     | `sh`     |
| 26     | `sw`     |
| 27     | `beq`    |
| 28     | `bne`    |
| 29     | `blt`    |
| 30     | `bge`    |
| 31     | `bltu`   |
| 32     | `bgeu`   |
| 33     | `jal`    |
| 34     | `jalr`   |
| 35     | `lui`    |
| 36     | `auipc`  |
| 37     | `ecall`  |
| 38     | `ebreak` |


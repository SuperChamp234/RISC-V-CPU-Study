## Components

- **PC:** or Program Counter holds the address of the next instruction that is to be executed from the fetch. Most instructions execute sequentially. Branch and jump instructions  specify a target instruction to execute next, and the PC logic must update the PC accordingly.
- **Fetch:** Holds the instructions to be executed.
- **Decode Logic:** Now that we hold the instruction, we must decode it to execute it. We must break it into fields based on its type.
- **Register file:** Register file contains the local storage or registers the program is working on. We decode the instruction to find out the registers we will be working on, this register is then read from the register file.
- **Register File Write:** The registers in the register file can also be written to store the output of the register.
- **DMem:** Our test program executes entirely out of the register file and does not require a data memory (DMem). But no CPU is complete without one. The DMem is written to by store instructions and read from by load instructions ~~straight from the edex site

![](https://i.imgur.com/kAsxURh.png)


---
### PC Logic

The PC is a byte address, only referencing the first byte of the address where the instruction is stored in IMem. Each instruction is 4 bytes, so a change in PC is equivalent to 4 bytes of increment in IMem. The PC is reset by the reset signal.


![](https://i.imgur.com/Cejkco3.png)

---
### Accessing memory in RISC-V

The memory can be accessed using the tag

```verilog
`READONLY_MEM($adrs,$$instr[31:0]);
```


## Instruction Memory

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

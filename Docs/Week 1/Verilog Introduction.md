## Different Types of Gate

### AND Gate

```verilog
module andgate(
  input wire a,
  input wire b,
  output wire c);
  
  assign c = a && b;

endmodule
 ```
AND Gate

```verilog
module andgate_tb;
  wire r;
  reg p, q;
  andgate my_gate( .a(p), .b(q), .c(r) );
  
  initial
  begin

    $monitor(p,q,r);
    p = 1'b0;
   	q = 1'b0;

    #1
    p = 1'b0;
    q = 1'b1;

    #1
   	p = 1'b1;
    q = 1'b0;

    #1
    p = 1'b1;
    q = 1'b1;

  end
endmodule
```
Test Bench

---
## OR Gate

```verilog
// Code your design here
module or(
  input wire a,
  input wire b,
  output wire c);
  
  assign c = a || b;

endmodule
```
OR Gate

Same testbench

---
## NAND Gate
```verilog
// Code your design here
module nand(
  input wire a,
  input wire b,
  output wire c);
  
  assign c = !(a && b);

endmodule
```

---

## XOR Gate

```verilog
// Code your design here
module xor_gate(output reg c,
                input a,
                input b);
  
  always @ (a or b) begin
    c = (a && ~b) + (~a && b);
  end

endmodule
```
---
## D-Flip Flop

```verilog
module DFlipFlop(D,clk,Q);
input D; 
input clk; 
output Q;
always @(posedge clk) 
begin
 Q <= D; 
end 
endmodule
```
Flip Flop Working at the rising edge.

---

## Important Theory

The _endianness_ (or, informally, "direction") of a vector is whether the the least significant bit has a lower index (little-endian, e.g., [3:0]) or a higher index (big-endian, e.g., [0:3]). In Verilog, once a vector is declared with a particular endianness, it must always be used the same way. e.g., writing `vec[0:3]` when `vec` is declared `wire [3:0] vec;` is illegal. Being consistent with endianness is good practice, as weird bugs occur if vectors of different endianness are assigned or used together.


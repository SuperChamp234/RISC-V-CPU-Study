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
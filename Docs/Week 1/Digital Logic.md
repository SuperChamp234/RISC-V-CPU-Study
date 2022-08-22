# Logic Gates

![](https://i.imgur.com/TomJj3X.png)
Might not be visible in Dark Mode

![](https://i.imgur.com/je5QUQ0.png)

Full Adder circuit

## TL – Verilog Syntax

Parenthesis can be used to group expressions into more complex logic functions.

If a statement is extended across multiple lines, then these lines should have more indentation than the first line.

TL-Verilog is an indentation sensitive! Each Indentation is three spaces wide.

### Signal Name Regulations

-   Must start with `$`
-   Must be composed of tokens delimited by underscores, tokens consisting of lower case alphabets and ending with zero or multiple digits.
-   Must begin with at least 2 or more alphabetic characters.

![](https://i.imgur.com/XdIya9l.png)

### Vectors

A collection of `N` wires can hold $2^N$ possible values. We can also hold the sign of the vector innit.

Operations like `+, -, >, == , <` can be performed on them.

Vectors can be defined by
```verilog
$vector[3:0] = 0001
```
Which is a 4-bit vector.

### Multiplexers

With multiplexers, one can select between two signals with the help of a select line which is used to identify the two signals.
![](https://i.imgur.com/IbTGTK2.png ) ![](https://i.imgur.com/TZC4n5N.png)
Multiplexer and Multiplexer Circuit.
> The MUX depicted in the "Two-way single-bit multiplexer" graphic above can be constructed from basic logic gates, as seen below. We might read this implementation as "assert the output if X1 is asserted and selected (by **S == 1**) OR X2 is asserted and selected (by **S == 0**)".

#### TL-Verilog Syntax

In TLV, we can simply use the ternary operator `? :` as a selector
Syntax 👇
`$out = $sel ? $in1 : $in0;`

Multiple lines of ternary operator can be chained to select for two or more values. These can be inputted as vectors too.

```verilog
$out[7:0] =  
   $sel[3]  
      ? $in3 :  
   $sel[2]  
      ? $in2 :   $sel[1]  
      ? $in1 :  
   //default  
        $in0;
```

![](https://i.imgur.com/V1A67jj.png)
Multiple selector represented as a single selector.

---

### Literals
Refer to third resource in [[Resources]] document.

### Concatenation

Two vectors can be concatenated to form another vector. 
Syntax 👇
`$word[15:0] = {$upper_byte, $lower_byte};`

---
### TL Verilog File Structure

```verilog
\m4_TLV_version 1d --bestsv: tl-x.org
   // This version line specifies:
   //   o that macro preprocessing using M4 is enabled
   //   o the language version in use (1d)
   //   o optionally command-line arguments
   //   o a link to docs.

\SV
   // This region contains SystemVerilog (or Verilog) code.
   // SandPiper passes this code through to the Verilog file without
   // any processing.

   m4_makerchip_module
      // This M4 macro expands to a Verilog module definition with
      // an interface that is required by the Makerchip platform.
      // This module interface provides the communication between
      // Makerchip and your design.
      //
      // It includes global clock and reset input signals
      // via this interface and its output signals “passed”
      // and “failed” can be driven to end the simulation with a
      // “Simulation Passed” or “Simulation FAILED” message in the
      // LOG.
      //
      // To see the expansion of this macro, look in the NAV-TLV
      // pane. This macro also provides a random vector that can
      // be used for stimulus and it provides some Verilator
      // configuration.

\TLV
   // TL-Verilog syntax is enabled in this region to express your
   // logic. In this course, we’ll always declare our logic
   // here within the m4_makerchip_module, but you could also
   // put your TLV logic in a separate module with an interface
   // that is yours to define.

   $reset = *reset;
      // In \TLV context, *reset references the (System)Verilog
      // reset signal. Here we simply connect it to a TL-Verilog
      // $reset pipesignal.

   // YOUR LOGIC HERE

   *passed = ...;
   *failed = ...;
      // Assert either of these to end simulation (before Makerchip
      // cycle limit). 

\SV
   // Back to SystemVerilog context to end the module.
   endmodule```


---
### Flip Flops

The flip flop's value changes with the change in the applied input. Depending on behaviour to different change, flip flops are divided into different categories.  We are only concerned with D-flip-flop for now.

##### D-Flip-Flop

In this type of Flip Flop, the output changes at the clock's edge, and if the input changes at other times, the output is unaffected.

![](https://i.imgur.com/lNpOVA8.png)

![](https://i.imgur.com/O81hJoa.png)
Truth table for flip-flop (D).

As we can see that the D-Flip flop **essentially stores** the value in D signal until it is instructed by the clock to release the formation.
Thus, a D-Flip-Flop can be used as a **Register**.

#### Building a fibonacci series circuit using flip flops

As flip flops basically hold a value, they can be designed to hold the previous value and thus form a series from the values of the last iteration.

A fibonacci series is simply the sum of the last iteration's numbers.
Thus, the previous values of the register can be accessed by the use of `>>n`  where `n` is the nth previous value.
Every circuit also requires a reset signal, which resets the series back to the start. Here if we simply reset the variable's current value to 1, we'd easily have it resetted.

Therefore, the code for fibonacci series is:
```verilog
$num[31:0] = $reset ? 1 : (>>1$num + >>2$num);
```
---

Tags:
#flip-flops #tl-verilog #syntax #multiplexers #vectors #digital-logic 

---

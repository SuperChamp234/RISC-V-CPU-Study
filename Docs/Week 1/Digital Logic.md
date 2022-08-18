# Logic Gates

![](https://i.imgur.com/TomJj3X.png)
Might not be visible in Dark Mode

![](https://i.imgur.com/je5QUQ0.png)

Full Adder circuit

## TL - Verilog Syntax

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

With multiplexors, one can select between two signals with the help of a select line which is used to identify the two signals.
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

Two vectors can be concatnated to form another vector. 
Syntax 👇
`$word[15:0] = {$upper_byte, $lower_byte};`

---

## Lab - Calculator

```verilog
\m4_TLV_version 1d: tl-x.org
\SV

   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================

   // Default Makerchip TL-Verilog Code Template
   
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV
   $reset = *reset;
   $val1[31:0] = 'ha;
   $val2[31:0] = 'ha;
   $opt[1:0] = 2'b00;
   $out[31:0] =
      $opt == 2'b00
         ? $val1+$val2 :
      $opt == 2'b01
         ? $val1-$val2 :
      $opt == 2'b10
         ? $val1*$val2 :
      $opt == 2'b11
         ? $val1/$val2 :
      //default
         -1;
   //...

   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule

```
---
### Lab Calculator Stimulus

```verilog
\m4_TLV_version 1d: tl-x.org
\SV

   // =================================================
   // Welcome!  New to Makerchip? Try the "Learn" menu.
   // =================================================

   // Default Makerchip TL-Verilog Code Template
   
   // Macro providing required top-level module definition, random
   // stimulus support, and Verilator config.
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
	/* verilator lint_on WIDTH */
\TLV
   $val1[31:0] = {26'd0, $val1_rand[5:0]};
   $val2[31:0] = {28'd0, $val2_rand[3:0]};
   $out[31:0] =
      $opt[1:0] == 2'b00
         ? $val1 + $val2 :
      $opt == 2'b01
         ? $val1 - $val2 :
      $opt == 2'b10
         ? $val1 * $val2 :
         $val1 / $val2;
   //...

   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
\SV
   endmodule
```

>Full Lab with calculator module imported 
>http://makerchip.com/sandbox/0YEf3hZw2/0oYhXrp#

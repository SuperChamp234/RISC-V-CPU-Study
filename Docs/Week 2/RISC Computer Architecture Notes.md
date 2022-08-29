# RISC Computer Architecture Notes

## Instructions in RISC-V

- Each Instruction is 32 Bits.
- There are 6 types of instruction formats
	- R - Format
		- These Instructions use 3 register inputs.
		- `add, xor, mul` - Arithmetic or Logical Operations.
	- I - Format
		- These Instructions have intermediates
		- `addi, lw, jalr, slli`
	- S - Format
		- Store Instructions, `sw, sb`.
	- SB - Format
		- Branch Instructions, `beq, bge`
	- U - Format
		- Instructions with upper immediates ,with "upper" meaning the upper 16 bits,
		- `lui, auipc`
	- UJ - Format
		- Jump instructions, `jal`.
![](https://i.imgur.com/FnItkg1.png)
![](https://i.imgur.com/FsJDTAG.png)



## Register File

- There are 31 general purpose registers from x1 to x31. 
	- The register x0 is hardwired to the constant 0.
	- For R64, the registers are 64 Bit Wide, while for RV32 they are 32 bits wide.
	-`XPRLEN` is used to signify the width of x register in bits.

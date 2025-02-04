## Definitions
- [[#Instruction Set]] - collection of instructions that are understood by the CPU, represented by binary
- Operand - the mathematical or computational function (and, or, +, -, /, etc)
- Direct Addressing - when the opcode and the instruction links directly to the operand (in the main memory)
- Indirect Addressing - when the opcode and the instruction links indirectly to the operand (in the main memory), by this we mean it points to a pointer which then points to the correct address of the operand in main memory
- Register Addressing - when the opcode directly holds the address for a register
- Register Indirect Addressing - when the opcode indirect holds the address to a register which is actually a pointer to the address of the register in the main memory
- Displacement Addressing - this is when the address is "displaced" by a fixed number, to fix this you use the register to find the displacement value and add it to the address value which gives you the final address of the operand in main memory
## Notes
### Instruction Set
- We generally convert the binary into something easier to read for people
- There are three main types of instruction sets:
	- data transfers: registers, main memory, stack or I/P
	- data processors: arithmetic, logical
	- control: systems control, transfer of control
- We have spoken about *control statements*, they allow us to break up the sequential steps into loops and if statements (branches)
	(below is a diagram of the above)
	![[Pasted image 20250204160954.png]]

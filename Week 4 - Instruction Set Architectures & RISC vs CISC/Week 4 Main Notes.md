There was some notes made in the [[Week 4 Pre-Session Notes]] that won't be repeated here
## Definitions
- Registers - small *temporary* working space (storage), these tend to have the highest level in the memory hierarchy
- Instruction Prefetch - when you fetch the next instruction during the execution of another instruction
- [[#CISC]] - complex instruction set computer
- [[#RISC]] - reduce instruction set computer
## Notes
- When doing *displacement addressing*, the CPU automatically adds the value into the register instead of repeating the whole cycle twice as this would be too slow
### Pipelining
- Fetch tends to involve accessing main memory (which is too slow)
- Execution of ALU operations do not access main memory
	- this means that we can fetch the next instruction during the execution of the current instruction
	- this is called *instruction prefetching*
	- **NOTE: branching does mess up this process**
- Pipelining can be made up of *five main stages:* (note that note all versions of pipelines are the same but this is the one we are using)
	1. IF: Fetch Instruction
	2. ID: Decode Instruction
	3. RR: Register Read
	4. EX: Execute instruction
	5. WB: Write Back Result
	(below is a table representing clock speed, x == pipeline stages, y == clock cycles)
	![[Pasted image 20250204185211.png]]
	(*this diagram assumes independence which means that no variable is used more than once*)

	(below is a table representing clock speed, x == pipeline stages, y == clock cycles)
	![[Pasted image 20250204185617.png]]
	(*because of a branch, a lot is missing which means that that much must be repeated starting again from I15*)

- Using instruction pipelining there is a formula to help figure out *how much* the clock speed will speed up (see below)
	![[Pasted image 20250204185929.png]]
- In regards to branches whilst pipelining you can:
	1. Prefetch Branch Target
		- the target of the branch is prefetched in addition to the instructions following the branch
		- keep the target until the branch is executed
		- used by IBM till 91
		- kinda wasteful as you will ALWAYS throw one branch away
	2. Loop Buffer
		- you essentially just add a tiny bit of very fast memory to the CPU solely for this purpose
		- this is maintained by the fetch stage of the pipeline
		- check the buffer
		- before fetching from memory
		- good for **small loops**
	3. Branch Prediction
		- you can predict it using ***Opcode:***
			- some instructions are more likely to jump than others
			- this means that you can get up to a 75% success rate
		- you can use a ***taken/not taken switch:***
			- you use previous history to put a switch
			- only really good for loops
			- you start by predicting you will always get taken or not get taken but if the opposite occurs twice then you switch sides (see below for the flow chart)
				![[Pasted image 20250204190929.png]]
	
### RISC vs CISC
#### CISC
- complex machines instructions are harder to exploit so its harder to simplify
- optimisation is difficult
- small programs take up less memory but:
	- memory is now super cheap
	- may not actually occupy less bit but just look smaller in symbolic form (its a cheat)
		- more instructions require op-codes
		- register references use less bits
#### RISC
- the best thing to do is always try to optimise anything that is used often and by multiple users
- large number of register files
- this has a careful design of pipelines

### The Use of a Large Register File
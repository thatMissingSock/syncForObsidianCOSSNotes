I made some notes about the videos in the [[Week 1 Pre-session Notes]]

First couple of weeks will be intro and the rest will be *assembly-like* language.

### In Session Notes
![[Notes_250114_181124_1.png]]

![[Notes_250114_181124_0.png]]
- assembly references the registers directly (unlike other languages)
- only *privileged* OS routines can use PC, IR and PSW (program status word)
	- PSW - holds the generic status of a current program
- *user-visible registers* can be referenced by machine languages
	- available to all programs
	- data and address can be accessed and changed
- annotated *basic instruction cycle* found in [[Week 1 Pre-session Notes]]

##### Characteristics of a (hypothetical) machine
- instructions tend to be a fixed length
- instructions are made up of an opcode (operation type) and an address
- the **size** of the opcode defines how many operations you have 
	- 4 bit opcode means you have 2^4 different types of operations

#### CPU Speeds
- definition - the amount of time the CPU "clicks" per second
	- 1Hz == 1 cycle per second
- instructions vary by speed depending on what they are doing
	- accessing memory tends to be slower than anything else

#### Other Performance Measurements
- MIPS - million instruction per second can be executed
- CPI/IPC - cycles per instruction/instructions per cycle
- the ***above*** are more accurate ways of measuring the CPU performance

#### Computer Modules
![[Notes_250114_184829_0.png]]

#### Bus Interconnection Scheme
- system's bus is usually made up of *3 individual buses (lines)*
- they can be made up of 3 different lines:
	- control lines  - dedicated for synchronising the system together
	- address lines - dedicated for transferring address (for operands/opcode)
	- data lines - dedicated bus to transfer data
- **bus width** determines *how* much data can actually be transmitted
- address granularity - when one address identifies a whole word

#### Caching
- a word is a natural amount of data that the processor can move, change and/or read
	- the size of the word depends on the processor
	- on x86 systems the "standard" word size is 32 bits
	- on x64 systems the "standard" word size is 64 bits
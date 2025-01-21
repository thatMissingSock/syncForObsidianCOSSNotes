**FORENOTE** - I did make some notes based on the videos he suggested we watch, they can be found in [[Week 2 Pre-Session Notes]]

## Definitions
- [[#Operating Systems]] - an extended (or virtual) machine, mainly used to show high level abstracted data whilst providing services via system calls
- [[#System Calls]] - a set of functions that can be used to *indirectly* interact with the hardware (easier to use since its a higher level of abstraction) 
- Accounting (CS context) - a term to describe the act of keeping track of what is being used and how many times it has been accessed/executed
- Kernel - portion of the operating system that is in the main memory usually containing the most used functions, can be called the nucleus 
- [[#Uniprogramming]] - a method of running programs, it has *no* interruptions and processes everything one at a time (FIFO) 
- [[#Multiprogramming]] - a method of running programs, it allows for interruptions and processes multiple things at a time (based on certain factors)
- Time Sharing Systems - systems where there are multiple users accessing the system simultaneously 
- [[#Process]] - a program in execution
- [[#Five State Process Model]] - a visual representation of how a [[#Process]] actually proceeds in regards to execution
- Throughput - the quantity of items (or instructions) running through the OS
- Interrupt Handler - set lines of code that specifically specify to the OS that the code is either finished or an event must occur
- [[#Input Output Techniques]] - these are techniques used by I/O devices to transfer data/execute instructions
## In Session Notes
### Operating Systems 
- By presenting a virtual machine, it is easier to use (due to the level of abstraction)
- It is also a resource manager
	- allows for the controlled allocation of space, time and multiplexing *for programs*
- ***You can still interact with the hardware if needed***
- *This is still the same thing as **ordinary computer software***
	- it's main caveat is that it is designated as a kernel (see [[#Definitions]])
#### Layers and Views
- This is an idea of how to view the OS by:
	- viewing each part of the computer as layers
	- the deeper you go the *less* abstract you go
	- the layers can *"communicate"* with the adjacent layer 
		(below is an image of this representation)
		![[Notes_250121_153201_0.png]]
	- "layers can only communicate to its adjacent layers" - this means that they **will not** communicate with the other layers directly, they may use [[#System Calls]]
#### Services Provided by the OS
- Program execution
- Access to I/O devices
- Controlled access to resources (e.g. files)
- System access
- Error detection and response
- Accounting
### Uniprogramming
- This is inefficient as the whole CPU must wait until the instructions have finished running 
- It also ensures that the instructions have run at the cost of running time
		(below is a diagram of a representation of uniprogramming)
		![[Pasted image 20250121153650.png]]
- Were used a *long* time ago in systems
- There was a good question about this that I answered in [[Week 2 Tutorial Questions]] 
- **FOR QUESTIONS ABOUT THIS WE ASSUME I/O DEVICES ARE INDEPENDANT**
### Multiprogramming 
- The processor can execute more than one program at a time
- The sequence of programs are executed based on their relative priorities (aka scheduler see [[#Definitions]])
- After an interrupt handler completes, the control may not return to the original program that was running
		(below is a representation of multiprogramming)
		![[Pasted image 20250121153756.png]]
- This are most commonly used today
- There was a good question about this that I answered in [[Week 2 Tutorial Questions]]
- **FOR QUESTIONS ABOUT THIS WE ASSUME I/O DEVICES ARE INDEPENDANT**

### Major OS Concepts
#### Process
- Can also be defined as an instance of a program running on a computer
- A unit of activity characterised by:
	- a single sequential thread of execution
	- a current state
	- an associated set of system resources (memory image, open files, locks etc)
- Processes can be split into **three segments:**
	- code segment - an executable program
	- data segment - the associated data needed by the program
	- context segment - *all* the information the system needs to manage the process
		- process entry table (state, priority, accounting)
		- stack
##### Five State Process Model
 (below is a representation of the five state process model)
![[Pasted image 20250121185708.png]]
- Above is the "states" that the process can be:
	- new - the program is chosen to be run based on its priority 
	- ready - when the instruction is in the main memory and has everything it needs to be dispatched
	- running - when the instruction is actively moved from the main memory into the short term memory queue and is executes, there are multiple paths that it can be moved from
		- release - the OS releases the program due to it either breaking completely or finishing completely
		- time out - the OS states that the computation time is finished but the computation has not finished and it is allowing the program to retry
		- event wait - this is when the program is in requirement of a resource that they don't have readily available
	- blocked - when the OS stops everything as it is waiting for an event to occur for the currently running program
	- exit - the resources are released and the program exits
#### Memory Management
- There are many techniques that the OS can utilise to help with memory management:
	- process isolation
	- automatic allocation and management
	- support of [modular programming](https://www.tiny.cloud/blog/modular-programming-principle/)
	- protection and access control
	- long-term storage
#### Scheduling and Resource Management
- The aim of the OS is to be:
	- fair - to give fair and equal access to resources
	- equitable - able to be responsive and discriminate jobs based on priority
	- efficient - to maximise throughput (see [[#Definitions]]), minimise response time and accommodate as many users as possible
### System Calls
- Can also be referred to as *service calls*
- It is the interface between OS and user programs (to undertake privileged operations)
### Input Output Techniques
- There are three main types of techniques:
	- [[#Programmed (I/O Technique)]]
	- [[#Interrupt Driven (I/O Technique)]]
	- [[#Direct Memory Access (I/O Technique)]]
#### Programmed (I/O Technique)
- This technique goes as the following:
	- I/O module performs the action
	- sets the appropriate bits in the I/O status register
	- CPU checks status bits periodically (this is ***inefficient***)
	- **NO** interrupts occur
	- processor checks status until the operation is complete
- **ALL** of the data goes into the CPU *solely* to transfer the data into the main memory (**extremely inefficient**)
#### Interrupt Driven (I/O Technique)
- The main advantages of this is that:
	- it overcomes the CPU waiting 
		- **IT STILL PASSES THROUGH THE CPU**
	- there is **no** repeat checking of the device
	- I/O module interrupts when it is ready
- It does this by doing the following:
	- it transfers the data as normal
	- it will interrupt the normal execution cycle of the processor and runs its own special code of which there are two types:
		- program generated - code made because of an instruction
		- hardware generated - code caused because of a timer, I/O, other errors etc
- If there is an interrupt then:
	- it suspends execution of the program
	- it executes the interrupt-handler routine/interrupt service procedure
	- it *may or may not* return control to the original suspended program
#### Direct Memory Access (I/O Technique)
- The main advantages of this is that:
	- it fully overpasses the CPU which means that:
		- transfer rate is not limited (theoretically)
		- the CPU does not get tied up
- It does this by doing the following:
	- it transfers blocks of data directly to or from the main memory
	- an interrupt is sent when the transfer is complete
- The main time taken for doing this method is the time taken for the interrupt to stop the transfer

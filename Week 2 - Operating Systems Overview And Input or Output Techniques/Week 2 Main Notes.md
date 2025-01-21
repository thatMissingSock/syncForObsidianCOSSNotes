**FORENOTE** - I did make some notes based on the videos he suggested we watch, they can be found in [[Week 2 Main Notes]]

## Definitions
- [[#Operating Systems]] - an extended (or virtual) machine, mainly used to show high level abstracted data whilst providing services via system calls
- [[#System Calls]] - a set of functions that can be used to *indirectly* interact with the hardware (easier to use since its a higher level of abstraction) 
- Accounting (CS context) - a term to describe the act of keeping track of what is being used and how many times it has been accessed/executed
- Kernel - portion of the operating system that is in the main memory usually containing the most used functions, can be called the nucleus 
- [[#Uniprogramming]] - a method of running programs, it has *no* interruptions and processes everything one at a time (FIFO) 
- [[#Multiprogramming]] - a method of running programs, it allows for interruptions and processes multiple things at a time (based on certain factors)
- Time Sharing Systems - systems where there are multiple users accessing the system simultaneously 
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

### System Calls
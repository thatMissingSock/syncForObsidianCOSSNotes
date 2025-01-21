#### What is an operating system?
- It is an extended (or virtual) machine
	- provides a simple abstract view (doesn't show all of the details)
	- it is a resource manager
	- presents the user with services that can be called by the system
![[Notes_250121_153201_0.png]]

#### Resource Management
- You can actually figure out how long it would take for a program to run/execute instructions
- Below is an example of figuring this out
![[Pasted image 20250121153339.png]]

- In regards to ***methods*** of CPU utilisation, there are two main types:
	- Uniprogramming - the methodology where the CPU must wait for I/O instruction to complete before it can proceed
		- (below is a diagram to represent this)
	![[Pasted image 20250121153650.png]]
	- Multiprogramming - the methodology where more than one programming can sit in main memory at one time
		- (below is a diagram to represent this)
		![[Pasted image 20250121153756.png]]
		- a *"scheduler* decides which order these programs should run
		- if one program is *stuck* then **any** other program may run to be more efficient
- (Below is a diagram that shows how they would process the same instructions)
![[Notes_250121_154300_0.png]]
- The left side of the diagram does it in order of FIFO (first in first out)
	- this wastes time and memory (see all the blue space above)
	- this is easier to think about and thus keep track off
- The right side of the diagram does it in order of FIFO ***BUT*** with the caveat of this instruction "if the current program gets stuck (or we are waiting for a response) go onto the next and store the data in memory"

#### Five State Process Model
- (Below is a diagram of what set of orders the computer will follow)
![[Pasted image 20250121154643.png]]
- This infers a few things:
	- whenever we have a new program we admit it to the main memory so it is ready to be ran
	- when it is running it has three possible paths:
		- Release - it has finished the program and exits
		- Event Wait - it is waiting for a response (from a server etc) and thus it goes onto "blocked" disallowing the processor from doing anything else
		- Timeout - there was an issue with the program and thus it tries again
	- *we **must** keep the address of the main data in the RAM in case we need to access it again later* 

#### I/O Devices
![[Pasted image 20250121155554.png]]
- There are ***three main I/O techniques***
	- Programmed I/O - this is when the plugged in I/O has set instructions and sets the appropiate bits in the I/O status register. **THE CPU BLOCKS EVERYTHING ELSE AND IS ESSENTIALLY IDLE DURING THIS**
		![[Pasted image 20250121155803.png]]
	- Instruction Cycle *with* Interrupts - this is when the I/O is still coded and gives instructions but allows for peripherals to "issue an interrupt" (this means that it will do what it needs to address the interrupt)
		![[Pasted image 20250121160101.png]]
	-  DMA (direct memory access) Configurations - this is a technique with transferring data from the I/O to the main memory (and vice versa) *without* passing it through the CPU
		![[Pasted image 20250121160829.png]]
		
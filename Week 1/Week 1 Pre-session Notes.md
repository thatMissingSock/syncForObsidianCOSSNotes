### Computer Architecture Introduction Notes
##### Computer Structure - Top Level
- Central processing unit (CPU) is what does all the data computations 
- Main memory is where the RAM is
	- tends to be fast
	- stores the data for the CPU
- Input/Output system which is what helps the computer communicate with external peripherals
- Systems bus (interconnection) is what allows the internals of the computer to talk with each other

##### CPU internals
- Registers are very small amounts of memory that are very fast (usually 64 bits)
- Arithmetic and logic unit is the part that actually does the computations
- Control unit controls the flow of the execution of programs and synchronises the timings of the other components (thus it has an internal clock)
- Internal CPU interconnection is the *specific* connections between the components of the CPU

#### Computer Components - Registers
![[Notes_250109_184633_0.png]]

#### Basic Instruction Cycle
![[Notes_250109_185041_0.png]]

#### Characteristics of a hypothetical machine
- registers are fixed width so you **want** your instruction format to have a fixed width in the following format

![[Notes_250109_185459_0.png]]

#### Simple Computation Example
![[Pasted image 20250109185624.png]]
1. loads the data from address 940 (into AC)
2. performs addition using data from 941 (and AC)
3. stores the new result into memory address 941 (from AC)
- ***AC IS A REGISTER IN THE CPU***

The following is a visual representation of above:
![[Pasted image 20250109185841.png]]

#### Physical Realisation of Bus Architecture
- there are usually multiple examples of bus architecture and they all differ
- PHYSICALLY they are usually made of wires etc
![[Pasted image 20250109190110.png]]

#### Bus Interconnection Scheme
- system's bus is usually made up of *3 individual buses (lines)*
- they can be made up of 3 different lines:
	- control lines  - dedicated for synchronising the system together
	- address lines - dedicated for transferring address (for operands/opcode)
	- data lines - dedicated bus to transfer data
![[Pasted image 20250109190252.png]]

### Memory Hierarchy and I/O

#### The Memory Hierarchy
- the fastest memory is at the top and the slowest is at the bottom of the triangle
- fastest usually means it's the smallest and most expensive
![[Pasted image 20250109190626.png]]

#### Memory (pyramid)
- SSD's have an access time of 25-100 msec
![[Pasted image 20250109190709.png]]

#### Logic and Memory Performance Gap
- the x axis is megahertz (clock speed)
	- this just means the number of cycles the CPU goes through per second
- the y axis is the year
- the correlation shows an increase in clock speed 
- the average increase in CPU speed is 60% a year
- the average increase in memory capabilities is only 10% a year
![[Pasted image 20250109191013.png]]

#### Cache and Main Memory
- when going into CPU from the main memory we have a cache as the middle man
	- we do this because we assume that we are going to need more than one thing from that area of main memory
- when going from the cache to CPU we ONLY transfer a byte/word per transfer
![[Pasted image 20250109191036.png]]

#### Cache Read Operation
- this explains *how* the cache actually operates
- "moving blocks of data require overhead" but unfortunately the video cuts off and I cannot find any more information as the slides (he provided) seem to ***heavily*** require his input
![[Pasted image 20250109191218.png]]
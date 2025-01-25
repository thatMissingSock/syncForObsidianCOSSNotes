**FORENOTE** - This was just an intro into I/O devices and the multiple techniques into how they can be utilised, I *assume* that there will be more in-depth notes in the [[Week 3 Main Notes]]

## Definitions
- Seek Time - time it takes to position the head at the desired track
- Rotational delay/latency - time it takes for the beginning of the sector to reach the head
- Access time - sum of seek time and rotational delay (time it takes to get into position for it to read and write)
- [[#Disk Scheduling Policies]] - different policies that help keep the mechanical hard drive efficient
- [[#Device Driver]] - a program to allow the OS to interact with a device through a bus
- [[#Device Independent I/O Software]] - a device that is plugged in can be read without installing or changing the code in the OS (should basically be universal)
## Notes
**Forenote** - for the remainder of this session he is *solely* referring to MECHANCIAL hard drives *not* SSDs.
### Disk Scheduling Policies
- The hard drive can follow FIFO (first in, first out)
	- it processes requests sequentially
	- its fair to *all processes*
- The hard drive can follow SSTF (shortest service, seek time first)
	- it selects the request that requires **the least** movement from its current position
	- it will always try to choose the minimum seek time
- The hard drive can follow SCAN
	- the arm moves in *one direction only* satisfying all outstanding requests until it reaches the last track in that direction
- The hard drive can follow C-SCAN
	- the arm is restricted to scanning in one direction only
	- when the last track has been visited then the arm is returned to the opposite end of the disc and the scan starts again
(below is a comparison between all the different types)
![[Pasted image 20250125132916.png]]	

### Device Driver
(below is a representation of how this interaction may occur)
![[Pasted image 20250125133506.png]]
### Device Independent I/O Software
(below is a representation of how this interaction may occur)
![[Pasted image 20250125133925.png]]

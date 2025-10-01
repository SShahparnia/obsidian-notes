# Chapter 1 - Introduction
## Operating System
- Resource Allocator - manages resources
- Control Program - ctrls exec to prevent errors and use
## Computer System Structure
- Hardware
- Operating System
	- Controls and coordinates use of hardware among various applications and users 
- Application Programs
	- Word processors, compilers, web browsers, database systems, video games
- Users
Diagram Description Hierarchy
Hardware/OS/System/application program/ users
![[Pasted image 20250930171613.png]]
### Computer System Organization
## Computer Startup
- Bootstrap Program - loaded at power-up/reboot
	- stored in ROM (read-only memory) or EPROM (erasable progammable ROM)(firmware)
	- Software but it's firm (not erasable)
### Computer System Operation
- I/O & CPU can execute concurrently
- Device controller has local buffer
- CPU moves data from/to main mem to/from local buffers
- I/O is from device to local buffer of controller
- Controller informs CPU finished operation by interrupt
### Common Functions of Interrupts
- TRAP -> software-generated interrupt
- interrupt vector -> contain all addresses of all services routines (table of all interrupt error addresses)
## Storage Hierarchy
- Speed
- Cost
- Volatility
### Storage-Device Hierarchy
- Registers <-> Cache <-> Main memory <-> ssd <-> hdd <-> optical disk <-> magnetic tape
## Systemic Multiprocessing Architecture
CPU0 --- CPU1 --- CPU2
registers <---> cache for each cpu and then --> memory

## OS operations
- Interrupt Driven
	- Software
		- Exceptions or Traps
	- Hardware
- D
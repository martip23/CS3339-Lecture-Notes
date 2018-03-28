# Cache and Memory #
### Memory Wall ###
* Memory has not advanced as fast as CPUs.
* Memory speed has increased linearly, while CPU speed increased exponentially.
* Bandwidth is an issue w/ multi-core CPUs.

#### Dealing w/ memory wall ####
* Building faster memory
	* Limited by technology, current research in HBM
* Fast memory that is small
	* Usually small is **too** small
* Current solution
## Hierarchy of memory ##

* Good to separate Data & Memory
	* Helps prevent structural hazards
* **Registers**
	* L1 Cache (ITLB, DTLB, Instr Cache, Data Cache)
	* L2 Cache
	* Main Memory
	* Secondary Memory (disk)
* **Responsibilities**
	* Registers <-> Cache: Compiler
	* Cache <-> RAM: Compiler, cache controller
	* Main memory <-> disks: OS, TLB, programmer
* Nothing gained without locality
* Temporal locality, if mem location is accessed, chances we'll need it again.
* Spacial locality, address next to mem location are likely to be accessed soon.
* **Cannot do if**
	* No locality
	* Locality within a program that is not exploited
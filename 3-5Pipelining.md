# Pipelining

* Think about a single cycle processor
	* **Limited by slowest instruction**
	* Not ideal.

### Pipelining is natural.
* Think about laundry.
	* Folding clothes, running washer and running dryer at the same time.
	* ```30min(Washer) -> 30min(Dryer) -> 30min(folding clothes)```
		* ```Load of Laundry -> Instruction```
		* ```Landromat -> Processor```
		* ```Washer/Dryer -> Resources(registers, ALU, Mem)```
		* ```30 Minutes -> Clock Cycle Time```
	* **Main Idea: Take task and break into subtasks. Release the resource to whomever needs it next as soon as possible.**
	* Steps must be dependent. If they are independent, then parallelism is a better answer.
		* Can be applied to software level as well
	* How do we break up CPU tasks?
		* ```Instruction Fetch -> Instruction Decode -> Execute -> Memory -> Write back```

### MIPS is ideal for Pipelining
* All Instructions are the same size (32 bits)
* Symmetry across formats (3)
* Memory operations only occur in loads/stores
* Each instruction writes at most one result, and at the end.
* 


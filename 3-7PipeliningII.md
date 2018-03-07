# Pipelining II - Hazards

----------

## Hazards
* Hazard is any situation that can disrupt pipelining.
* Hurts performance in incorrect execution.
* Can usually resolve by stalling


----------

### Structural Hazards
* Two different instructions attempt to use same resources
* not many in MIPS
* easy to handle
* **Solved by separate data/instruction memory (not on registers)**
* **For registers: Read/Write each take half a cycle**
	* Read should go first, **this would help avoid data hazards too**

### Data Hazards
* Instruction to use data before it's ready
	* How to solve? Take an analysis so Processor knows if a variable is dependent or not.
	* Compiler will determine what can be paralleled or not.
* **Solved by:**
	* **Stalling pipeline** (Not ideal)
	* **Forwarding - Using hardware aka bypassing**
		* **EX to EX**
			* Premise: Add knows result at end of cycle 3 (Execute)
			* Premise 2: Next arithmetic doesn't actually need result until right before cycle 3 (execute)
			* Result: Forward instruction back to start of ALU for instruction 2 using state register.
				* Can also be forwarded to next instruction.
				* By the third cycle, should be written to register so forwarding is no longer needed
			* What do we need?
				* MUX
				* Control signal
		* **Mem (stage) to EX**
			* Two stage forwarding

### Control Hazards ###
* Attempt to make decision about control before condition has been evaluated or the new PC target address is calculated.
* Branch and jump instructions and exceptions.

----------

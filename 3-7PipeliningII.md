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
	* **RAW** Read after write
	* **WAR** Write after read
	* **WAW** Write after write
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
		* **Data hazard from Load-Store (Address computation)**
			* Need to STALL
		* **MEM to MEM**

### Control Hazards ###
* Attempt to make decision about control before condition has been evaluated or the new PC target address is calculated.
* Branch and jump instructions and exceptions.
	* **Branch result at end of ALU but needed before Fetch**
* **Handling**
	* Stalling
	* Delay decision(Branch delay)
	* Move branch
	* Guess and hope for the best

#### Types of stalls ####
* **nop** - (no op) bubble inserted between 2 instructions in a pipeline
	* Used for load-use
* **flush** - Reset to previous instruction
	* For an n=100 loop, condition would be false only 1 time.

#### Move branch ####
* Moving branch tgt address calculation to ID
	* Cmopute branch target address
	* Need extra hardware
		* Use the state register to access information earlier
		* MEM/WB to IF/ID forwarding
		* WB to IF/ID
		* 
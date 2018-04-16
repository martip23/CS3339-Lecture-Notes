# SuperScalar and VLIW

## Review

* Dependencies limit the benefit from Super Scalar or VLIW archtiectures.
* More instructions "in-flight". Increased risk of hazards.

### VLIW
* Uses very long words
* Static
* Done in software, (compile time)
* Can look at entire scope of program

### Super scalar
* Dynamic
* Done by HW

## In order vs out-of-order
* In order
	* Processor executes in machine code order
* Out of order
	* Processor has liberty to change in-out of order
* Can have in-order issue and out-of-order execution or out-of-order issue and in-order execution too.
* As the contision are relaxed, there is better performance (but more probability of bugs)

## In-Order issue and In-Order Completion
* Stalls may be necessary to ensure in-order completion

## In-Order issue and Out-Of-Order Completion
* Eliminates some stalls due to requirement to finish in-order 
	* Mult instruction that takes two cycles does not cause stall in next instruction if it is a one cycle instruction.

### OO issue & OO Completion
* Eliminates many 2 stalls.
* Turned out to have 3 write cycles. Our hypothetical machine only allowed two write backs.
	* We would need another stall, but it is a free stall since the next stage originally had only 1 instruction using WB

### OOI-OOC and In-Order commit
* INstructions are buffered in commit unit so they can be committed in Instructin-Fetch order.
* In-order COmmit may cause sacrifice in performance.

## VLIW
* Do everything at compiler level
* You can use *bundles* to tell compiler what to program at once.
	* 2-issue MIPS with 2-instruction bundle
	* Inst are always fetched, decoded and executed in pairs
	* Need (4 read ports, 2 write, seperate memory addr. adder.
* Data dependence (Compilers look for this within instructions)
* A dependence occurs when 2 instructions access the same register, and one is a write.
* If there is a dependence from A to B, then A must execute before B.
### Types of Data Dependance
* RAW (true data dependence)
* WAR (Anti dependence)
* WAW (Output Dependencies)

## Instrution Scheduling.
* Latency, the amount an instruction has to wait to avoid RAW
	* Can be hidden by instruction scheduling


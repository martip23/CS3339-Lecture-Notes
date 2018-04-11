# Parallel Architectures I: Superscalar and VLIW

* Any system w/ more than one processing unit (Higher level than an ALU)

## Intra-Core Parallel Architecutres

* Pipelining
* Tag-comparisons in cache operations
* ALU and branch target operation
* Extra adder for updating CPU
* Register reading
* TLB
* RAID (redundancy and parallel access)
* Compiler techniques

### Multi-Issue
* Fetching multiple instructions, done dynamically in HW
* Superscalar - Out of order
* VLIW - Very long instruction word
* Fetch and ex more than one isn per cycle
	* CPI often < 1
* Generally use IPC (Instructions per cycle)
* Physically added two ALUs
* Register and DM not duplicated
	* Regi and DM s/b consistent
* More potential for Hazards
* Advantage of VLIW
	* More scope
	* Penalty paid at compile-time instead of run-time

## Inter-Core Parallel Architectures

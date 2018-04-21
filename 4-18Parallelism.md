## Loop Unrolling

* Create multiple copies of the instruction in static form
	* Do operation 4 times instead of once and incremenet by for in a i < 100 for loop.
	* Helps scheduling by running load/store and ALU at the same time.
	* Instruction Level Paralellism (ILP)

## Summary
* For more performancew e need both ILP and Machine paralellism.

# Paralellism 2; SMP, Clusters, CMP, GPU

## SMP
* Shared Memory Multiprocessor. Processors have their own Processor & Cache. 
* Processors communicate through shared variables in memory
* Architecture must provide features to co-ordinate data.

# DMS
* Distributed Memory System (Each processor has its own memory)

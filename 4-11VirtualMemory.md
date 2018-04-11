# Virtual Memory

* Good for programs that need more memory than is available on system.
* "Swap space"
* Good because it's safer for sharing.
	* Memory is abstracted out
	* Prevents one program from looking at the data from another program
* Page Table
	* Maps between virtual and physical memory
	* Located on main memory
	* May take two trips to fetch data
		* Look for translation in Memory
		* Looking for data (location in cache)
		* Eliminates usefulness of Cache
	* TLB is solution: A cache for the page table on processor
		* Must have an entry for all pages requested for all processes
		* Hardware page table walker
	* Page faults are orders of magnitude more expensive than L1 misses
	
* If you are writing code that shows a lot of misses, what do you ask?
	* What is the size of the page
	* Type of TLB, Associative etc.
	* Access five different pages repeatedly.
* What happens on a load?
	* 1st: Fetch
	* 2nd: Decode
		* Extract register #
		* Register numbers
		* Address offset
	* 3rd: Memory address is computed
		* Split into memory address and VPN (virtual page number)
	* 4th: VPN mapping is looked up in TLB
	* 5th: If miss,
		* Go to page table
		* If miss,
			* Page fault
			* Fetch page from disk, update page table
			* Update TLB with PPN
			* REtrieve PPN
		* Concatenate with page offset
		* Look up in L1 cache, if miss, L2, Main Memory, retrieve block place into L2, update into L1, send word to processor


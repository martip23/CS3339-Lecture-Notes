# Pipelining III - Branch Prediction #

* **Main idea** - When you come to a branch, guess at the outcome.
	* Only two possible outcomes (Taken/Not Taken)
	* 50% chance of guessing correctly
	* This is a "static scheme" since the same decision is made for every branch.
		* We make hardware that says the branch is always taken.
	* If we are wrong
		* Flush instructions (1-3 cycle penalty, depending on branch logic)
		* Ensure that flushed instructions didn't change machien state.
		* Restart pipeline at branch destination.

----------

### Branch Prediction and Loops ###
#### Static Prediction ####
* PRe-test loops (for, while)
	* Not-taken prediction is better
* Post-test (do-while)
	* Taken prediction is better
* No way to prevent **all** stalls
* We can improve with DYNAMIC PERDICTION


#### Dynamic Prediction ####
* What information can help us predict the outcome of a loop?
	* What happened last time?
	* Use **Branch History Table**

#### Branch History Table ####
* Can use only one bit per branch, so storing 64 could take one byte.
* Is stationed in the IF stage
* A 1 bit predictor will be wrong twice in the worst case.
	* Worst case is the same when initializing to 0 or 1
	* When initializing to 0, when a branch is taken, it will be wrong twice.
	* If the branch is taken 90% of the time, accuracy is 80%.
	* IN an on/off alternate, prediction would be wrong 100% of the time.

* With a 2 bit predictor, accuracy goes up to 90%.
	* Branch must be wrong twice for prediction to be changed.
	* During first 10 executions, prediction accuracy 70%.
	* After this, 90 accuracy.
	* In an on/off alternation, prediction would be right 50% of the time.

### Branch Target Buffer ###
* Gets branch target buffer and caches the address for quick retrieval.
* BTB eliminates the one cycle stall caused by branch taken prediction.
* 
# Cache #

* We store metadata for the cache. 
	* Tag - Used to access data (Helps prevent collisions when loading from Memory into cache.
	* Valid bit - To determine if this info is valid for this program.

### Placing value in Cache ###
* Module-based placement. (Mod 4)
* mem block 0, 4, 8, 12, 16 map to cache block 0.
* mem block 1, 5, 9, 13, 17 map to cache block 1.


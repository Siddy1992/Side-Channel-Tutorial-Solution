# Assignment 3: Experiment on Flush and Reload Attack. 

## Task Overview
Participants are required to complete the missing logic in the **flushCache** and **reloadCache** function to implement Flush & Reload proof of concept. This will show memory address with the secret code used by victim process.
 
## What Needs to be Implemented?
- Write the code for **flushCache** functionto flush the cache.
- Implement the logic to calculate the cache access time for each cache line in **reloadCache** function.
- Print the inferred secret bit alongside the data used by the victim process in the same function.
 
## Hints
- Longer execution time (CPU Cycle) typically corresponds **Cache MISS**.
- Shorter execution time typically corresponds **Cache HIT**.
- You need to empirically determine a **threshold Cache HIT** time by executing cache_timing_experiment code.

## Compilation & Execution
### Compile:
```sh
gcc cache_timing_experiment.c -o cache_timing_experiment
gcc FlushReload.c -o FlushReload
```
### Run:
First execute the cache_timing_experiment code to check cache accessing time of your system.
```sh
./cache_timing_experiment
```
## Expected Output (Not Exact, but you will see a decrease in cache access time)
```sh
Addresses cached for array[3*128] should be:0x5ca106e301c0-0x5ca106e30200
Addresses cached for array[7*128] should be:0x5ca106e303c0-0x5ca106e30400
Access time for array[0*128],with address 0x5ca106e30040: 824 CPU cycles
Access time for array[1*128],with address 0x5ca106e300c0: 506 CPU cycles
Access time for array[2*128],with address 0x5ca106e30140: 528 CPU cycles
Access time for array[3*128],with address 0x5ca106e301c0: 92 CPU cycles
Access time for array[4*128],with address 0x5ca106e30240: 90 CPU cycles
Access time for array[5*128],with address 0x5ca106e302c0: 800 CPU cycles
Access time for array[6*128],with address 0x5ca106e30340: 512 CPU cycles
Access time for array[7*128],with address 0x5ca106e303c0: 90 CPU cycles
Access time for array[8*128],with address 0x5ca106e30440: 88 CPU cycles
Access time for array[9*128],with address 0x5ca106e304c0: 90 CPU cycles
```
**Note:** Choose any one the minimum cache hit time and set it as **CACHE_HIT_THRESHOLD** in FlushReload code. Next compile and execute the FlushReload code to find the secret code of the victim.
```sh
./FlushReload
```
## Expected Output
```sh
The secret is:23, array[23*4096+64]
```

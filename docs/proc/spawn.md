

 spawn proc
------------




**See also:** 


[background setting (proc)](#/proc/set/background) 

[sleep proc](#/proc/sleep) 




**See also:** 

**See also:**

[background setting (proc)](#/proc/set/background) 

[sleep proc](#/proc/sleep) 


[background setting (proc)](#/proc/set/background)

[sleep proc](#/proc/sleep) 

[sleep proc](#/proc/sleep)


**Format:** 


 spawn(Delay=0) Statement
 


**Format:** 

**Format:**

 spawn(Delay=0) Statement



**Args:** 


 Delay: The amount of time (in 1/10 seconds) before Statement is executed.
 


**Args:** 

**Args:**

 Delay: The amount of time (in 1/10 seconds) before Statement is executed.


 Run Statement after a delay. Statement may be a single statement or a code
block enclosed in (optional) braces and indented. If delay is negative, the
spawned code is executed before continuing in the main code. If it is zero,
the spawned code is scheduled to happen right after other existing events that
are immediately pending.



### 
 Example:



 spawn(30) storm()
usr << "Storm clouds are brewing!"


 This will display
 `"Storm clouds are brewing!"` 
 and then call the
storm() proc after 3 seconds.



`"Storm clouds are brewing!"`


 A spawned statement or block is a copy of the current proc. The current proc
keeps running and the copy waits its turn.
 




 A spawned statement or block is a copy of the current proc. The current proc
keeps running and the copy waits its turn.




 The important feature of spawn() is that the caller does not have to wait
around for the spawned code to finish.




 Any vars you have defined in the proc itself, including arguments, will be
copied between the spawned code and the code that runs right away. This means
that if one part modifies one of those vars, the other part will not see that
change. Changes made to objects, lists, datums, etc. however will be visible
to both code blocks.




[Pointers](#/operator/&/pointer) 
 to any vars that belong to the
proc will stay with the original proc, not the spawned block.



[Pointers](#/operator/&/pointer)


---



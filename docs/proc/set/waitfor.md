

 waitfor setting (proc)
------------------------




**See also:** 


[sleep proc](#/proc/sleep) 

[spawn proc](#/proc/spawn) 

[. var (proc)](#/proc/var/%2e) 





**See also:** 

**See also:**

[sleep proc](#/proc/sleep) 

[spawn proc](#/proc/spawn) 

[. var (proc)](#/proc/var/%2e) 



[sleep proc](#/proc/sleep)

[spawn proc](#/proc/spawn) 

[. var (proc)](#/proc/var/%2e) 


[spawn proc](#/proc/spawn)

[. var (proc)](#/proc/var/%2e) 

[. var (proc)](#/proc/var/%2e)

 By default, procs that sleep usually expect their callers to wait for them
to finish, so the callers must sleep as well. Using
 
 set waitfor=0
 
 will disable that behavior, causing any sleep to return control to the caller
immediately.




 set waitfor=0

### 
 Example



 mob/proc/LongLoop()
 set waitfor = 0
 while(1)
 UpdateAI()
 // proc will return to caller here
 sleep(1)


 This setting will also dictate what happens if a callee sleeps. Consider an
example where proc A calls proc B which calls proc C, and proc B has
 
 waitfor
 
 set to 0. When proc C sleeps, proc B will also sleep, but
proc A will continue running as if proc B returned early. The
 
 .
 
 var
currently in proc B will be used as its return value to A. When proc C wakes
up and finishes, it will wake up proc B, but now B's return value will be
ignored since A is no longer waiting for it.




 waitfor


 .


 In older versions, the
 [New
 
 proc](#/datum/proc/New) 
 always had
 
 waitfor
 
 set to 0 by default, but this was later changed.
Now 1 is always the default, so setting
 
 waitfor
 
 to 1 will result in a
warning that it is no longer necessary.



[New
 
 proc](#/datum/proc/New)

 New


 waitfor


 waitfor



---



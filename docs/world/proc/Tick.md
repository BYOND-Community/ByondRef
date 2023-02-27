

 Tick proc (world)
-------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_usage var (world)](#/world/var/tick_usage) 





**See also:** 

**See also:**

[cpu var (world)](#/world/var/cpu) 

[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_usage var (world)](#/world/var/tick_usage) 



[cpu var (world)](#/world/var/cpu)

[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_usage var (world)](#/world/var/tick_usage) 


[map\_cpu var (world)](#/world/var/map_cpu)

[tick\_usage var (world)](#/world/var/tick_usage) 

[tick\_usage var (world)](#/world/var/tick_usage)


**Format:** 


 Tick()
 


**Format:** 

**Format:**

 Tick()



**When:** 


 Called during the server tick, after sleeping procs and queued commands,
just before map information is sent to the clients.
 


**When:** 

**When:**

 Called during the server tick, after sleeping procs and queued commands,
just before map information is sent to the clients.



**Default action:** 


 None.
 


**Default action:** 

**Default action:**

 None.


 This proc allows you to do any updates just before map info is sent out.
One possible use for this is to run a movement loop, or sync up any user
interface input that might have arrived and deal with it all at once.



### 
 Example:



 world/Tick()
 for(var/client/C)
 if(C.mob?.move\_dir)
 try
 step(C.mob, move\_dir)
 catch
 // empty catch, just so a failed step won't break the loop


 Note: The tick will not wait if this proc sleeps. It effectively has
 [set waitfor=0](#/proc/set/waitfor) 
 already built in.
It's a good idea not to sleep in this proc or any of its callees at all,
since it will keep getting called every tick.



[set waitfor=0](#/proc/set/waitfor)


---



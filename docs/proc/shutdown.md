

 shutdown proc
---------------




**See also:** 


[Export proc (world)](#/world/proc/Export) 

[startup proc](#/proc/startup) 




**See also:** 

**See also:**

[Export proc (world)](#/world/proc/Export) 

[startup proc](#/proc/startup) 


[Export proc (world)](#/world/proc/Export)

[startup proc](#/proc/startup) 

[startup proc](#/proc/startup)


**Format:** 


 shutdown(Addr,Natural=0)
 


**Format:** 

**Format:**

 shutdown(Addr,Natural=0)



**Args:** 


 Addr: This is the address of the child world returned by startup().
 
 Natural: Specifies whether to wait for the child world to die
 naturally, or whether it should be killed with the "Del" world topic.
 The default value of 0 kills the child, and a value of 1 waits for the
 child to exit of its own accord.
 



**Args:** 

**Args:**

 Addr: This is the address of the child world returned by startup().
 
 Natural: Specifies whether to wait for the child world to die
 naturally, or whether it should be killed with the "Del" world topic.
 The default value of 0 kills the child, and a value of 1 waits for the
 child to exit of its own accord.
 


 Natural: Specifies whether to wait for the child world to die
 naturally, or whether it should be killed with the "Del" world topic.
 The default value of 0 kills the child, and a value of 1 waits for the
 child to exit of its own accord.


 If no address is specified, the current world is shut down.





---



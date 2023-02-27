

 Del proc (world)
------------------




**See also:** 


[Del proc (datum)](#/datum/proc/Del) 

[shutdown proc](#/proc/shutdown) 




**See also:** 

**See also:**

[Del proc (datum)](#/datum/proc/Del) 

[shutdown proc](#/proc/shutdown) 


[Del proc (datum)](#/datum/proc/Del)

[shutdown proc](#/proc/shutdown) 

[shutdown proc](#/proc/shutdown)


**Format:** 


 Del()
 


**Format:** 

**Format:**

 Del()



**When:** 


 Called when the world is shutdown.
 


**When:** 

**When:**

 Called when the world is shutdown.



**Default action:** 


 Shutdown the world.
 


**Default action:** 

**Default action:**

 Shutdown the world.


 When the world is destroyed, only the Del() proc of the
 `world` 
 object is called automatically. If you want to delete any other objects, you
must do so from within
 `world/Del()` 
 . Once this procedure returns,
any other procedures which may still be executing are immediately aborted and
all objects are silently destroyed.



`world`
`world/Del()`

 To prevent accidental hangs during
 `world/Del()` 
 from preventing
shutdown, a timeout is applied to any sleeping operations such as
 `sleep` 
 ,
 `world.Export()` 
 , and so on. If the total time
slept exceeds the timeout,
 `world/Del()` 
 is aborted. Currently,
this timeout is set at 30 seconds.



`world/Del()`
`sleep`
`world.Export()`
`world/Del()`


---



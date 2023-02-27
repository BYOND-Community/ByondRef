

 Stat proc (atom)
------------------




**See also:** 


[Stat proc (client)](#/client/proc/Stat) 

[stat proc](#/proc/stat) 

[Info control (skin)](#/{skin}/control/info) 





**See also:** 

**See also:**

[Stat proc (client)](#/client/proc/Stat) 

[stat proc](#/proc/stat) 

[Info control (skin)](#/{skin}/control/info) 



[Stat proc (client)](#/client/proc/Stat)

[stat proc](#/proc/stat) 

[Info control (skin)](#/{skin}/control/info) 


[stat proc](#/proc/stat)

[Info control (skin)](#/{skin}/control/info) 

[Info control (skin)](#/{skin}/control/info)


**Format:** 


 Stat()
 


**Format:** 

**Format:**

 Stat()



**When:** 


 Called periodically by the client to update the stat window.
 


**When:** 

**When:**

 Called periodically by the client to update the stat window.



**Default action:** 


 none.
 


**Default action:** 

**Default action:**

 none.


 The following code could be used to display a player's current status.



### 
 Example:



 mob/var
 health = 100
mob/Stat()
 stat("health",health)
 statpanel("Inventory",contents)



---



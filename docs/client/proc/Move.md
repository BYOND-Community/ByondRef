

 Move proc (client)
--------------------




**See also:** 


[East proc (client)](#/client/proc/East) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[North proc (client)](#/client/proc/North) 

[Northeast proc (client)](#/client/proc/Northeast) 

[Northwest proc (client)](#/client/proc/Northwest) 

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 











**See also:** 

**See also:**

[East proc (client)](#/client/proc/East) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[North proc (client)](#/client/proc/North) 

[Northeast proc (client)](#/client/proc/Northeast) 

[Northwest proc (client)](#/client/proc/Northwest) 

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 









[East proc (client)](#/client/proc/East)

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[North proc (client)](#/client/proc/North) 

[Northeast proc (client)](#/client/proc/Northeast) 

[Northwest proc (client)](#/client/proc/Northwest) 

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 








[Move proc (movable atom)](#/atom/movable/proc/Move)

[North proc (client)](#/client/proc/North) 

[Northeast proc (client)](#/client/proc/Northeast) 

[Northwest proc (client)](#/client/proc/Northwest) 

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 







[North proc (client)](#/client/proc/North)

[Northeast proc (client)](#/client/proc/Northeast) 

[Northwest proc (client)](#/client/proc/Northwest) 

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 






[Northeast proc (client)](#/client/proc/Northeast)

[Northwest proc (client)](#/client/proc/Northwest) 

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 





[Northwest proc (client)](#/client/proc/Northwest)

[South proc (client)](#/client/proc/South) 

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 




[South proc (client)](#/client/proc/South)

[Southeast proc (client)](#/client/proc/Southeast) 

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 



[Southeast proc (client)](#/client/proc/Southeast)

[Southwest proc (client)](#/client/proc/Southwest) 

[West proc (client)](#/client/proc/West) 


[Southwest proc (client)](#/client/proc/Southwest)

[West proc (client)](#/client/proc/West) 

[West proc (client)](#/client/proc/West)


**Format:** 


 Move(loc,dir)
 


**Format:** 

**Format:**

 Move(loc,dir)



**Returns:** 


 1 on success; 0 on failure
 


**Returns:** 

**Returns:**

 1 on success; 0 on failure



**When:** 


 Called by the direction procs.
 


**When:** 

**When:**

 Called by the direction procs.



**Default action:** 


 Calls src.mob.Move(). Also cancels any automated movement by
 calling walk(usr,0).
 


**Default action:** 

**Default action:**

 Calls src.mob.Move(). Also cancels any automated movement by
 calling walk(usr,0).



---





 Exit proc (atom)
------------------




**See also:** 


[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 











**See also:** 

**See also:**

[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 









[Enter proc (atom)](#/atom/proc/Enter)

[Entered proc (atom)](#/atom/proc/Entered) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 








[Entered proc (atom)](#/atom/proc/Entered)

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 







[Exited proc (atom)](#/atom/proc/Exited)

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 






[Cross proc (atom)](#/atom/proc/Cross)

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 





[Crossed proc (atom)](#/atom/proc/Crossed)

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 




[Uncross proc (atom)](#/atom/proc/Uncross)

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 



[Uncrossed proc (atom)](#/atom/proc/Uncrossed)

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 


[Move proc (movable atom)](#/atom/movable/proc/Move)

[movement\_mode var (world)](#/world/var/movement_mode) 

[movement\_mode var (world)](#/world/var/movement_mode)


**Format:** 


 Exit(atom/movable/O, atom/newloc)
 


**Format:** 

**Format:**

 Exit(atom/movable/O, atom/newloc)



**Returns:** 


 1 to permit; 0 to deny.
 


**Returns:** 

**Returns:**

 1 to permit; 0 to deny.



**When:** 


 Called when an object attempts to exit the contents list.
 


**When:** 

**When:**

 Called when an object attempts to exit the contents list.



**Args:** 


 O: the object attempting to exit.
 

 newloc
 
 : the object's new location.
 



**Args:** 

**Args:**

 O: the object attempting to exit.
 

 newloc
 
 : the object's new location.
 



 newloc
 
 : the object's new location.


 newloc



**Default action:** 


 Turfs will call Uncross() and return that value (1 by default). All others allow the object to exit (returning 1).
 


**Default action:** 

**Default action:**

 Turfs will call Uncross() and return that value (1 by default). All others allow the object to exit (returning 1).


 By default, every atom returns 1 to allow exit, except for turfs which
call Uncross() to handle it for them.




 The following behavior only applies to
 [LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode) 
 . In all
other movement modes, the turf's contents are not taken into account. Only the
result of turf.Uncross() matters.



[LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode)

 In the default Exit handler for turfs, Uncross() is called for the turf
itself and then Uncross() will also be called for any atoms in turf.contents
that cover the entire tile. If any Uncross() call fails, Exit() fails too and
will return 0. In games using pixel movement, Uncross() is usually called
separately, but this allows projects using tile-based movement instead to
benefit from Cross() and Uncross().





---





 Enter proc (atom)
-------------------




**See also:** 


[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 












**See also:** 

**See also:**

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 










[Entered proc (atom)](#/atom/proc/Entered)

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 









[Exit proc (atom)](#/atom/proc/Exit)

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 








[Exited proc (atom)](#/atom/proc/Exited)

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 







[Cross proc (atom)](#/atom/proc/Cross)

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 






[Crossed proc (atom)](#/atom/proc/Crossed)

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 





[Uncross proc (atom)](#/atom/proc/Uncross)

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 




[Uncrossed proc (atom)](#/atom/proc/Uncrossed)

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 



[Move proc (movable atom)](#/atom/movable/proc/Move)

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 


[movement\_mode var (world)](#/world/var/movement_mode)

[Pixel movement](#/{notes}/pixel-movement) 

[Pixel movement](#/{notes}/pixel-movement)


**Format:** 


 Enter(atom/movable/O, atom/oldloc)
 


**Format:** 

**Format:**

 Enter(atom/movable/O, atom/oldloc)



**Returns:** 


 1 to permit; 0 to deny.
 


**Returns:** 

**Returns:**

 1 to permit; 0 to deny.



**When:** 


 Called when an object attempts to enter the contents list.
 


**When:** 

**When:**

 Called when an object attempts to enter the contents list.



**Args:** 


 O: the object attempting to enter.
 
 oldloc: the old (current) loc of the object attempting to enter.
 



**Args:** 

**Args:**

 O: the object attempting to enter.
 
 oldloc: the old (current) loc of the object attempting to enter.
 


 oldloc: the old (current) loc of the object attempting to enter.



**Default action:** 


 Explained below.
 


**Default action:** 

**Default action:**

 Explained below.


 Areas, objs, and mobs will always permit anything to enter by default.




 The following behavior only applies to
 [LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode) 
 . In all
other movement modes, the turf's contents are not taken into account. Only the
result of turf.Cross() matters.



[LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode)

 Turfs will return 1 (permit) or 0 (deny) based on density. In simple
terms, if the atom that is entering is dense, then the turf will deny entry
if the turf itself or its contents (any that take up the full tile) are
dense.




 What actually happens in turf.Enter() is more detailed: Cross() is called
for the turf, and if it succeeds (movement is permitted), then Cross() is
called for any atoms in turf.contents that cover the entire tile. If any
Cross() call fails, Enter() fails too and will return 0.




 If a mob is standing on a turf but its bounding box does not cover the
whole tile, it is ignored by Enter(). Instead, its Cross() proc is called if
there is a danger of the object overlapping it.





---



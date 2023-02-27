

 Cross proc (atom)
-------------------




**See also:** 


[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 













**See also:** 

**See also:**

[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 











[Enter proc (atom)](#/atom/proc/Enter)

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 










[Entered proc (atom)](#/atom/proc/Entered)

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 









[Exit proc (atom)](#/atom/proc/Exit)

[Exited proc (atom)](#/atom/proc/Exited) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 








[Exited proc (atom)](#/atom/proc/Exited)

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 







[Crossed proc (atom)](#/atom/proc/Crossed)

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 






[Uncross proc (atom)](#/atom/proc/Uncross)

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 





[Uncrossed proc (atom)](#/atom/proc/Uncrossed)

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 




[Move proc (movable atom)](#/atom/movable/proc/Move)

[group var (mob)](#/mob/var/group) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 



[group var (mob)](#/mob/var/group)

[movement\_mode var (world)](#/world/var/movement_mode) 

[Pixel movement](#/{notes}/pixel-movement) 


[movement\_mode var (world)](#/world/var/movement_mode)

[Pixel movement](#/{notes}/pixel-movement) 

[Pixel movement](#/{notes}/pixel-movement)


**Format:** 


 Cross(atom/movable/O)
 


**Format:** 

**Format:**

 Cross(atom/movable/O)



**Returns:** 


 1 to permit; 0 to deny.
 


**Returns:** 

**Returns:**

 1 to permit; 0 to deny.



**When:** 


 Called when another object attempts to overlap this one.
 


**When:** 

**When:**

 Called when another object attempts to overlap this one.



**Args:** 


 O: the object attempting to overlap.
 


**Args:** 

**Args:**

 O: the object attempting to overlap.



**Default action:** 


 Allow overlap unless both atoms are dense. If both atoms are mobs, the
behavior depends partly on whether they are in the same group.
 


**Default action:** 

**Default action:**

 Allow overlap unless both atoms are dense. If both atoms are mobs, the
behavior depends partly on whether they are in the same group.


 The following behavior only applies to
 [LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode) 
 . In
other movement modes, src.Cross(O) returns 0 by default if src and O are both
mobs in the same group.



[LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode)

 If src completely covers the turf it is standing on, Cross() is called as
part of turf.Enter(). This is to preserve the behavior of older games, which
expect turf.Enter() to care about its contents.




 If src and O are both mobs, and O is in src's group, overlap is allowed
 *unless* 
 neither of them use pixel movement. Older games that do not use
pixel movement expect that Bump() will be called, and by default Bump() will
swap the mobs' positions. Swapping obviously only works in situations where a
mob takes up a whole tile and only moves by tiles; for all other situations,
allowing an overlap makes more sense.



*unless*


---



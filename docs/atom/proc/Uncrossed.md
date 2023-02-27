

 Uncrossed proc (atom)
-----------------------




**See also:** 


[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 












**See also:** 

**See also:**

[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 










[Enter proc (atom)](#/atom/proc/Enter)

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 









[Entered proc (atom)](#/atom/proc/Entered)

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 








[Exit proc (atom)](#/atom/proc/Exit)

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 







[Exited proc (atom)](#/atom/proc/Exited)

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 






[Cross proc (atom)](#/atom/proc/Cross)

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 





[Crossed proc (atom)](#/atom/proc/Crossed)

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 




[Uncross proc (atom)](#/atom/proc/Uncross)

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 



[Move proc (movable atom)](#/atom/movable/proc/Move)

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 


[group var (mob)](#/mob/var/group)

[Pixel movement](#/{notes}/pixel-movement) 

[Pixel movement](#/{notes}/pixel-movement)


**Format:** 


 Uncrossed(atom/movable/O)
 


**Format:** 

**Format:**

 Uncrossed(atom/movable/O)



**When:** 


 Called when an object has stopped overlapping this one through a call to
Move(). Directly setting the object's loc or step\_x/y vars does not result
in a call to Uncrossed() or any other movement side-effects. The same goes
for deletion of an object.
 


**When:** 

**When:**

 Called when an object has stopped overlapping this one through a call to
Move(). Directly setting the object's loc or step\_x/y vars does not result
in a call to Uncrossed() or any other movement side-effects. The same goes
for deletion of an object.



**Args:** 


 O: the object that moved and is no longer overlapping.
 


**Args:** 

**Args:**

 O: the object that moved and is no longer overlapping.



**Default action:** 


 none
 


**Default action:** 

**Default action:**

 none

### 
 Example:



 obj/pressure\_plate
 Uncrossed(O)
 // if no other mobs are standing on it...
 if(!(locate(/mob) in bounds()))
 // do something
 Release()



---



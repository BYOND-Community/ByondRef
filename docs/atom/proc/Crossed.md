

 Crossed proc (atom)
---------------------




**See also:** 


[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

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

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 










[Enter proc (atom)](#/atom/proc/Enter)

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 









[Entered proc (atom)](#/atom/proc/Entered)

[Exit proc (atom)](#/atom/proc/Exit) 

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 








[Exit proc (atom)](#/atom/proc/Exit)

[Exited proc (atom)](#/atom/proc/Exited) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 







[Exited proc (atom)](#/atom/proc/Exited)

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 






[Cross proc (atom)](#/atom/proc/Cross)

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 





[Uncross proc (atom)](#/atom/proc/Uncross)

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[group var (mob)](#/mob/var/group) 

[Pixel movement](#/{notes}/pixel-movement) 




[Uncrossed proc (atom)](#/atom/proc/Uncrossed)

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


 Crossed(atom/movable/O)
 


**Format:** 

**Format:**

 Crossed(atom/movable/O)



**When:** 


 Called when an object has overlapped this one through Move(). Directly
setting the object's loc or step\_x/y vars does not result in a call to
Crossed() or any other movement side-effects. The same goes for creation
or deletion of an object at a location.
 


**When:** 

**When:**

 Called when an object has overlapped this one through Move(). Directly
setting the object's loc or step\_x/y vars does not result in a call to
Crossed() or any other movement side-effects. The same goes for creation
or deletion of an object at a location.



**Args:** 


 O: the object that moved and is now overlapping.
 


**Args:** 

**Args:**

 O: the object that moved and is now overlapping.



**Default action:** 


 none
 


**Default action:** 

**Default action:**

 none

### 
 Example:



 obj/landmine
 Crossed(O)
 O << "You stepped on a land mine!"
 Explode()



---



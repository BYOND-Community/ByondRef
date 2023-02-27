

 Exited proc (atom)
--------------------




**See also:** 


[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 










**See also:** 

**See also:**

[Enter proc (atom)](#/atom/proc/Enter) 

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 








[Enter proc (atom)](#/atom/proc/Enter)

[Entered proc (atom)](#/atom/proc/Entered) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 







[Entered proc (atom)](#/atom/proc/Entered)

[Exit proc (atom)](#/atom/proc/Exit) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 






[Exit proc (atom)](#/atom/proc/Exit)

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 





[Cross proc (atom)](#/atom/proc/Cross)

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 




[Crossed proc (atom)](#/atom/proc/Crossed)

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 



[Uncross proc (atom)](#/atom/proc/Uncross)

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[Move proc (movable atom)](#/atom/movable/proc/Move) 


[Uncrossed proc (atom)](#/atom/proc/Uncrossed)

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[Move proc (movable atom)](#/atom/movable/proc/Move)


**Format:** 


 Exited(atom/movable/Obj, atom/newloc)
 


**Format:** 

**Format:**

 Exited(atom/movable/Obj, atom/newloc)



**When:** 


 Called when an object has exited from the contents list through a call to
Move(). Directly setting the object's loc or step\_x/y vars does not result
in a call to Exited() or any other movement side-effects. The same goes for
deletion of an object.
 


**When:** 

**When:**

 Called when an object has exited from the contents list through a call to
Move(). Directly setting the object's loc or step\_x/y vars does not result
in a call to Exited() or any other movement side-effects. The same goes for
deletion of an object.



**Args:** 


 Obj: the object that exited (a mob or obj).
 

 newloc
 
 : the object's new location.
 



**Args:** 

**Args:**

 Obj: the object that exited (a mob or obj).
 

 newloc
 
 : the object's new location.
 



 newloc
 
 : the object's new location.


 newloc



**Default action:** 


 None for most atoms, but turfs will call Uncrossed().
 


**Default action:** 

**Default action:**

 None for most atoms, but turfs will call Uncrossed().



---



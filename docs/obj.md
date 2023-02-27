

 obj
-----




**See also:** 


[atom](#/atom) 

[movable atoms](#/atom/movable) 

[procs (obj)](#/obj/proc) 

[vars (obj)](#/obj/var) 






**See also:** 

**See also:**

[atom](#/atom) 

[movable atoms](#/atom/movable) 

[procs (obj)](#/obj/proc) 

[vars (obj)](#/obj/var) 




[atom](#/atom)

[movable atoms](#/atom/movable) 

[procs (obj)](#/obj/proc) 

[vars (obj)](#/obj/var) 



[movable atoms](#/atom/movable)

[procs (obj)](#/obj/proc) 

[vars (obj)](#/obj/var) 


[procs (obj)](#/obj/proc)

[vars (obj)](#/obj/var) 

[vars (obj)](#/obj/var)

 There are two types of movable atoms: objs and mobs. The difference between
them is that a mob can be attached to a human player, and is also typically
used for NPCs and creatures. The obj type is a little bit simpler and is
typically used for objects in the environment, items in inventory, etc.




 Objects are derived from
 
 /obj
 
 , which derives from
 
 /atom/movable
 
 .




 /obj


 /atom/movable


 The following example defines the obj type
 
 /obj/scooper
 
 .




 /obj/scooper

### 
 Example:



 obj
 scooper
 desc = "Super pooper scooper."



---



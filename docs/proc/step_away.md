

 step\_away proc
-----------------




**See also:** 


[get\_step\_away proc](#/proc/get_step_away) 

[walk\_away proc](#/proc/walk_away) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 





**See also:** 

**See also:**

[get\_step\_away proc](#/proc/get_step_away) 

[walk\_away proc](#/proc/walk_away) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 



[get\_step\_away proc](#/proc/get_step_away)

[walk\_away proc](#/proc/walk_away) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 


[walk\_away proc](#/proc/walk_away)

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_size var (movable atom)](#/atom/movable/var/step_size)


**Format:** 


 step\_away(Ref,Trg,Max=5,Speed=0)
 


**Format:** 

**Format:**

 step\_away(Ref,Trg,Max=5,Speed=0)



**Returns:** 


 1 on success; 0 otherwise.
 


**Returns:** 

**Returns:**

 1 on success; 0 otherwise.



**Args:** 


 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Max: The maximum distance between Ref and Targ before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 





**Args:** 

**Args:**

 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Max: The maximum distance between Ref and Targ before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 




 Trg: An object on the map.
 
 Max: The maximum distance between Ref and Targ before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 



 Max: The maximum distance between Ref and Targ before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 


 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.


 Move Ref on a path away from location Trg, taking obstacles into
account. If Ref is farther than Max steps from Trg, no action will be taken.





---



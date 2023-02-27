

 step\_to proc
---------------




**See also:** 


[get\_step\_to proc](#/proc/get_step_to) 

[get\_steps\_to proc](#/proc/get_steps_to) 

[walk\_to proc](#/proc/walk_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 






**See also:** 

**See also:**

[get\_step\_to proc](#/proc/get_step_to) 

[get\_steps\_to proc](#/proc/get_steps_to) 

[walk\_to proc](#/proc/walk_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 




[get\_step\_to proc](#/proc/get_step_to)

[get\_steps\_to proc](#/proc/get_steps_to) 

[walk\_to proc](#/proc/walk_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 



[get\_steps\_to proc](#/proc/get_steps_to)

[walk\_to proc](#/proc/walk_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 


[walk\_to proc](#/proc/walk_to)

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_size var (movable atom)](#/atom/movable/var/step_size)


**Format:** 


 step\_to(Ref,Trg,Min=0,Speed=0)
 


**Format:** 

**Format:**

 step\_to(Ref,Trg,Min=0,Speed=0)



**Returns:** 


 1 on success; 0 otherwise.
 


**Returns:** 

**Returns:**

 1 on success; 0 otherwise.



**Args:** 


 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 





**Args:** 

**Args:**

 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 




 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 



 Min: The minimum distance between Ref and Trg before movement halts.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 


 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.


 Move Ref on a path to the location Trg, taking obstacles into account. If
Ref is within Min steps of Trg, no action will be taken. This is also the
case if the target is too far away (more than twice world.view steps).





---



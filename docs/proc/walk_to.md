

 walk\_to proc
---------------




**See also:** 


[get\_step\_to proc](#/proc/get_step_to) 

[step\_to proc](#/proc/step_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 





**See also:** 

**See also:**

[get\_step\_to proc](#/proc/get_step_to) 

[step\_to proc](#/proc/step_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 



[get\_step\_to proc](#/proc/get_step_to)

[step\_to proc](#/proc/step_to) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 


[step\_to proc](#/proc/step_to)

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_size var (movable atom)](#/atom/movable/var/step_size)


**Format:** 


 walk\_to(Ref,Trg,Min=0,Lag=0,Speed=0)
 


**Format:** 

**Format:**

 walk\_to(Ref,Trg,Min=0,Lag=0,Speed=0)



**Args:** 


 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 






**Args:** 

**Args:**

 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 





 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 




 Min: The minimum distance between Ref and Trg before movement halts.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 



 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 


 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.


 Move Ref on a path to Trg continuously, taking obstacles into account.
Each step will be preceded by Lag time of inactivity. If Ref is within Min
steps of Trg, no action will be taken. This is also true if the target is
too far away (more than twice world.view steps).




 A call to a walking function aborts any previous walking function called
on Ref. To halt walking, call walk(Ref,0).




 This function returns immediately, but continues to process in the
background.





---



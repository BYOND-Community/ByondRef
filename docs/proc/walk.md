

 walk proc
-----------




**See also:** 


[get\_step proc](#/proc/get_step) 

[step proc](#/proc/step) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 





**See also:** 

**See also:**

[get\_step proc](#/proc/get_step) 

[step proc](#/proc/step) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 



[get\_step proc](#/proc/get_step)

[step proc](#/proc/step) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 


[step proc](#/proc/step)

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_size var (movable atom)](#/atom/movable/var/step_size)


**Format:** 


 walk(Ref,Dir,Lag=0,Speed=0)
 


**Format:** 

**Format:**

 walk(Ref,Dir,Lag=0,Speed=0)



**Args:** 


 Ref: A mob or obj.
 
 Dir: One of NORTH, SOUTH, EAST, WEST, NORTHEAST, NORTHWEST, SOUTHEAST,
 SOUTHWEST, or 0 to halt.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 





**Args:** 

**Args:**

 Ref: A mob or obj.
 
 Dir: One of NORTH, SOUTH, EAST, WEST, NORTHEAST, NORTHWEST, SOUTHEAST,
 SOUTHWEST, or 0 to halt.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 




 Dir: One of NORTH, SOUTH, EAST, WEST, NORTHEAST, NORTHWEST, SOUTHEAST,
 SOUTHWEST, or 0 to halt.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 



 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 


 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.


 Move Ref in the direction Dir continuously. Each step will be preceded
by Lag time of inactivity.




 A call to a walking function aborts any previous walking function called
on Ref. To halt walking, call walk(Ref,0).




 This function returns immediately, but continues to process in the
background.





---



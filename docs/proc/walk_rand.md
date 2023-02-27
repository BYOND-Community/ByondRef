

 walk\_rand proc
-----------------




**See also:** 


[get\_step\_rand proc](#/proc/get_step_rand) 

[step\_rand proc](#/proc/step_rand) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 





**See also:** 

**See also:**

[get\_step\_rand proc](#/proc/get_step_rand) 

[step\_rand proc](#/proc/step_rand) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 



[get\_step\_rand proc](#/proc/get_step_rand)

[step\_rand proc](#/proc/step_rand) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 


[step\_rand proc](#/proc/step_rand)

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_size var (movable atom)](#/atom/movable/var/step_size)


**Format:** 


 walk\_rand(Ref,Lag=0,Speed=0)
 


**Format:** 

**Format:**

 walk\_rand(Ref,Lag=0,Speed=0)



**Args:** 


 Ref: A mob or obj.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 




**Args:** 

**Args:**

 Ref: A mob or obj.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 



 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 


 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.


 Moves Ref randomly. Each step will be preceded by Lag time of inactivity.




 A call to a walking function aborts any previous walking function called
on Ref. To halt walking, call walk(Ref,0).




 This function returns immediately, but continues to process in the
background.





---



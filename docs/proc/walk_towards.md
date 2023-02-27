

 walk\_towards proc
--------------------




**See also:** 


[get\_step\_towards proc](#/proc/get_step_towards) 

[step\_towards proc](#/proc/step_towards) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 





**See also:** 

**See also:**

[get\_step\_towards proc](#/proc/get_step_towards) 

[step\_towards proc](#/proc/step_towards) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 



[get\_step\_towards proc](#/proc/get_step_towards)

[step\_towards proc](#/proc/step_towards) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 


[step\_towards proc](#/proc/step_towards)

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_size var (movable atom)](#/atom/movable/var/step_size)


**Format:** 


 walk\_towards(Ref,Trg,Lag=0,Speed=0)
 


**Format:** 

**Format:**

 walk\_towards(Ref,Trg,Lag=0,Speed=0)



**Args:** 


 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 





**Args:** 

**Args:**

 Ref: A mob or obj.
 
 Trg: An object on the map.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 




 Trg: An object on the map.
 
 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 



 Lag: Delay in world ticks between movement.
 
 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.
 


 Speed: Speed to move, in pixels. 0 uses Ref.step\_size.


 Move Ref in the direction of Trg continuously. Each step will be preceded
by Lag time of inactivity.




 A call to a walking function aborts any previous walking function called
on Ref. To halt walking, call walk(Ref,0).




 This function returns immediately, but continues to process in the
background.





---



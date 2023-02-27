

 get\_step\_to proc
--------------------




**See also:** 


[step\_to proc](#/proc/step_to) 

[walk\_to proc](#/proc/walk_to) 

[get\_steps\_to proc](#/proc/get_steps_to) 





**See also:** 

**See also:**

[step\_to proc](#/proc/step_to) 

[walk\_to proc](#/proc/walk_to) 

[get\_steps\_to proc](#/proc/get_steps_to) 



[step\_to proc](#/proc/step_to)

[walk\_to proc](#/proc/walk_to) 

[get\_steps\_to proc](#/proc/get_steps_to) 


[walk\_to proc](#/proc/walk_to)

[get\_steps\_to proc](#/proc/get_steps_to) 

[get\_steps\_to proc](#/proc/get_steps_to)


**Format:** 


 get\_step\_to(Ref, Trg, Min=0)
 


**Format:** 

**Format:**

 get\_step\_to(Ref, Trg, Min=0)



**Returns:** 


 The location of the new position, or 0 if no change.
 


**Returns:** 

**Returns:**

 The location of the new position, or 0 if no change.



**Args:** 


 Ref: Starting point or object.
 
 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 




**Args:** 

**Args:**

 Ref: Starting point or object.
 
 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 



 Trg: An object on the map.
 
 Min: The minimum distance between Ref and Trg before movement halts.
 


 Min: The minimum distance between Ref and Trg before movement halts.


 Calculate the position of a step from
 
 Ref
 
 on a path to
 
 Trg
 
 , taking obstacles into account.




 Ref


 Trg


 If
 
 Ref
 
 is within
 
 Min
 
 steps of
 
 Trg
 
 , no step is
computed. This is also true if the target is too far away (more than twice
 
 world.view
 
 steps). In either case, null is returned.




 Ref


 Min


 Trg


 world.view



---



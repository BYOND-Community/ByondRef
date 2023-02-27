

 get\_steps\_to proc
---------------------




**See also:** 


[step proc](#/proc/step) 

[step\_to proc](#/proc/step_to) 

[walk\_to proc](#/proc/walk_to) 

[get\_step\_to proc](#/proc/get_step_to) 






**See also:** 

**See also:**

[step proc](#/proc/step) 

[step\_to proc](#/proc/step_to) 

[walk\_to proc](#/proc/walk_to) 

[get\_step\_to proc](#/proc/get_step_to) 




[step proc](#/proc/step)

[step\_to proc](#/proc/step_to) 

[walk\_to proc](#/proc/walk_to) 

[get\_step\_to proc](#/proc/get_step_to) 



[step\_to proc](#/proc/step_to)

[walk\_to proc](#/proc/walk_to) 

[get\_step\_to proc](#/proc/get_step_to) 


[walk\_to proc](#/proc/walk_to)

[get\_step\_to proc](#/proc/get_step_to) 

[get\_step\_to proc](#/proc/get_step_to)


**Format:** 


 get\_steps\_to(Ref, Trg, Min=0)
 


**Format:** 

**Format:**

 get\_steps\_to(Ref, Trg, Min=0)



**Returns:** 


 A list of directions to step.
 


**Returns:** 

**Returns:**

 A list of directions to step.



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


 Calculate a set of steps from
 
 Ref
 
 on a path to
 
 Trg
 
 , taking obstacles into account. The result of the proc is a list
of directions that can be used with
 
 step()
 
 , or null if a path could
not be found.




 Ref


 Trg


 step()


 If
 
 Ref
 
 is within
 
 Min
 
 steps of
 
 Trg
 
 , no steps are
computed. This is also true if the target is too far away (more than twice
 
 world.view
 
 steps). In either case, null is returned.




 Ref


 Min


 Trg


 world.view



---



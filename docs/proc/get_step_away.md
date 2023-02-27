

 get\_step\_away proc
----------------------




**See also:** 


[step\_away proc](#/proc/step_away) 

[walk\_away proc](#/proc/walk_away) 




**See also:** 

**See also:**

[step\_away proc](#/proc/step_away) 

[walk\_away proc](#/proc/walk_away) 


[step\_away proc](#/proc/step_away)

[walk\_away proc](#/proc/walk_away) 

[walk\_away proc](#/proc/walk_away)


**Format:** 


 get\_step\_away(Ref, Trg, Max=5)
 


**Format:** 

**Format:**

 get\_step\_away(Ref, Trg, Max=5)



**Returns:** 


 The location of the new position, or 0 if no change.
 


**Returns:** 

**Returns:**

 The location of the new position, or 0 if no change.



**Args:** 


 Ref: Starting point or object.
 
 Trg: An object on the map.
 
 Max: The maximum distance between Ref and Targ before movement halts.
 




**Args:** 

**Args:**

 Ref: Starting point or object.
 
 Trg: An object on the map.
 
 Max: The maximum distance between Ref and Targ before movement halts.
 



 Trg: An object on the map.
 
 Max: The maximum distance between Ref and Targ before movement halts.
 


 Max: The maximum distance between Ref and Targ before movement halts.


 Calculate position of a step from
 
 Ref
 
 on a path away from
 
 Trg
 
 , taking obstacles into account. If
 
 Ref
 
 is farther than
 
 Max
 
 steps from
 
 Trg
 
 , 0 will be returned.




 Ref


 Trg


 Ref


 Max


 Trg



---



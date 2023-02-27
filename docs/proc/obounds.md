

 obounds proc
--------------




**See also:** 


[bounds proc](#/proc/bounds) 



**See also:** 

**See also:**

[bounds proc](#/proc/bounds) 

[bounds proc](#/proc/bounds)


**Format:** 


 obounds(Ref=src, Dist=0)
 
 obounds(Ref, x\_offset, y\_offset, extra\_width=0, extra\_height=0)
 



**Format:** 

**Format:**

 obounds(Ref=src, Dist=0)
 
 obounds(Ref, x\_offset, y\_offset, extra\_width=0, extra\_height=0)
 


 obounds(Ref, x\_offset, y\_offset, extra\_width=0, extra\_height=0)



**Returns:** 


 A list of atoms within the given bounding box, excluding Ref.
 


**Returns:** 

**Returns:**

 A list of atoms within the given bounding box, excluding Ref.



**Args:** 


 Ref: A turf, obj, or mob.
 
 Dist: A number (distance in pixels).
 
 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 





**Args:** 

**Args:**

 Ref: A turf, obj, or mob.
 
 Dist: A number (distance in pixels).
 
 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 




 Dist: A number (distance in pixels).
 
 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 



 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 


 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)


 The results from obounds() are identical to bounds(), but obounds() leaves
Ref out of the results.





---



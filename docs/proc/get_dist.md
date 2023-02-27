

 get\_dist proc
----------------




**See also:** 


[bounds\_dist proc](#/proc/bounds_dist) 



**See also:** 

**See also:**

[bounds\_dist proc](#/proc/bounds_dist) 

[bounds\_dist proc](#/proc/bounds_dist)


**Format:** 


 get\_dist(Loc1, Loc2)
 


**Format:** 

**Format:**

 get\_dist(Loc1, Loc2)



**Returns:** 


 The distance between
 
 Loc1
 
 and
 
 Loc2
 
 , in tiles. This is
the number of full-tile movements (disregarding any obstacles and allowing
diagonal moves
 *including across Z levels* 
 ) required to go from one to
the other. You can think of it as the max of their x, y, and z distances.
 


**Returns:** 

**Returns:**

 The distance between
 
 Loc1
 
 and
 
 Loc2
 
 , in tiles. This is
the number of full-tile movements (disregarding any obstacles and allowing
diagonal moves
 *including across Z levels* 
 ) required to go from one to
the other. You can think of it as the max of their x, y, and z distances.


 Loc1


 Loc2

*including across Z levels*


**Args:** 


 Loc1: An object on the map.
 
 Loc2: An object on the map.
 



**Args:** 

**Args:**

 Loc1: An object on the map.
 
 Loc2: An object on the map.
 


 Loc2: An object on the map.


 At this time,
 
 get\_dist()
 
 never returns a value greater than 127.




 get\_dist()


 For a distance in pixels, use
 
 bounds\_dist()
 
 .




 bounds\_dist()



 get\_dist()
 
 will return -1 in error conditions, such as when
 
 Loc1
 
 and
 
 Loc2
 
 are the same object.




 get\_dist()


 Loc1


 Loc2



---



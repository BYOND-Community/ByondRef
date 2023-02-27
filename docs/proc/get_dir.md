

 get\_dir proc
---------------




**See also:** 


[dir var (atom)](#/atom/var/dir) 



**See also:** 

**See also:**

[dir var (atom)](#/atom/var/dir) 

[dir var (atom)](#/atom/var/dir)


**Format:** 


 get\_dir(Loc1, Loc2)
 


**Format:** 

**Format:**

 get\_dir(Loc1, Loc2)



**Returns:** 


 The direction from Loc1 to Loc2. Possible results are
 
 NORTH
 
 ,
 
 SOUTH
 
 ,
 
 EAST
 
 ,
 
 WEST
 
 ,
 
 NORTHEAST
 
 ,
 
 NORTHWEST
 
 ,
 
 SOUTHEAST
 
 , and
 
 SOUTHWEST
 
 .
 


**Returns:** 

**Returns:**

 The direction from Loc1 to Loc2. Possible results are
 
 NORTH
 
 ,
 
 SOUTH
 
 ,
 
 EAST
 
 ,
 
 WEST
 
 ,
 
 NORTHEAST
 
 ,
 
 NORTHWEST
 
 ,
 
 SOUTHEAST
 
 , and
 
 SOUTHWEST
 
 .


 NORTH


 SOUTH


 EAST


 WEST


 NORTHEAST


 NORTHWEST


 SOUTHEAST


 SOUTHWEST



**Args:** 


 Loc1: An object on the map.
 
 Loc2: An object on the map.
 



**Args:** 

**Args:**

 Loc1: An object on the map.
 
 Loc2: An object on the map.
 


 Loc2: An object on the map.


 If the direction is not directly lying along one of the four primary
cardinal directions, the result will become the nearest diagonal direction
(eg. if
 
 Loc2
 
 is mostly north but a little to the east of
 
 Loc1
 
 , the direction returned will be
 
 NORTHEAST
 
 ).




 Loc2


 Loc1


 NORTHEAST



---



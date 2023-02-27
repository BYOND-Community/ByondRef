

 bounds proc
-------------




**See also:** 


[bound\_x var (movable atom)](#/atom/movable/var/bound_x) 

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 












**See also:** 

**See also:**

[bound\_x var (movable atom)](#/atom/movable/var/bound_x) 

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 










[bound\_x var (movable atom)](#/atom/movable/var/bound_x)

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 









[bound\_y var (movable atom)](#/atom/movable/var/bound_y)

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 








[bound\_width var (movable atom)](#/atom/movable/var/bound_width)

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 







[bound\_height var (movable atom)](#/atom/movable/var/bound_height)

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 






[step\_x var (movable atom)](#/atom/movable/var/step_x)

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 





[step\_y var (movable atom)](#/atom/movable/var/step_y)

[locs list var (movable atom)](#/atom/movable/var/locs) 

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 




[locs list var (movable atom)](#/atom/movable/var/locs)

[obounds proc](#/proc/obounds) 

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 



[obounds proc](#/proc/obounds)

[Pixel movement](#/{notes}/pixel-movement) 

[bounds var (client)](#/client/var/bounds) 


[Pixel movement](#/{notes}/pixel-movement)

[bounds var (client)](#/client/var/bounds) 

[bounds var (client)](#/client/var/bounds)


**Format:** 


 bounds(Ref=src, Dist=0)
 
 bounds(Ref, x\_offset, y\_offset, extra\_width=0, extra\_height=0)
 
 bounds(x, y, width, height, z)
 




**Format:** 

**Format:**

 bounds(Ref=src, Dist=0)
 
 bounds(Ref, x\_offset, y\_offset, extra\_width=0, extra\_height=0)
 
 bounds(x, y, width, height, z)
 



 bounds(Ref, x\_offset, y\_offset, extra\_width=0, extra\_height=0)
 
 bounds(x, y, width, height, z)
 


 bounds(x, y, width, height, z)



**Returns:** 


 A list of atoms within the given bounding box.
 


**Returns:** 

**Returns:**

 A list of atoms within the given bounding box.



**Args:** 


 Ref: A turf, obj, or mob.
 
 Dist: A number (distance in pixels).
 
 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 
 x, y, z: Lower left corner of bounding box in absolute coords; x=1,y=1 is lower left of map
 
 width, height: Size of bounding box in absolute coords
 







**Args:** 

**Args:**

 Ref: A turf, obj, or mob.
 
 Dist: A number (distance in pixels).
 
 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 
 x, y, z: Lower left corner of bounding box in absolute coords; x=1,y=1 is lower left of map
 
 width, height: Size of bounding box in absolute coords
 






 Dist: A number (distance in pixels).
 
 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 
 x, y, z: Lower left corner of bounding box in absolute coords; x=1,y=1 is lower left of map
 
 width, height: Size of bounding box in absolute coords
 





 x\_offset, y\_offset: Shift to bounding box position (from Ref's bounding box)
 
 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 
 x, y, z: Lower left corner of bounding box in absolute coords; x=1,y=1 is lower left of map
 
 width, height: Size of bounding box in absolute coords
 




 extra\_width, extra\_height: Adjustment to bounding box size (from Ref's bounding box)
 
 x, y, z: Lower left corner of bounding box in absolute coords; x=1,y=1 is lower left of map
 
 width, height: Size of bounding box in absolute coords
 



 x, y, z: Lower left corner of bounding box in absolute coords; x=1,y=1 is lower left of map
 
 width, height: Size of bounding box in absolute coords
 


 width, height: Size of bounding box in absolute coords


 To leave Ref out of the results, use obounds() instead.




 Calling bounds() will default to bounds(src,0), if src is a turf, obj, or
mob. This returns all turfs, objs, and mobs (including src) within src's
bounding box.




 Changing the distance will return all objects within that distance from the
bounding box. E.g., bounds(turf,12) will show you everything within 12 pixels
of that turf.




 An object's bounding box can also be offset. bounds(src,-6,0) shows what src
would touching if it moved 6 pixels west. bounds(turf,-12,-12,24,24) is
equivalent to bounds(turf,12).




 In the final form, bounds() can use absolute coordinates and does not need
an object to be Ref. Absolute coordinates start at 1,1 at the lower left corner
of the map, by tradition.





---



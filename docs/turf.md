

 turf
------




**See also:** 


[atom](#/atom) 

[procs (turf)](#/turf/proc) 

[vars (turf)](#/turf/var) 

[Map](#/map) 






**See also:** 

**See also:**

[atom](#/atom) 

[procs (turf)](#/turf/proc) 

[vars (turf)](#/turf/var) 

[Map](#/map) 




[atom](#/atom)

[procs (turf)](#/turf/proc) 

[vars (turf)](#/turf/var) 

[Map](#/map) 



[procs (turf)](#/turf/proc)

[vars (turf)](#/turf/var) 

[Map](#/map) 


[vars (turf)](#/turf/var)

[Map](#/map) 

[Map](#/map)

 Turfs cover the surface of the map. They are derived from
 
 /turf
 
 which derives from
 
 /atom
 
 .




 /turf


 /atom


 This example defines the turf prototype
 
 /turf/floor
 
 and
 
 /turf/wall
 
 .




 /turf/floor


 /turf/wall

### 
 Example:



 turf
 floor
 desc = "A wood plank floor."
 wall
 desc = "A stone wall."
 density = 1


 Turfs cannot be moved. They can only be created or destroyed by changing
 
 world.maxx
 
 ,
 
 world.maxy
 
 , or
 
 world.maxz
 
 . When you
create a new turf with
 
 new()
 
 , it always replaces the old one.




 world.maxx


 world.maxy


 world.maxz


 new()

### 
 Example:



 // replace old\_turf with a wall
var/turf/wall/T = new(old\_turf)



---



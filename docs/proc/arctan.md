

 arctan proc
-------------




**See also:** 


[arcsin proc](#/proc/arcsin) 

[arccos proc](#/proc/arccos) 

[tan proc](#/proc/tan) 

[turn proc](#/proc/turn) 






**See also:** 

**See also:**

[arcsin proc](#/proc/arcsin) 

[arccos proc](#/proc/arccos) 

[tan proc](#/proc/tan) 

[turn proc](#/proc/turn) 




[arcsin proc](#/proc/arcsin)

[arccos proc](#/proc/arccos) 

[tan proc](#/proc/tan) 

[turn proc](#/proc/turn) 



[arccos proc](#/proc/arccos)

[tan proc](#/proc/tan) 

[turn proc](#/proc/turn) 


[tan proc](#/proc/tan)

[turn proc](#/proc/turn) 

[turn proc](#/proc/turn)


**Format:** 


 arctan(A)
 
 arctan(x, y)
 



**Format:** 

**Format:**

 arctan(A)
 
 arctan(x, y)
 


 arctan(x, y)



**Returns:** 


 The inverse tangent of A in degrees; or for x,y, the polar coordinate angle.
 


**Returns:** 

**Returns:**

 The inverse tangent of A in degrees; or for x,y, the polar coordinate angle.


 When
 
 arctan
 
 is called with just one argument, the resulting angle
can range from -90 to 90.




 arctan


 The two-argument form uses the polar angle. This angle starts at 0° for
due east, and increases counter-clockwise from there. Therefore 1,0 has an
arctangent of 0°, 0,1 is 90°, -1,0 is 180°, and so on. At point
0,0 the angle is undefined since it could be any angle, but
 
 arctan
 
 will return 0.




 arctan

### 
 Example:



 mob/verb/test()
 usr << arctan(0) // 0
 usr << arctan(1) // 45
 usr << arctan(sqrt(3)) // 60

 // polar coordinates
 usr << arctan(3, 4) // 53.1301
 usr << arctan(-1, 1) // 135
 usr << arctan(0, -5) // 270


 Here's another example, in which a rotating turret points to a target on
another tile.




 mob/turret
 proc/PointAt(atom/target)
 if(!target) return
 var/dx = target.x - x
 var/dy = target.y - y
 // turret's icon normally faces east
 transform = matrix().Turn(-arctan(dx, dy))



---



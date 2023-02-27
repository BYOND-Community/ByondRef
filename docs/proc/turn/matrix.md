

 turn proc (applied to a matrix)
---------------------------------




**See also:** 


[turn proc](#/proc/turn) 

[matrix](#/matrix) 




**See also:** 

**See also:**

[turn proc](#/proc/turn) 

[matrix](#/matrix) 


[turn proc](#/proc/turn)

[matrix](#/matrix) 

[matrix](#/matrix)


**Format:** 


 turn(Matrix, Angle)
 


**Format:** 

**Format:**

 turn(Matrix, Angle)



**Returns:** 


 A new matrix which has been rotated.
 


**Returns:** 

**Returns:**

 A new matrix which has been rotated.



**Args:** 


 Matrix: a matrix to rotate
 
 Angle: An angle in degrees (clockwise rotation).
 



**Args:** 

**Args:**

 Matrix: a matrix to rotate
 
 Angle: An angle in degrees (clockwise rotation).
 


 Angle: An angle in degrees (clockwise rotation).

### 
 Example:



 mob/verb/drink()
 //this effect is very confusing!
 usr.transform = turn(usr.transform, 90)
 usr << "Woah! That stuff is powerful!"
 sleep(200)
 usr.transform = null



---



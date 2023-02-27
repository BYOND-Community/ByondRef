

 round proc
------------




**See also:** 


[floor proc](#/proc/floor) 

[ceil proc](#/proc/ceil) 

[trunc proc](#/proc/trunc) 

[fract proc](#/proc/fract) 






**See also:** 

**See also:**

[floor proc](#/proc/floor) 

[ceil proc](#/proc/ceil) 

[trunc proc](#/proc/trunc) 

[fract proc](#/proc/fract) 




[floor proc](#/proc/floor)

[ceil proc](#/proc/ceil) 

[trunc proc](#/proc/trunc) 

[fract proc](#/proc/fract) 



[ceil proc](#/proc/ceil)

[trunc proc](#/proc/trunc) 

[fract proc](#/proc/fract) 


[trunc proc](#/proc/trunc)

[fract proc](#/proc/fract) 

[fract proc](#/proc/fract)


**Format:** 


 round(A)
 
 round(A,B)
 



**Format:** 

**Format:**

 round(A)
 
 round(A,B)
 


 round(A,B)



**Returns:** 


 rounded A
 


**Returns:** 

**Returns:**

 rounded A



**Args:** 


 A: A number.
 
 B: The nearest multiple to round A.
 



**Args:** 

**Args:**

 A: A number.
 
 B: The nearest multiple to round A.
 


 B: The nearest multiple to round A.


 The first format returns the floor of A (the largest integer less than or
equal to A), and has been deprecated in favor of
 
 floor(A)
 
 . The second
format rounds A to the nearest multiple of B.




 floor(A)

### 
 Example:



 usr << round(1.45) // outputs 1

usr << round(-1.45) // outputs -2

usr << round(1.45,1.5) // outputs 1.5



---



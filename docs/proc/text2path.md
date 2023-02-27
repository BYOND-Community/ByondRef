

 text2path proc
----------------




**See also:** 


[ispath proc](#/proc/ispath) 



**See also:** 

**See also:**

[ispath proc](#/proc/ispath) 

[ispath proc](#/proc/ispath)


**Format:** 


 text2path(T)
 


**Format:** 

**Format:**

 text2path(T)



**Args:** 


 T: A text string.
 


**Args:** 

**Args:**

 T: A text string.



**Returns:** 


 a type path or null.
 


**Returns:** 

**Returns:**

 a type path or null.

### 
 Example:



 var/myturf = text2path("/turf/[src.color]")
if(myturf)
 src.loc = locate(myturf)


 T is changed from a text string to the equivalent type path, or null if
 there is no such type.





---



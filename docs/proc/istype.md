

 istype proc
-------------




**See also:** 


[ispath proc](#/proc/ispath) 

[locate proc](#/proc/locate) 

[typesof proc](#/proc/typesof) 





**See also:** 

**See also:**

[ispath proc](#/proc/ispath) 

[locate proc](#/proc/locate) 

[typesof proc](#/proc/typesof) 



[ispath proc](#/proc/ispath)

[locate proc](#/proc/locate) 

[typesof proc](#/proc/typesof) 


[locate proc](#/proc/locate)

[typesof proc](#/proc/typesof) 

[typesof proc](#/proc/typesof)


**Format:** 


 istype(Val,Type)
 
 istype(Val)
 



**Format:** 

**Format:**

 istype(Val,Type)
 
 istype(Val)
 


 istype(Val)



**Returns:** 


 1 if Val is derived from Type; 0 otherwise.
 


**Returns:** 

**Returns:**

 1 if Val is derived from Type; 0 otherwise.



**Args:** 


 Val: An object instance.
 
 Type: An object prototype or instance. If no type is specified and a
 variable was passed in as the first argument, it will default to the
 declared type of the variable.
 



**Args:** 

**Args:**

 Val: An object instance.
 
 Type: An object prototype or instance. If no type is specified and a
 variable was passed in as the first argument, it will default to the
 declared type of the variable.
 


 Type: An object prototype or instance. If no type is specified and a
 variable was passed in as the first argument, it will default to the
 declared type of the variable.


 If you don't have an object instance to test, but just want to see if one
prototype derives from another one, use
 [ispath()](#/proc/ispath) 
 instead.



[ispath()](#/proc/ispath)
### 
 Example:



 var/M
M = new/mob/ugly/duckling()
if(istype(M,/mob/ugly)) //this will be true
 usr << "[M] is ugly!"


 Using implicit types, that same example can be rewritten as follows:




 var/mob/ugly/M
M = new/mob/ugly/duckling()
if(istype(M)) //this will be true
 usr << "[M] is ugly!"



---



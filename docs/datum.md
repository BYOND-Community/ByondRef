

 datum
-------




**See also:** 


[atom](#/atom) 

[procs (datum)](#/datum/proc) 

[vars (datum)](#/datum/var) 





**See also:** 

**See also:**

[atom](#/atom) 

[procs (datum)](#/datum/proc) 

[vars (datum)](#/datum/var) 



[atom](#/atom)

[procs (datum)](#/datum/proc) 

[vars (datum)](#/datum/var) 


[procs (datum)](#/datum/proc)

[vars (datum)](#/datum/var) 

[vars (datum)](#/datum/var)

 The datum object is the ancestor of all other data types in DM. (The
only exceptions are currently /world, /client, /list, and /savefile, but
those will be brought into conformance soon.) That means that the variables
and procedures of /datum are inherited by all other types of objects.




 When you define a new "top level" object, if you do not specify a
parent\_type, it defaults to /datum.



### 
 Example:



 datum
 //definitions to be shared by all object types
 proc/DebugMe()
 world.log << "/datum properties:"
 world.log << "type: [type]"
 world.log << "parent\_type: [parent\_type]"
 return ..()

MyType
 var
 myvar = "test"
 DebugMe()
 world.log << "/MyType properties:"
 world.log << "myvar: [myvar]"
 return ..() //this calls /datum/proc/DebugMe()



---



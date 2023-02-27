

 new proc
----------




**See also:** 


[New proc (atom)](#/atom/proc/New) 

[New proc (datum)](#/datum/proc/New) 

[New proc (icon)](#/icon/proc/New) 

[newlist proc](#/proc/newlist) 

[path operators](#/operator/path) 







**See also:** 

**See also:**

[New proc (atom)](#/atom/proc/New) 

[New proc (datum)](#/datum/proc/New) 

[New proc (icon)](#/icon/proc/New) 

[newlist proc](#/proc/newlist) 

[path operators](#/operator/path) 





[New proc (atom)](#/atom/proc/New)

[New proc (datum)](#/datum/proc/New) 

[New proc (icon)](#/icon/proc/New) 

[newlist proc](#/proc/newlist) 

[path operators](#/operator/path) 




[New proc (datum)](#/datum/proc/New)

[New proc (icon)](#/icon/proc/New) 

[newlist proc](#/proc/newlist) 

[path operators](#/operator/path) 



[New proc (icon)](#/icon/proc/New)

[newlist proc](#/proc/newlist) 

[path operators](#/operator/path) 


[newlist proc](#/proc/newlist)

[path operators](#/operator/path) 

[path operators](#/operator/path)


**Format:** 


 new Type(Args)
 


**Format:** 

**Format:**

 new Type(Args)



**Returns:** 


 A reference to a new instance of Type.
 


**Returns:** 

**Returns:**

 A reference to a new instance of Type.



**Args:** 


 Type: The type of object to create.
 
 Args: Arguments for the Type.New() proc.
 



**Args:** 

**Args:**

 Type: The type of object to create.
 
 Args: Arguments for the Type.New() proc.
 


 Args: Arguments for the Type.New() proc.


 A new instance of Type is created. The arguments (Args) are passed to its
New() proc. A handy short-cut: if Type is not specified and new() is being
used in an assignment, the variable type of the left-hand-side will be used as
the default type.




 The atom types /area, /turf, /obj, and /mob all take a location argument
specifying the initial position. If not specified, it defaults to null.




 Newly created areas or turfs replace any existing area or turf at the
specified location.



### 
 Example:



 obj/stick
mob/verb/magic\_stick()
 var/obj/stick/S = new(src) //create a stick in my inventory
 S.desc = "This is no ordinary stick!"
 view() << "[src] creates \an [S] from thin air!"



---



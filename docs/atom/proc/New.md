

 New proc (atom)
-----------------




**See also:** 


[New proc (datum)](#/datum/proc/New) 

[new proc](#/proc/new) 




**See also:** 

**See also:**

[New proc (datum)](#/datum/proc/New) 

[new proc](#/proc/new) 


[New proc (datum)](#/datum/proc/New)

[new proc](#/proc/new) 

[new proc](#/proc/new)


**Format:** 


 New(loc)
 

 (supports
 [named arguments](#/proc/arguments/named) 
 )
 




**Format:** 

**Format:**

 New(loc)
 

 (supports
 [named arguments](#/proc/arguments/named) 
 )
 




 (supports
 [named arguments](#/proc/arguments/named) 
 )
 


 (supports
 [named arguments](#/proc/arguments/named) 
 )

[named arguments](#/proc/arguments/named)


**When:** 


 Called when the object is created.
 


**When:** 

**When:**

 Called when the object is created.



**Args:** 


 loc: The initial location.
 


**Args:** 

**Args:**

 loc: The initial location.



**Default action:** 


 None.
 


**Default action:** 

**Default action:**

 None.


 By the time New() is called, the object has already been created at the
specified location and all of its variables have been initialized. You can
perform additional initialization by overriding this procedure.




 Since the initial location parameter passed to
 `new()` 
 is
applied before New() is even called, there is some special handling of the
 
 loc
 
 variable when using named arguments in a call. Normally, if a
procedure is overridden, named arguments in a call are matched against those
in the the overridden definition. In this case, however, the
 
 loc
 
 parameter name is hard-coded. Regardless of what you call the first argument
in your definition of New(), the initial location will be taken from the first
positional argument, or from the argument named
 
 loc
 
 if there are no
positional arguments.



`new()`

 loc


 loc


 loc


 The following example does some extra initialization that is not possible
in the variable definition section, because it requires a runtime evaluation.
This is a common reason to use New().



### 
 Example:



 mob
 var
 birthdate //time stamp
 New()
 birthdate = world.realtime
 return ..()
 verb/look()
 set src in view()
 usr << "[src] was born on [time2text(birthdate,"DD-MMM-YYYY")]."



---



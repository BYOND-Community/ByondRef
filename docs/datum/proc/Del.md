

 Del proc (datum)
------------------




**See also:** 


[del proc](#/proc/del) 

[garbage collection](#/DM/garbage) 




**See also:** 

**See also:**

[del proc](#/proc/del) 

[garbage collection](#/DM/garbage) 


[del proc](#/proc/del)

[garbage collection](#/DM/garbage) 

[garbage collection](#/DM/garbage)


**Format:** 


 Del()
 


**Format:** 

**Format:**

 Del()



**When:** 


 Called when the object is destroyed, for example by using the
 `del` 
 instruction.
 


**When:** 

**When:**

 Called when the object is destroyed, for example by using the
 `del` 
 instruction.

`del`


**Default action:** 


 Delete the object. The contents of atomic objects are also destroyed at
this time, as though
 `del` 
 were called on each one of them.
 


**Default action:** 

**Default action:**

 Delete the object. The contents of atomic objects are also destroyed at
this time, as though
 `del` 
 were called on each one of them.

`del`

 When the world is destroyed, the
 
 Del()
 
 proc is not automatically
called. The only object for which it is called is
 [/world](#/world) 
 .
If you need the
 
 Del()
 
 proc for a particular object to be called at
that time, you should explicitly call it from
 
 world/Del()
 
 .




 Del()

[/world](#/world)

 Del()


 world/Del()


 Note:
 **Always** 
 call
 
 ..()
 
 at the end of the proc if you
override it.



**Always**

 ..()



---



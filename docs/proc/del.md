

 del proc
----------




**See also:** 


[Del proc (datum)](#/datum/proc/Del) 

[garbage collection](#/DM/garbage) 

[refcount proc](#/proc/refcount) 





**See also:** 

**See also:**

[Del proc (datum)](#/datum/proc/Del) 

[garbage collection](#/DM/garbage) 

[refcount proc](#/proc/refcount) 



[Del proc (datum)](#/datum/proc/Del)

[garbage collection](#/DM/garbage) 

[refcount proc](#/proc/refcount) 


[garbage collection](#/DM/garbage)

[refcount proc](#/proc/refcount) 

[refcount proc](#/proc/refcount)


**Format:** 


 del Object
 


**Format:** 

**Format:**

 del Object



**Args:** 


 Object: Any data object (datum, savefile, world, you name it)
 


**Args:** 

**Args:**

 Object: Any data object (datum, savefile, world, you name it)


 Destroy an object and null out all references to it. Procs that are
executing with
 `src` 
 equal to that object are silently killed,
causing execution to return to the caller. If that is not what you want, you
should detach the proc from the source object by setting
 `src` 
 to
 `null` 
 .



`src`
`src`
`null`

 When an object is deleted, its Del() procedure is called. Currently, if
the Del() procedure does not execute the default action (by calling ..()),
then the deletion of the object is aborted. You should not depend on this, as
it may change. In other words, be sure to always call the default handler
after doing your own stuff.



### 
 Example:



 mob/Del()
 src << "Aaaaaaaah!"
 ..()
mob/verb/self\_destruct()
 del usr


 While manual object deletion is useful in many cases, the search for live
references to an object does take some time. The more active objects in the
world, and the more variables in those objects, the longer the search will
take. For larger projects, this search time can become significant. In these
cases, as a best practice, manual deletion should be avoided by ensuring that
all references to an object are taken care of when the need for object
destruction arises. Objects that have no references are deleted automatically
without the need for a search. See
 [garbage collection](#/DM/garbage) 
 for more details.



[garbage collection](#/DM/garbage)


---



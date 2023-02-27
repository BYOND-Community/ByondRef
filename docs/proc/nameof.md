

 nameof proc
-------------




**See also:** 


[:: operator](#/operator/::) 



**See also:** 

**See also:**

[:: operator](#/operator/::) 

[:: operator](#/operator/::)


**Format:** 


 nameof(Var)
 
 nameof(ProcRef)
 
 nameof(Path)
 




**Format:** 

**Format:**

 nameof(Var)
 
 nameof(ProcRef)
 
 nameof(Path)
 



 nameof(ProcRef)
 
 nameof(Path)
 


 nameof(Path)



**Args:** 


 Var: A variable, e.g. src.density or foo::bar.
 
 ProcRef: A proc reference, e.g. /mob::Enter().
 
 Path: A type path, e.g. /obj/item/barrel.
 




**Args:** 

**Args:**

 Var: A variable, e.g. src.density or foo::bar.
 
 ProcRef: A proc reference, e.g. /mob::Enter().
 
 Path: A type path, e.g. /obj/item/barrel.
 



 ProcRef: A proc reference, e.g. /mob::Enter().
 
 Path: A type path, e.g. /obj/item/barrel.
 


 Path: A type path, e.g. /obj/item/barrel.


 This returns the name of a var or proc, or the last part of a type path.
This proc only exists at compile-time.




 The main purpose of this proc is to turn a proc reference into a name,
which is useful in some esoteric situations.



### 
 Example:



 var/list/event\_queue

proc/CallLater(object, procref, a, b, c)
 var/list/forlater = list(object, nameof(procref), a, b, c)
 event\_queue ||= list()
 event\_queue[++event\_queue.len] = forlater

world/Tick()
 while(length(event\_queue))
 var/list/forlater = event\_queue[1]
 event\_queue.Cut(1,2)
 var/object = forlater[1]
 var/procname = forlater[2]
 var/a = forlater[3]
 var/b = forlater[4]
 var/c = forlater[5]
 call(object, procname)(a, b, c)



---



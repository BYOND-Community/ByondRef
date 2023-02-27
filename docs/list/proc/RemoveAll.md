

 RemoveAll proc (list)
-----------------------




**See also:** 


[Add proc (list)](#/list/proc/Add) 

[Remove proc (list)](#/list/proc/Remove) 




**See also:** 

**See also:**

[Add proc (list)](#/list/proc/Add) 

[Remove proc (list)](#/list/proc/Remove) 


[Add proc (list)](#/list/proc/Add)

[Remove proc (list)](#/list/proc/Remove) 

[Remove proc (list)](#/list/proc/Remove)


**Format:** 


 list.RemoveAll(Item1,Item2,...)
 


**Format:** 

**Format:**

 list.RemoveAll(Item1,Item2,...)



**Returns:** 


 Number of items removed.
 


**Returns:** 

**Returns:**

 Number of items removed.



**Args:** 


 One or more items to remove entirely from the list.
 


**Args:** 

**Args:**

 One or more items to remove entirely from the list.


 Removes all copies of the specified items from the list. If an argument is
itself a list, each item contained in it will be removed.




 This is basically a faster version of the statement
 
 while(list.Remove(Item1,Item2,...))
 
 with an empty code block. For
large lists this might be a big improvement because the list doesn't have to
be traversed every time.




 while(list.Remove(Item1,Item2,...))



---



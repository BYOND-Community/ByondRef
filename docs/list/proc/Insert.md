

 Insert proc (list)
--------------------




**See also:** 


[Cut proc (list)](#/list/proc/Cut) 

[Copy proc (list)](#/list/proc/Copy) 

[Swap proc (list)](#/list/proc/Swap) 





**See also:** 

**See also:**

[Cut proc (list)](#/list/proc/Cut) 

[Copy proc (list)](#/list/proc/Copy) 

[Swap proc (list)](#/list/proc/Swap) 



[Cut proc (list)](#/list/proc/Cut)

[Copy proc (list)](#/list/proc/Copy) 

[Swap proc (list)](#/list/proc/Swap) 


[Copy proc (list)](#/list/proc/Copy)

[Swap proc (list)](#/list/proc/Swap) 

[Swap proc (list)](#/list/proc/Swap)


**Format:** 


 list.Insert(Index,Item1,Item2...)
 


**Format:** 

**Format:**

 list.Insert(Index,Item1,Item2...)



**Returns:** 


 The index following the inserted items.
 


**Returns:** 

**Returns:**

 The index following the inserted items.



**Args:** 


 Index: The index where the new item will be inserted. Any value
 already at that index will be pushed forward.
 
 Item1: A value or list of values to insert.
 
 Item2...: (optional) Additional items to insert, immediately after the
 previous item(s).
 




**Args:** 

**Args:**

 Index: The index where the new item will be inserted. Any value
 already at that index will be pushed forward.
 
 Item1: A value or list of values to insert.
 
 Item2...: (optional) Additional items to insert, immediately after the
 previous item(s).
 



 Item1: A value or list of values to insert.
 
 Item2...: (optional) Additional items to insert, immediately after the
 previous item(s).
 


 Item2...: (optional) Additional items to insert, immediately after the
 previous item(s).


 Insert values into a list at a specific point. Using Index=0 or
Index=list.len+1 is the same as adding to the list.




 If any of the items you insert is itself a list, its elements will be
inserted instead of the list itself.




 Note: This proc doesn't work with many special lists such as
 `contents` 
 or
 `overlays` 
 .



`contents`
`overlays`


---



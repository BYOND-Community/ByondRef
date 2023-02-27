

 Swap proc (list)
------------------




**See also:** 


[Cut proc (list)](#/list/proc/Cut) 

[Copy proc (list)](#/list/proc/Copy) 

[Insert proc (list)](#/list/proc/Insert) 





**See also:** 

**See also:**

[Cut proc (list)](#/list/proc/Cut) 

[Copy proc (list)](#/list/proc/Copy) 

[Insert proc (list)](#/list/proc/Insert) 



[Cut proc (list)](#/list/proc/Cut)

[Copy proc (list)](#/list/proc/Copy) 

[Insert proc (list)](#/list/proc/Insert) 


[Copy proc (list)](#/list/proc/Copy)

[Insert proc (list)](#/list/proc/Insert) 

[Insert proc (list)](#/list/proc/Insert)


**Format:** 


 list.Swap(Index1,Index2)
 


**Format:** 

**Format:**

 list.Swap(Index1,Index2)



**Returns:** 


 Nothing.
 


**Returns:** 

**Returns:**

 Nothing.



**Args:** 


 Index1: The index (1 to list.len) of one of the items to swap.
 
 Index2: The index of the other item.
 



**Args:** 

**Args:**

 Index1: The index (1 to list.len) of one of the items to swap.
 
 Index2: The index of the other item.
 


 Index2: The index of the other item.


 Swap two items in a list. If the list has associated values, they
will be preserved. This is most useful for user-defined sorting routines.



### 
 Example:



 var/item
var/list/L = list("orange" = 3, "green" = 2, "blue" = 5)
for(item in L) world << "[item] -> [L[item]]"
world << ""
L.Swap(1, 3)
for(item in L) world << "[item] -> [L[item]]"

### 
 Result:



 orange -> 3
green -> 2
blue -> 5

blue -> 5
green -> 2
orange -> 3


 Note: This proc doesn't work with many special lists such as
 `contents` 
 or
 `overlays` 
 .



`contents`
`overlays`


---



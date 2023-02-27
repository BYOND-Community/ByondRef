

 list proc
-----------




**See also:** 


[arglist proc](#/proc/arglist) 

[list](#/list) 

[list associations](#/list/associations) 





**See also:** 

**See also:**

[arglist proc](#/proc/arglist) 

[list](#/list) 

[list associations](#/list/associations) 



[arglist proc](#/proc/arglist)

[list](#/list) 

[list associations](#/list/associations) 


[list](#/list)

[list associations](#/list/associations) 

[list associations](#/list/associations)


**Format:** 


 list(A,B,C,...)
 
 or
 
 list(A=a,B=b,C=c,...)
 




**Format:** 

**Format:**

 list(A,B,C,...)
 
 or
 
 list(A=a,B=b,C=c,...)
 



 or
 
 list(A=a,B=b,C=c,...)
 


 list(A=a,B=b,C=c,...)



**Returns:** 


 A new list with contents A, B, C, and (optional) associated values a, b, c.
 


**Returns:** 

**Returns:**

 A new list with contents A, B, C, and (optional) associated values a, b, c.



**Args:** 


 Arbitrary number of elements to be inserted into the list.
 


**Args:** 

**Args:**

 Arbitrary number of elements to be inserted into the list.


 Assign elements to a list.



### 
 Example:



 var/L[]
L = list(1,2,3)


 This creates a new list 'L' that initially contains elements 1, 2, and
3. The length of L is 3.




 The
 `list()` 
 instruction may also be used to create associative
lists.



`list()`
### 
 Example:



 var/list/lst = list("player" = "James Byond", "score" = 2000)


 That creates a list with contents ("player, "score") and associated values
("James Byond", 2000) respectively.




 The index values should be constants, and that usually means text
constants. When these index values happen to be text strings that satisfy all
the requirements for variable names, this may also be written in a convenient
short-hand without the double quotes:




 var/list/lst = list(player = "James Byond", score = 2000)


 In other words, this is exactly the same syntax as for
 [named arguments](#/proc/arguments/named) 
 .



[named arguments](#/proc/arguments/named)


---



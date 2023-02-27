

 in operator
-------------




**See also:** 


[list](#/list) 

[operators](#/operator) 

[! operator](#/operator/!) 

[locate proc](#/proc/locate) 

[input proc](#/proc/input) 







**See also:** 

**See also:**

[list](#/list) 

[operators](#/operator) 

[! operator](#/operator/!) 

[locate proc](#/proc/locate) 

[input proc](#/proc/input) 





[list](#/list)

[operators](#/operator) 

[! operator](#/operator/!) 

[locate proc](#/proc/locate) 

[input proc](#/proc/input) 




[operators](#/operator)

[! operator](#/operator/!) 

[locate proc](#/proc/locate) 

[input proc](#/proc/input) 



[! operator](#/operator/!)

[locate proc](#/proc/locate) 

[input proc](#/proc/input) 


[locate proc](#/proc/locate)

[input proc](#/proc/input) 

[input proc](#/proc/input)


**Format:** 


 A in List
 


**Format:** 

**Format:**

 A in List



**Returns:** 

**1 if A exists in List; 0 if not** 




**Returns:** 

**1 if A exists in List; 0 if not** 


**Returns:**

**1 if A exists in List; 0 if not** 

**1 if A exists in List; 0 if not**

 This is a relatively safe way to check if an item is in a list, because
the value of
 
 List
 
 is allowed to be a non-list value, such as null.
Compare to
 
 List.Find(A)
 
 which will fail if
 
 List
 
 is not an
actual list.




 List


 List.Find(A)


 List



 List
 
 can also be an atom, in which case
 
 A in List
 
 is
equivalent to
 
 A in List.contents
 
 .




 List


 A in List


 A in List.contents



 The
 
 in
 
 operator has a lower precedence than
 
 !
 
 , which can be a point of confusion. If you want to check if
something is
 *not* 
 in a list, it's a common mistake to try
 
 if(!A in
List)
 
 . Unfortunately the
 
 !A
 
 part is evaluated first and becomes
0 or 1, so you're really asking if 0 or 1 is in the list. The correct way to
check if something is not in a list is to wrap the
 
 in
 
 operator and
its operands with parentheses, as in
 
 if(!(A in List))
 
 .
 



 Similarly, the assignment operators also have higher precedence than
 
 in
 
 , so
 
 has\_thing = thing in src
 
 will not be interpreted as
you might expect. Again the solution is to use parentheses, e.g.
 
 has\_thing
= (thing in src)
 
 .
 




 The
 
 in
 
 operator has a lower precedence than
 
 !
 
 , which can be a point of confusion. If you want to check if
something is
 *not* 
 in a list, it's a common mistake to try
 
 if(!A in
List)
 
 . Unfortunately the
 
 !A
 
 part is evaluated first and becomes
0 or 1, so you're really asking if 0 or 1 is in the list. The correct way to
check if something is not in a list is to wrap the
 
 in
 
 operator and
its operands with parentheses, as in
 
 if(!(A in List))
 
 .




 in


 !

*not*

 if(!A in
List)


 !A


 in


 if(!(A in List))


 Similarly, the assignment operators also have higher precedence than
 
 in
 
 , so
 
 has\_thing = thing in src
 
 will not be interpreted as
you might expect. Again the solution is to use parentheses, e.g.
 
 has\_thing
= (thing in src)
 
 .




 in


 has\_thing = thing in src


 has\_thing
= (thing in src)


 The
 
 in
 
 operator is also a modifier for some procs such as
 [locate()](#/proc/locate) 
 and
 [input()](#/proc/input) 
 .




 in

[locate()](#/proc/locate)
[input()](#/proc/input)

 Note: For
 [associative
lists](#/list/associations) 
 there's a faster way to see if an item is in that list. The
lookup of
 
 List[A]
 
 in an associative list is relatively fast, so if
the associated value is always expected to be true (not null, 0, or an empty
string), you can use
 
 List[A]
 
 instead of
 
 A in List
 
 in those
situations.



[associative
lists](#/list/associations)

 List[A]


 List[A]


 A in List



---



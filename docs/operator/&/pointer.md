

 & pointer operator
--------------------




**See also:** 


[\* operator (pointers)](#/operator/*/prefix) 

[operators](#/operator) 

[ispointer proc](#/proc/ispointer) 





**See also:** 

**See also:**

[\* operator (pointers)](#/operator/*/prefix) 

[operators](#/operator) 

[ispointer proc](#/proc/ispointer) 



[\* operator (pointers)](#/operator/*/prefix)

[operators](#/operator) 

[ispointer proc](#/proc/ispointer) 


[operators](#/operator)

[ispointer proc](#/proc/ispointer) 

[ispointer proc](#/proc/ispointer)


**Format:** 


 &A
 


**Format:** 

**Format:**

 &A



**Returns:** 


 A pointer to the var or list item A.
 


**Returns:** 

**Returns:**

 A pointer to the var or list item A.


 Sometimes it is desirable to have easy access to a var without knowing its
name, or send multiple items back from a proc. To do this, you can create a
pointer to that var. Then you can use the
 
 \*
 
 operator to refer to the
value inside the pointer, or even to assign a value to it.




 \*


 This operator is also called the reference operator,
since it creates a reference to a var that you can use elsewhere.)



### 
 Example:



 var/a=3, b=4
var/p = &a
world << \*p // same as world << a
\*p = 5 // same as a = 5

var/list/L = list(1, 2, 3)
var/list/pl = &L[2]
\*pl \*= 10 // same as L[2] \*= 10


 If you want the compiler to recognize that the item in your pointer var
should be a certain type, you can give the pointer var that same type. Hence
in the example above,
 
 pl
 
 is defined as a
 
 /list
 
 .




 pl


 /list


 You can also call procs this way. You can either wrap the pointer and the
 
 \*
 
 operator in paretheses, like
 
 (\*p).MyProc()
 
 , or you can
skip the operator and just call
 
 p.MyProc()
 
 directly.




 \*


 (\*p).MyProc()


 p.MyProc()


 The same also applies to the list index operator
 
 []
 
 . If
 
 p = &list
 
 then you can use
 
 (\*p)[index]
 
 or
 
 p[index]
 
 interchangeably.




 []


 p = &list


 (\*p)[index]


 p[index]


 Pointers can be made for any of these kinds of vars:



* Vars belonging to an object
* Local vars in a proc, including
 
 src
 
 ,
 
 usr
 
 , and the
 
 .
 
 var
* Arguments in a proc
* Global vars
* An item in a list, including values in
 [associative lists](#/list/associations)


- Vars belonging to an object

- Local vars in a proc, including
 
 src
 
 ,
 
 usr
 
 , and the
 
 .
 
 var


 src


 usr


 .

- Arguments in a proc

- Global vars

- An item in a list, including values in
 [associative lists](#/list/associations)

[associative lists](#/list/associations)

 One advantage of pointers is that you can use them to alter a value in a
suspended (sleeping) proc.





---



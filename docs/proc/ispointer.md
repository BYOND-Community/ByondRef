

 ispointer proc
----------------




**See also:** 


[\* operator (pointers)](#/operator/*) 

[& operator (pointers)](#/operator/&) 




**See also:** 

**See also:**

[\* operator (pointers)](#/operator/*) 

[& operator (pointers)](#/operator/&) 


[\* operator (pointers)](#/operator/*)

[& operator (pointers)](#/operator/&) 

[& operator (pointers)](#/operator/&)


**Format:** 


 ispointer(Value)
 


**Format:** 

**Format:**

 ispointer(Value)



**Args:** 


 Value: The value to test
 


**Args:** 

**Args:**

 Value: The value to test



**Returns:** 


 1 if the value is a pointer; 0 otherwise.
 


**Returns:** 

**Returns:**

 1 if the value is a pointer; 0 otherwise.


 Tests whether an value is a pointer.




 Note: This does not check if the pointer is still valid, like for instance
if the object it belongs to has been deleted, or if it points to a list index
that is now out of bounds.





---



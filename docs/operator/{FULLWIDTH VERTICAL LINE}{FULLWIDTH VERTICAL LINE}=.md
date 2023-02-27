

 ||= operator
--------------




**See also:** 


[|| operator](#/operator/||) 

[&& operator](#/operator/&&) 

[&&= operator](#/operator/&&=) 

[operators](#/operator) 






**See also:** 

**See also:**

[|| operator](#/operator/||) 

[&& operator](#/operator/&&) 

[&&= operator](#/operator/&&=) 

[operators](#/operator) 




[|| operator](#/operator/||)

[&& operator](#/operator/&&) 

[&&= operator](#/operator/&&=) 

[operators](#/operator) 



[&& operator](#/operator/&&)

[&&= operator](#/operator/&&=) 

[operators](#/operator) 


[&&= operator](#/operator/&&=)

[operators](#/operator) 

[operators](#/operator)


**Format:** 


 A ||= B
 


**Format:** 

**Format:**

 A ||= B



**Returns:** 


 Value of
 
 (A || B)
 
 after it has been assigned to A. This
expression can stand by itself; its result does not need to be assigned to
anything else.
 


**Returns:** 

**Returns:**

 Value of
 
 (A || B)
 
 after it has been assigned to A. This
expression can stand by itself; its result does not need to be assigned to
anything else.


 (A || B)


 First A is evaluated. If its value is false, B will be evaluated and
assigned to A. If A is true, B will not be evaluated and A will remain
unchanged.




 Note that this is slightly different from
 
 if(!A) A = B
 
 if A is
a complex expression such as
 
 list[index++]
 
 , because the expression
is only evaluated once.




 if(!A) A = B


 list[index++]


 This operator cannot be overloaded.





---



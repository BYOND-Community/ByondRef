

 : operator
------------




**See also:** 


[. operator](#/operator/%2e) 

[?. operator](#/operator/%3f%2e) 

[?: operator](#/operator/%3f:) 

[: path operator](#/operator/path/:) 

[operators](#/operator) 







**See also:** 

**See also:**

[. operator](#/operator/%2e) 

[?. operator](#/operator/%3f%2e) 

[?: operator](#/operator/%3f:) 

[: path operator](#/operator/path/:) 

[operators](#/operator) 





[. operator](#/operator/%2e)

[?. operator](#/operator/%3f%2e) 

[?: operator](#/operator/%3f:) 

[: path operator](#/operator/path/:) 

[operators](#/operator) 




[?. operator](#/operator/%3f%2e)

[?: operator](#/operator/%3f:) 

[: path operator](#/operator/path/:) 

[operators](#/operator) 



[?: operator](#/operator/%3f:)

[: path operator](#/operator/path/:) 

[operators](#/operator) 


[: path operator](#/operator/path/:)

[operators](#/operator) 

[operators](#/operator)

 This is the runtime search operator. It is used to access a property (var
or proc) of a var that is not explicitly prototyped. If the variable doesn't
have the specified variable or proc, a runtime error occurs.



### 
 Example:



 var/M
M = usr
M:name = "futz" // access a mob property from a non-mob var


 The
 
 .
 
 operator behaves the same way, but it checks at compile time
whether the property is available. If the var is assigned a value that isn't
the correct type and doesn't have this property, a runtime error will still
occur.




 .


 Note: You should prefer the
 
 .
 
 operator in most
situations, because it's better to catch a problem in the compiler instead of
at runtime.




 .



---





 #if directive
---------------




**See also:** 


[#define directive](#/DM/preprocessor/define) 

[#ifdef directive](#/DM/preprocessor/ifdef) 




**See also:** 

**See also:**

[#define directive](#/DM/preprocessor/define) 

[#ifdef directive](#/DM/preprocessor/ifdef) 


[#define directive](#/DM/preprocessor/define)

[#ifdef directive](#/DM/preprocessor/ifdef) 

[#ifdef directive](#/DM/preprocessor/ifdef)


**Format:** 


 #if Val
 
 ...
 
 #elif Val2
 
 ...
 
 #else
 
 ...
 
 #endif
 








**Format:** 

**Format:**

 #if Val
 
 ...
 
 #elif Val2
 
 ...
 
 #else
 
 ...
 
 #endif
 







 ...
 
 #elif Val2
 
 ...
 
 #else
 
 ...
 
 #endif
 






 #elif Val2
 
 ...
 
 #else
 
 ...
 
 #endif
 





 ...
 
 #else
 
 ...
 
 #endif
 




 #else
 
 ...
 
 #endif
 



 ...
 
 #endif
 


 #endif



**Args:** 


 Val: A logical expression.
 


**Args:** 

**Args:**

 Val: A logical expression.


 The
 `#if` 
 statement is used to conditionally compile code. If
Val is true (non-zero), the code following the
 `#if` 
 statement
will be compiled. Otherwise, compilation skips to the next
 `#elif` 
 ,
 `#else` 
 , or
 `#endif` 
 statement.



`#if`
`#if`
`#elif`
`#else`
`#endif`

 The function
 `defined()` 
 can be used in the conditional
expression. It is true if its argument is a defined macro (with
 `#define` 
 ) and false otherwise.



`defined()`
`#define`
### 
 Example:



 #if defined(DEBUG)
// This code will be compiled if DEBUG is
// defined
#else
// This code will be compiled if DEBUG is
// not defined
#endif



---



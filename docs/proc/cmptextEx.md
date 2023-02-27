

 cmptextEx proc
----------------




**See also:** 


[cmptext proc](#/proc/cmptext) 



**See also:** 

**See also:**

[cmptext proc](#/proc/cmptext) 

[cmptext proc](#/proc/cmptext)


**Format:** 


 cmptextEx(T1,T2,...)
 


**Format:** 

**Format:**

 cmptextEx(T1,T2,...)



**Returns:** 


 1 if all arguments are equal; 0 otherwise.
 


**Returns:** 

**Returns:**

 1 if all arguments are equal; 0 otherwise.



**Args:** 


 Any number of text strings to compare.
 


**Args:** 

**Args:**

 Any number of text strings to compare.


 This instruction is sensitive to case. The case-insensitive version is
cmptext().




 Because identical text is internally combined to conserve memory,
cmptextEx(T1,T2) is equivalent to (T1 == T2).



### 
 Example:



 if(cmptextEx("Hi","HI"))
 world << "Equal!"
else
 world << "Not equal!"


 This outputs "Not equal!" since "Hi" and "HI" are different when taking
case into account.




 Note: This proc used to be named cmpText, like cmptext
but with a capital T. To avoid confusion it has been renamed, but old code
will still compile.





---



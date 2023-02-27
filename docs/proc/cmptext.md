

 cmptext proc
--------------




**See also:** 


[cmptextEx proc](#/proc/cmptextEx) 



**See also:** 

**See also:**

[cmptextEx proc](#/proc/cmptextEx) 

[cmptextEx proc](#/proc/cmptextEx)


**Format:** 


 cmptext(T1,T2,...)
 


**Format:** 

**Format:**

 cmptext(T1,T2,...)



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


 This instruction is NOT sensitive to case. It also ignores the
 `\proper` 
 and
 `\improper` 
 text macros. The
case-sensitive version is cmptextEx().



`\proper`
`\improper`
### 
 Example:



 if(cmptext("Hi","HI"))
 world << "Equal!"
else
 world << "Not equal!"


 This outputs "Equal!" since "Hi" and "HI" are the same, ignoring case.





---



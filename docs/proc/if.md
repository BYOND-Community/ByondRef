

 if proc
---------




**See also:** 


[goto proc](#/proc/goto) 



**See also:** 

**See also:**

[goto proc](#/proc/goto) 

[goto proc](#/proc/goto)


**Format:** 


 if( E ) Statement1
 
 else if( E2 ) Statement2
 
 else Statement3
 




**Format:** 

**Format:**

 if( E ) Statement1
 
 else if( E2 ) Statement2
 
 else Statement3
 



 else if( E2 ) Statement2
 
 else Statement3
 


 else Statement3


 If the expression E is true (non-zero) then execute Statement1.
Otherwise, test E2, etc. Finally, if none of the expressions are true,
execute Statement3. The else nodes are all optional.




 Statement1, Statement2, and Statement3 may be a single statement or a
code block with optional braces: {}.



### 
 Example:



 if(T==1) world << "TRUE"
else world << "FALSE"


 This will display "TRUE" if T has value 1, and "FALSE" otherwise.





---



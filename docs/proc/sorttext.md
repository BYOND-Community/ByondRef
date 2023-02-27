

 sorttext proc
---------------




**See also:** 


[> operator](#/operator/%3e) 

[< operator](#/operator/%3c) 

[sorttextEx proc](#/proc/sorttextEx) 





**See also:** 

**See also:**

[> operator](#/operator/%3e) 

[< operator](#/operator/%3c) 

[sorttextEx proc](#/proc/sorttextEx) 



[> operator](#/operator/%3e)

[< operator](#/operator/%3c) 

[sorttextEx proc](#/proc/sorttextEx) 


[< operator](#/operator/%3c)

[sorttextEx proc](#/proc/sorttextEx) 

[sorttextEx proc](#/proc/sorttextEx)


**Format:** 


 sorttext(T1,T2,...)
 


**Format:** 

**Format:**

 sorttext(T1,T2,...)



**Args:** 


 Any number of text strings to sort.
 


**Args:** 

**Args:**

 Any number of text strings to sort.



**Returns:** 


 1 if text is ascending
 
 -1 if text is descending
 
 0 otherwise
 




**Returns:** 

**Returns:**

 1 if text is ascending
 
 -1 if text is descending
 
 0 otherwise
 



 -1 if text is descending
 
 0 otherwise
 


 0 otherwise


 This instruction is NOT sensitive to case. The case sensitive version is
sorttextEx().



### 
 Example:



 switch(sorttext("A","B"))
 if(1) world << "ascending"
 if(-1)world << "descending"
 if(0) world << "neither"


 This outputs "ascending", since "A" comes before "B" in the alphabet.





---



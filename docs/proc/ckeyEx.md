

 ckeyEx proc
-------------




**See also:** 


[ckey proc](#/proc/ckey) 



**See also:** 

**See also:**

[ckey proc](#/proc/ckey) 

[ckey proc](#/proc/ckey)


**Format:** 


 ckeyEx(Text)
 


**Format:** 

**Format:**

 ckeyEx(Text)



**Args:** 


 Text: The text string to convert to case-sensitive canonical key form.
 


**Args:** 

**Args:**

 Text: The text string to convert to case-sensitive canonical key form.



**Returns:** 


 The same text stripped of all punctuation and space. Unlike, ckey(),
 case is preserved as are the '-' and '\_' characters.
 


**Returns:** 

**Returns:**

 The same text stripped of all punctuation and space. Unlike, ckey(),
 case is preserved as are the '-' and '\_' characters.


 The true canonical form of a key is in all lowercase, but occasionally,
it is nice to preserve case when stripping a key (or other text) of any
special characters.




 Note: This proc used to be named
 
 cKey
 
 , like
 
 ckey
 
 but with a capital k. To avoid confusion it has been renamed,
but old code will still compile with a warning.




 cKey


 ckey



---



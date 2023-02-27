

 findtextEx proc
-----------------




**See also:** 


[findtext proc](#/proc/findtext) 

[replacetextEx proc](#/proc/replacetextEx) 

[Regular expressions](#/{notes}/regex) 





**See also:** 

**See also:**

[findtext proc](#/proc/findtext) 

[replacetextEx proc](#/proc/replacetextEx) 

[Regular expressions](#/{notes}/regex) 



[findtext proc](#/proc/findtext)

[replacetextEx proc](#/proc/replacetextEx) 

[Regular expressions](#/{notes}/regex) 


[replacetextEx proc](#/proc/replacetextEx)

[Regular expressions](#/{notes}/regex) 

[Regular expressions](#/{notes}/regex)


**Format:** 


 findtextEx(Haystack,Needle,Start=1,End=0)
 


**Format:** 

**Format:**

 findtextEx(Haystack,Needle,Start=1,End=0)



**Returns:** 


 The position of Needle in Haystack; 0 if not found.
 


**Returns:** 

**Returns:**

 The position of Needle in Haystack; 0 if not found.



**Args:** 


 Haystack: The text string to search.
 
 Needle: The sub-text to search for. May be a regular expression (regex).
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 





**Args:** 

**Args:**

 Haystack: The text string to search.
 
 Needle: The sub-text to search for. May be a regular expression (regex).
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 




 Needle: The sub-text to search for. May be a regular expression (regex).
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 



 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 


 End: The text byte position in Haystack immediately following the last
 character to search.


 When Needle is text, this instruction is sensitive to the case of Haystack
and Needle. The case-insensitive version is findtext().



### 
 Example:



 if(findtextEx("Hi There","there")==0)
 world << "Not found!"
else
 world << "Found!"


 This outputs "Not found!", since "there" is not a part of the string "Hi
There", taking into account case.




 If the start or end position is negative, the position is counted backwards
from the end of the string. E.g., findtextEx("Banana", "na", -3) starts three
characters from the end and only searches the final "ana".




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 findtextEx\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 findtextEx\_char()

[Unicode](#/{notes}/Unicode)

 Note: This proc used to be named
 
 findText
 
 ,
like
 
 findtext
 
 but with a capital T. To avoid confusion it has been
renamed, but old code will still compile.




 findText


 findtext



---



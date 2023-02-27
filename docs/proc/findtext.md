

 findtext proc
---------------




**See also:** 


[findlasttext proc](#/proc/findlasttext) 

[findtextEx proc](#/proc/findtextEx) 

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 






**See also:** 

**See also:**

[findlasttext proc](#/proc/findlasttext) 

[findtextEx proc](#/proc/findtextEx) 

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 




[findlasttext proc](#/proc/findlasttext)

[findtextEx proc](#/proc/findtextEx) 

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 



[findtextEx proc](#/proc/findtextEx)

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 


[replacetext proc](#/proc/replacetext)

[Regular expressions](#/{notes}/regex) 

[Regular expressions](#/{notes}/regex)


**Format:** 


 findtext(Haystack,Needle,Start=1,End=0)
 


**Format:** 

**Format:**

 findtext(Haystack,Needle,Start=1,End=0)



**Returns:** 


 The first position of Needle in Haystack; 0 if not found.
 


**Returns:** 

**Returns:**

 The first position of Needle in Haystack; 0 if not found.



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


 When Needle is text, this instruction is NOT sensitive to the case of
Haystack or Needle. The case-sensitive version is findtextEx().



### 
 Example:



 if(findtext("Hi There","there")==0)
 world << "Not found!"
else
 world << "Found!"


 This outputs "Found!", since "there" is a part of the string "Hi There",
ignoring case.




 If the start or end position is negative, the position is counted backwards
from the end of the string. E.g., findtext("Banana", "na", -3) starts three
characters from the end and only searches the final "ana".




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 findtext\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 findtext\_char()

[Unicode](#/{notes}/Unicode)


---



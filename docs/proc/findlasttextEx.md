

 findlasttextEx proc
---------------------




**See also:** 


[findtext proc](#/proc/findtext) 

[findtextEx proc](#/proc/findtextEx) 

[findlasttext proc](#/proc/findlasttext) 





**See also:** 

**See also:**

[findtext proc](#/proc/findtext) 

[findtextEx proc](#/proc/findtextEx) 

[findlasttext proc](#/proc/findlasttext) 



[findtext proc](#/proc/findtext)

[findtextEx proc](#/proc/findtextEx) 

[findlasttext proc](#/proc/findlasttext) 


[findtextEx proc](#/proc/findtextEx)

[findlasttext proc](#/proc/findlasttext) 

[findlasttext proc](#/proc/findlasttext)


**Format:** 


 findlasttextEx(Haystack,Needle,Start=0,End=1)
 


**Format:** 

**Format:**

 findlasttextEx(Haystack,Needle,Start=0,End=1)



**Returns:** 


 The last position of Needle in Haystack; 0 if not found.
 


**Returns:** 

**Returns:**

 The last position of Needle in Haystack; 0 if not found.



**Args:** 


 Haystack: The text string to search.
 
 Needle: The sub-text to search for.
 
 Start: The text byte position in Haystack in which to begin the search.
 Because this searches backwards, the default is the end of the string (0).
 
 End: The earliest position in Haystack that can be matched as a result.
 





**Args:** 

**Args:**

 Haystack: The text string to search.
 
 Needle: The sub-text to search for.
 
 Start: The text byte position in Haystack in which to begin the search.
 Because this searches backwards, the default is the end of the string (0).
 
 End: The earliest position in Haystack that can be matched as a result.
 




 Needle: The sub-text to search for.
 
 Start: The text byte position in Haystack in which to begin the search.
 Because this searches backwards, the default is the end of the string (0).
 
 End: The earliest position in Haystack that can be matched as a result.
 



 Start: The text byte position in Haystack in which to begin the search.
 Because this searches backwards, the default is the end of the string (0).
 
 End: The earliest position in Haystack that can be matched as a result.
 


 End: The earliest position in Haystack that can be matched as a result.


 This instruction is sensitive to the case of Haystack and Needle. The
case-insensitive version is findlasttext().




 If the start or end position is negative, the position is counted backwards
from the end of the string.




 Note: Unlike findtextEx(), a regular expression may NOT be used as the
Needle. Searching backwards is simply too complex for the regular expression
engine.




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 findlasttextEx\_char()
 
 to work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 findlasttextEx\_char()

[Unicode](#/{notes}/Unicode)


---



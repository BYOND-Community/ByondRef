

 findlasttext proc
-------------------




**See also:** 


[findtext proc](#/proc/findtext) 

[findtextEx proc](#/proc/findtextEx) 

[findlasttextEx proc](#/proc/findlasttextEx) 





**See also:** 

**See also:**

[findtext proc](#/proc/findtext) 

[findtextEx proc](#/proc/findtextEx) 

[findlasttextEx proc](#/proc/findlasttextEx) 



[findtext proc](#/proc/findtext)

[findtextEx proc](#/proc/findtextEx) 

[findlasttextEx proc](#/proc/findlasttextEx) 


[findtextEx proc](#/proc/findtextEx)

[findlasttextEx proc](#/proc/findlasttextEx) 

[findlasttextEx proc](#/proc/findlasttextEx)


**Format:** 


 findlasttext(Haystack,Needle,Start=0,End=1)
 


**Format:** 

**Format:**

 findlasttext(Haystack,Needle,Start=0,End=1)



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


 This instruction is NOT sensitive to the case of Haystack or Needle. The
case-sensitive version is findlasttextEx().




 If the start or end position is negative, the position is counted backwards
from the end of the string. E.g., findlasttext("Banana", "na", -3) starts three
characters from the end and will skip over the last "na".




 Note: Unlike findtext(), a regular expression may NOT be used as the
Needle. Searching backwards is simply too complex for the regular expression
engine.




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 findlasttext\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 findlasttext\_char()

[Unicode](#/{notes}/Unicode)


---



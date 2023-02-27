

 nonspantext proc
------------------




**See also:** 


[findtext proc](#/proc/findtext) 

[spantext proc](#/proc/spantext) 

[splittext proc](#/proc/splittext) 





**See also:** 

**See also:**

[findtext proc](#/proc/findtext) 

[spantext proc](#/proc/spantext) 

[splittext proc](#/proc/splittext) 



[findtext proc](#/proc/findtext)

[spantext proc](#/proc/spantext) 

[splittext proc](#/proc/splittext) 


[spantext proc](#/proc/spantext)

[splittext proc](#/proc/splittext) 

[splittext proc](#/proc/splittext)


**Format:** 


 nonspantext(Haystack,Needles,Start=1)
 


**Format:** 

**Format:**

 nonspantext(Haystack,Needles,Start=1)



**Returns:** 


 The number of consecutive characters, from the start position, that do NOT match the characters in Needles.
 


**Returns:** 

**Returns:**

 The number of consecutive characters, from the start position, that do NOT match the characters in Needles.



**Args:** 


 Haystack: The text string to search.
 
 Needles: A text string with all the characters that should not match.
 
 Start: The text byte position in Haystack in which to begin the search.
 




**Args:** 

**Args:**

 Haystack: The text string to search.
 
 Needles: A text string with all the characters that should not match.
 
 Start: The text byte position in Haystack in which to begin the search.
 



 Needles: A text string with all the characters that should not match.
 
 Start: The text byte position in Haystack in which to begin the search.
 


 Start: The text byte position in Haystack in which to begin the search.


 This proc is case-sensitive. A common use for this proc is in parsing.
For instance nonspantext("apples, oranges",", ") will return 6, because the
first 6 characters don't match a comma or a space.




 If the start position is negative, the position is counted backwards from
the end of the string.




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 nonspantext\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 nonspantext\_char()

[Unicode](#/{notes}/Unicode)


---



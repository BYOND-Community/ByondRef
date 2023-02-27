

 spantext proc
---------------




**See also:** 


[findtext proc](#/proc/findtext) 

[nonspantext proc](#/proc/nonspantext) 

[splittext proc](#/proc/splittext) 





**See also:** 

**See also:**

[findtext proc](#/proc/findtext) 

[nonspantext proc](#/proc/nonspantext) 

[splittext proc](#/proc/splittext) 



[findtext proc](#/proc/findtext)

[nonspantext proc](#/proc/nonspantext) 

[splittext proc](#/proc/splittext) 


[nonspantext proc](#/proc/nonspantext)

[splittext proc](#/proc/splittext) 

[splittext proc](#/proc/splittext)


**Format:** 


 spantext(Haystack,Needles,Start=1)
 


**Format:** 

**Format:**

 spantext(Haystack,Needles,Start=1)



**Returns:** 


 The number of consecutive characters, from the start position, that match the characters in Needles.
 


**Returns:** 

**Returns:**

 The number of consecutive characters, from the start position, that match the characters in Needles.



**Args:** 


 Haystack: The text string to search.
 
 Needles: A text string with all the characters that match.
 
 Start: The text byte position in Haystack in which to begin the search.
 




**Args:** 

**Args:**

 Haystack: The text string to search.
 
 Needles: A text string with all the characters that match.
 
 Start: The text byte position in Haystack in which to begin the search.
 



 Needles: A text string with all the characters that match.
 
 Start: The text byte position in Haystack in which to begin the search.
 


 Start: The text byte position in Haystack in which to begin the search.


 This proc is case-sensitive. A common use for this proc is in parsing.
spantext("apples, oranges",", ",7) will tell you that, starting at position 7,
you need to skip 2 characters to get past any commas or spaces.




 If the start position is negative, the position is counted backwards from
the end of the string.




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 spantext\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 spantext\_char()

[Unicode](#/{notes}/Unicode)


---



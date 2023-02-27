

 Find proc (regex)
-------------------




**See also:** 


[Regular expressions](#/{notes}/regex) 

[regex datum](#/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 

[regex vars](#/regex/var) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 








**See also:** 

**See also:**

[Regular expressions](#/{notes}/regex) 

[regex datum](#/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 

[regex vars](#/regex/var) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 






[Regular expressions](#/{notes}/regex)

[regex datum](#/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 

[regex vars](#/regex/var) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 





[regex datum](#/regex)

[Replace proc (regex)](#/regex/proc/Replace) 

[regex vars](#/regex/var) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 




[Replace proc (regex)](#/regex/proc/Replace)

[regex vars](#/regex/var) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 



[regex vars](#/regex/var)

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 


[regex proc](#/proc/regex)

[findtext proc](#/proc/findtext) 

[findtext proc](#/proc/findtext)


**Format:** 


 Find(haystack, Start=1, End=0)
 


**Format:** 

**Format:**

 Find(haystack, Start=1, End=0)



**Returns:** 


 The position of the matched text, or 0 if no match was found.
 


**Returns:** 

**Returns:**

 The position of the matched text, or 0 if no match was found.



**Args:** 


 haystack: The text to be searched
 
 Start: The start position (in bytes) to search; defaults to 1, or to src.next if this is a global pattern
 
 End: The position of the byte after the end of the search; 0 is the end. The actual match is allowed to extend past End.
 




**Args:** 

**Args:**

 haystack: The text to be searched
 
 Start: The start position (in bytes) to search; defaults to 1, or to src.next if this is a global pattern
 
 End: The position of the byte after the end of the search; 0 is the end. The actual match is allowed to extend past End.
 



 Start: The start position (in bytes) to search; defaults to 1, or to src.next if this is a global pattern
 
 End: The position of the byte after the end of the search; 0 is the end. The actual match is allowed to extend past End.
 


 End: The position of the byte after the end of the search; 0 is the end. The actual match is allowed to extend past End.


 Finds the regular expression pattern within the "haystack" text. The
following vars are set by the match:



* text: The text that was searched.
* index: The index where the match was found (same as the return value)
* match: The actual matched text
* group: If the expression contains capturing groups with the ( ) parentheses operator, this is a list that holds the text found in those groups. group[1] is the first group, and so on.
* next: If the "g" flag was used to create thie expression, this is the next index to begin searching.


- text: The text that was searched.

- index: The index where the match was found (same as the return value)

- match: The actual matched text

- group: If the expression contains capturing groups with the ( ) parentheses operator, this is a list that holds the text found in those groups. group[1] is the first group, and so on.

- next: If the "g" flag was used to create thie expression, this is the next index to begin searching.


 In a global expression (using the "g" flag), Find() can be called
repeatedly on the same piece of text and the Start position will be advanced
automatically unless you specify it.




 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 Find\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](@/{notes}/Unicode) 
 section for more information.




 Find\_char()

[Unicode](@/{notes}/Unicode)


---



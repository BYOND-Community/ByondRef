

 replacetextEx proc
--------------------




**See also:** 


[findtextEx proc](#/proc/findtextEx) 

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 






**See also:** 

**See also:**

[findtextEx proc](#/proc/findtextEx) 

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 




[findtextEx proc](#/proc/findtextEx)

[replacetext proc](#/proc/replacetext) 

[Regular expressions](#/{notes}/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 



[replacetext proc](#/proc/replacetext)

[Regular expressions](#/{notes}/regex) 

[Replace proc (regex)](#/regex/proc/Replace) 


[Regular expressions](#/{notes}/regex)

[Replace proc (regex)](#/regex/proc/Replace) 

[Replace proc (regex)](#/regex/proc/Replace)


**Format:** 


 replacetextEx(Haystack,Needle,Replacement,Start=1,End=0)
 


**Format:** 

**Format:**

 replacetextEx(Haystack,Needle,Replacement,Start=1,End=0)



**Returns:** 


 The Haystack text with all cases of Needle replaced by Replacement
 


**Returns:** 

**Returns:**

 The Haystack text with all cases of Needle replaced by Replacement



**Args:** 


 Haystack: The text string to search.
 
 Needle: The sub-text to search for. May be a regular expression (regex).
 
 Replacement: The replacement text, or a proc.
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 






**Args:** 

**Args:**

 Haystack: The text string to search.
 
 Needle: The sub-text to search for. May be a regular expression (regex).
 
 Replacement: The replacement text, or a proc.
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 





 Needle: The sub-text to search for. May be a regular expression (regex).
 
 Replacement: The replacement text, or a proc.
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 




 Replacement: The replacement text, or a proc.
 
 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 



 Start: The text byte position in Haystack in which to begin the search.
 
 End: The text byte position in Haystack immediately following the last
 character to search.
 


 End: The text byte position in Haystack immediately following the last
 character to search.


 When Needle is text, this instruction is sensitive to the case of Haystack
and Needle. The case-insensitive version is replacetext().



### 
 Example:



 world << replacetext("One on one", "one", "two")


 This outputs "Two on two", where the first case's "One" is identified as
uppercase.




 You may use a proc as the Replacement value. In that case, the proc will
be called with the found text as an argument, and its return value will be the
replacement. There will be no automatic correction to uppercase or all caps
in this case.




 When the Needle value is a regular expression, this proc behaves identically
to the
 [regex Replace()](#/regex/proc/Replace) 
 proc. Case-sensitivity,
and whether one match or all are replaced, depend on the regular expression.



[regex Replace()](#/regex/proc/Replace)

 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 replacetextEx\_char()
 
 to work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 replacetextEx\_char()

[Unicode](#/{notes}/Unicode)


---



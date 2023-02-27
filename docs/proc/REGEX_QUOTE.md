

 REGEX\_QUOTE proc
-------------------




**See also:** 


[regex proc](#/proc/regex) 

[regex datum](#/regex) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 





**See also:** 

**See also:**

[regex proc](#/proc/regex) 

[regex datum](#/regex) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 



[regex proc](#/proc/regex)

[regex datum](#/regex) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 


[regex datum](#/regex)

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[stddef.dm file](#/{{appendix}}/stddef%2edm)


**Format:** 


 REGEX\_QUOTE(text)
 
 REGEX\_QUOTE\_REPLACEMENT(text)
 



**Format:** 

**Format:**

 REGEX\_QUOTE(text)
 
 REGEX\_QUOTE\_REPLACEMENT(text)
 


 REGEX\_QUOTE\_REPLACEMENT(text)



**Returns:** 


 REGEX\_QUOTE: A version of the text with any special regular expression characters escaped by backslashes.
 
 REGEX\_QUOTE\_REPLACEMENT: A version of the text with $ characters escaped by a second $.
 



**Returns:** 

**Returns:**

 REGEX\_QUOTE: A version of the text with any special regular expression characters escaped by backslashes.
 
 REGEX\_QUOTE\_REPLACEMENT: A version of the text with $ characters escaped by a second $.
 


 REGEX\_QUOTE\_REPLACEMENT: A version of the text with $ characters escaped by a second $.



**Args:** 


 text: The text to escape
 


**Args:** 

**Args:**

 text: The text to escape


 Quotes a piece of text so that it can be used inside a regular expression
without fear of being treated as pattern instructions.



### 
 Example:



 proc/FindWord(text, word)
 // The \b pattern is a word break, to search for the word
 // on its own instead of as part of another word.
 var/regex/R = regex("\\b[REGEX\_QUOTE(word)]\b", "i")
 // find the pattern in the text
 return R.Find(text)



---



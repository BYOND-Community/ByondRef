

 ascii2text proc
-----------------




**See also:** 


[entities (text)](#/DM/text/entities) 

[text2ascii proc](#/proc/text2ascii) 




**See also:** 

**See also:**

[entities (text)](#/DM/text/entities) 

[text2ascii proc](#/proc/text2ascii) 


[entities (text)](#/DM/text/entities)

[text2ascii proc](#/proc/text2ascii) 

[text2ascii proc](#/proc/text2ascii)


**Format:** 


 ascii2text(N)
 


**Format:** 

**Format:**

 ascii2text(N)



**Returns:** 


 A text string.
 


**Returns:** 

**Returns:**

 A text string.



**Args:** 


 N: A number.
 


**Args:** 

**Args:**

 N: A number.


 ASCII codes are numerical values corresponding to keyboard and special
characters. Among other things, they are used to represent many symbols in
HTML. This proc converts an ASCII code to its corresponding text
representation.



### 
 Example:



 T = ascii2text(65) // = "A"


 BYOND now supports
 [Unicode](#/{notes}/Unicode) 
 via UTF-8
encoding, so you can use the character code for any valid Unicode
character, not just ASCII.



[Unicode](#/{notes}/Unicode)


---





 text2ascii proc
-----------------




**See also:** 


[ascii2text proc](#/proc/ascii2text) 

[entities (text)](#/DM/text/entities) 

[Unicode](#/{notes}/Unicode) 





**See also:** 

**See also:**

[ascii2text proc](#/proc/ascii2text) 

[entities (text)](#/DM/text/entities) 

[Unicode](#/{notes}/Unicode) 



[ascii2text proc](#/proc/ascii2text)

[entities (text)](#/DM/text/entities) 

[Unicode](#/{notes}/Unicode) 


[entities (text)](#/DM/text/entities)

[Unicode](#/{notes}/Unicode) 

[Unicode](#/{notes}/Unicode)


**Format:** 


 text2ascii(T,pos=1)
 


**Format:** 

**Format:**

 text2ascii(T,pos=1)



**Args:** 


 T: A text string.
 
 pos: The byte position in T to use, starting at 1.
 



**Args:** 

**Args:**

 T: A text string.
 
 pos: The byte position in T to use, starting at 1.
 


 pos: The byte position in T to use, starting at 1.



**Returns:** 


 A number representing the character's ASCII or Unicode code.
 


**Returns:** 

**Returns:**

 A number representing the character's ASCII or Unicode code.


 ASCII codes are numerical values corresponding to keyboard and special
characters. Among other things, they are used to represent many symbols in
HTML. This proc converts a text string to its corresponding ascii
representation.



### 
 Example:



 world << text2ascii("A") // = 65
world << text2ascii("HAPPY",2) // = 65


 With
 [Unicode](#/{notes}/Unicode) 
 , things may get more
complicated. DM stores text with UTF-8 encoding, so at this position there
might be several bytes strung together to make a single character. The value
of
 
 pos
 
 is in bytes, not characters. When the return value is 128
(0x80) or higher, multiple bytes are used for the charcter. In that case the
next character position is not
 
 pos + 1
 
 like it is for regular text,
but you can use
 
 pos + length(ascii2text(result))
 
 instead. Or, you
can determine the byte count from this table:



[Unicode](#/{notes}/Unicode)

 pos


 pos + 1


 pos + length(ascii2text(result))



| 
 Character code
  | 
 Size in bytes
  |
| --- | --- |
| 
 0 - 0x7F
  | 
 1
  |
| 
 0x80 - 0x7FF
  | 
 2
  |
| 
 0x800 - 0xFFFF
  | 
 3
  |
| 
 0x10000 - 0x10FFFF
  | 
 4
  |


| 
 Character code
  | 
 Size in bytes
  |

 
 Character code
 |
 
 Size in bytes
 |
| 
 0 - 0x7F
  | 
 1
  |

 
 0 - 0x7F
 |
 
 1
 |
| 
 0x80 - 0x7FF
  | 
 2
  |

 
 0x80 - 0x7FF
 |
 
 2
 |
| 
 0x800 - 0xFFFF
  | 
 3
  |

 
 0x800 - 0xFFFF
 |
 
 3
 |
| 
 0x10000 - 0x10FFFF
  | 
 4
  |

 
 0x10000 - 0x10FFFF
 |
 
 4
 |

 Alternatively, you can use
 
 test2ascii\_char()
 
 to work with
character positions instead of bytes, at a performance cost.




 test2ascii\_char()



---



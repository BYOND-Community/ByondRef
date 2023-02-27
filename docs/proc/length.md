

 length proc
-------------




**Format:** 


 length(E)
 


**Format:** 

**Format:**

 length(E)



**Returns:** 


 The length of the data associated with E.
 


**Returns:** 

**Returns:**

 The length of the data associated with E.



**Args:** 


 E: a text, list, or file
 


**Args:** 

**Args:**

 E: a text, list, or file

### 
 Example:



 world << length("Hi")


 This outputs, "2", the length of the string "Hi".



### 
 Example:



 world << length(list(1,2,3))


 This outputs, "3", the length of the list.



### 
 Example:



 world << length(file("test.txt"))


 This outputs the length of the file.




 Note: In strings containing non-ASCII characters, this is the length in
bytes, not characters; a character may span multiple bytes. Use
 
 length\_char()
 
 to work with character counts instead of bytes. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 length\_char()

[Unicode](#/{notes}/Unicode)


---



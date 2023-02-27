

 copytext proc
---------------




**See also:** 


[splicetext proc](#/proc/splicetext) 

[findtext proc](#/proc/findtext) 

[splittext proc](#/proc/splittext) 

[trimtext proc](#/proc/trimtext) 

[Copy proc (list)](#/list/proc/Copy) 







**See also:** 

**See also:**

[splicetext proc](#/proc/splicetext) 

[findtext proc](#/proc/findtext) 

[splittext proc](#/proc/splittext) 

[trimtext proc](#/proc/trimtext) 

[Copy proc (list)](#/list/proc/Copy) 





[splicetext proc](#/proc/splicetext)

[findtext proc](#/proc/findtext) 

[splittext proc](#/proc/splittext) 

[trimtext proc](#/proc/trimtext) 

[Copy proc (list)](#/list/proc/Copy) 




[findtext proc](#/proc/findtext)

[splittext proc](#/proc/splittext) 

[trimtext proc](#/proc/trimtext) 

[Copy proc (list)](#/list/proc/Copy) 



[splittext proc](#/proc/splittext)

[trimtext proc](#/proc/trimtext) 

[Copy proc (list)](#/list/proc/Copy) 


[trimtext proc](#/proc/trimtext)

[Copy proc (list)](#/list/proc/Copy) 

[Copy proc (list)](#/list/proc/Copy)


**Format:** 


 copytext(T,Start=1,End=0)
 


**Format:** 

**Format:**

 copytext(T,Start=1,End=0)



**Returns:** 


 A text string.
 


**Returns:** 

**Returns:**

 A text string.



**Args:** 


 T: A text string.
 
 Start: The text byte position in which to begin the copy.
 
 End: The text byte position immediately following the last character to be copied.
 




**Args:** 

**Args:**

 T: A text string.
 
 Start: The text byte position in which to begin the copy.
 
 End: The text byte position immediately following the last character to be copied.
 



 Start: The text byte position in which to begin the copy.
 
 End: The text byte position immediately following the last character to be copied.
 


 End: The text byte position immediately following the last character to be copied.


 Copy characters in T between Start and End. The default end position of 0
stands for
 
 length(T)+1
 
 , so by default the entire text string is copied.




 length(T)+1

### 
 Example:



 pre = copytext("Hi there",1,3))// = "Hi"
post = copytext("Hi there",4)) // = "there"


 If the start or end position is negative, it counts backwards from the end
of the string.



### 
 Example:



 post = copytext("Hi there",-5)) // = "there"


 Note: In strings containing non-ASCII characters, byte position and
character position are not the same thing. Use
 
 copytext\_char()
 
 to
work with character counts instead of bytes, at a performance cost. See the
 [Unicode](#/{notes}/Unicode) 
 section for more information.




 copytext\_char()

[Unicode](#/{notes}/Unicode)


---



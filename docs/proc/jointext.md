

 jointext proc
---------------




**See also:** 


[splittext proc](#/proc/splittext) 

[Join proc (list)](#/list/proc/Join) 




**See also:** 

**See also:**

[splittext proc](#/proc/splittext) 

[Join proc (list)](#/list/proc/Join) 


[splittext proc](#/proc/splittext)

[Join proc (list)](#/list/proc/Join) 

[Join proc (list)](#/list/proc/Join)


**Format:** 


 jointext(List,Glue,Start=1,End=0)
 


**Format:** 

**Format:**

 jointext(List,Glue,Start=1,End=0)



**Returns:** 


 A text string made up of the items in List, joined together by Glue.
 


**Returns:** 

**Returns:**

 A text string made up of the items in List, joined together by Glue.



**Args:** 


 List: The list to be joined.
 
 Glue: The text that will go between each item.
 
 Start: The list item on which to begin.
 
 End: The list item immediately following the last item to be joined.
 
 include\_delimiters: True if any delimiters found should be included in
 the result.
 






**Args:** 

**Args:**

 List: The list to be joined.
 
 Glue: The text that will go between each item.
 
 Start: The list item on which to begin.
 
 End: The list item immediately following the last item to be joined.
 
 include\_delimiters: True if any delimiters found should be included in
 the result.
 





 Glue: The text that will go between each item.
 
 Start: The list item on which to begin.
 
 End: The list item immediately following the last item to be joined.
 
 include\_delimiters: True if any delimiters found should be included in
 the result.
 




 Start: The list item on which to begin.
 
 End: The list item immediately following the last item to be joined.
 
 include\_delimiters: True if any delimiters found should be included in
 the result.
 



 End: The list item immediately following the last item to be joined.
 
 include\_delimiters: True if any delimiters found should be included in
 the result.
 


 include\_delimiters: True if any delimiters found should be included in
 the result.


 Any items in List that are not already text will be converted to text.
The Glue string only goes between two items, so a single-item list is the
same as converting that one item to text, and an empty list becomes an empty
string.



### 
 Example:



 var/list/items = list("apples", "oranges", "bananas")
usr << jointext(items, ", ")


 If the start or end position is negative, the position is counted backwards
from the end of the list.




 Calling List.Join(Glue,Start,End) is the same thing, as long as List is a
valid list.





---



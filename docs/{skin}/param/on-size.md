

 on-size parameter (skin)
--------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 



**See also:** 

**See also:**

[size parameter](#/{skin}/param/size) 

[size parameter](#/{skin}/param/size)


**Applies to:** 


[All](#/{skin}/control) 



**Applies to:** 

**Applies to:**

[All](#/{skin}/control) 

[All](#/{skin}/control)


**Format:** 


 string
 


**Format:** 

**Format:**

 string


[Command](#/{skin}/commands) 
 executed when this control is resized. If you are dragging a window edge or splitter, the command won't run until you finish.



[Command](#/{skin}/commands)

 No command will be sent in response to size or splitter changes made by
 [winset()](#/proc/winset) 
 .



[winset()](#/proc/winset)

 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the control's new size. Likewise,
 
 [[width]]
 
 will be replaced with the width and
 
 [[height]]
 
 with the height. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)




 [[\*]]


 [[width]]


 [[height]]

[client commands](#/{skin}/commands)

 [[...]]



---



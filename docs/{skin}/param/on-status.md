

 on-status parameter (skin)
----------------------------




**See also:** 


[statusbar parameter](#/{skin}/param/statusbar) 



**See also:** 

**See also:**

[statusbar parameter](#/{skin}/param/statusbar) 

[statusbar parameter](#/{skin}/param/statusbar)


**Applies to:** 


[Main](#/{skin}/control/main) 



**Applies to:** 

**Applies to:**

[Main](#/{skin}/control/main) 

[Main](#/{skin}/control/main)


**Format:** 


 string
 


**Format:** 

**Format:**

 string


[Command](#/{skin}/commands) 
 executed when the text that would go in the statusbar is changed. This applies even if this control is a pane and not a window, or is a window without a statusbar. It applies to all panes and windows that directly or indirectly contain whatever control generated the statusbar text (e.g., a map).



[Command](#/{skin}/commands)

 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the new text. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)




 [[\*]]

[client commands](#/{skin}/commands)

 [[...]]



 [[from]]
 
 can be used to reference the control (if any) that generated the next text. You can also use expressions like
 
 [[from.type]]
 
 ,
 
 [[from.parent.pos.x]]
 
 , etc.




 [[from]]


 [[from.type]]


 [[from.parent.pos.x]]



---



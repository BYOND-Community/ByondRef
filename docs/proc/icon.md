

 icon proc
-----------




**See also:** 


[file proc](#/proc/file) 

[icon\_states proc](#/proc/icon_states) 

[icons](#/DM/icon) 





**See also:** 

**See also:**

[file proc](#/proc/file) 

[icon\_states proc](#/proc/icon_states) 

[icons](#/DM/icon) 



[file proc](#/proc/file)

[icon\_states proc](#/proc/icon_states) 

[icons](#/DM/icon) 


[icon\_states proc](#/proc/icon_states)

[icons](#/DM/icon) 

[icons](#/DM/icon)


**Format:** 


 icon(icon,state,dir,frame,moving)
 

 (supports
 [named arguments](#/proc/arguments/named) 
 )
 




**Format:** 

**Format:**

 icon(icon,state,dir,frame,moving)
 

 (supports
 [named arguments](#/proc/arguments/named) 
 )
 




 (supports
 [named arguments](#/proc/arguments/named) 
 )
 


 (supports
 [named arguments](#/proc/arguments/named) 
 )

[named arguments](#/proc/arguments/named)


**Args:** 


 icon: an icon file or /icon object
 
 icon\_state: an optional text string, specifying a single icon state to load
 
 dir: an optional direction to extract
 
 frame: an optional animation frame to extract
 
 moving: Non-zero to extract only movement states, 0 for non-movement states,
 or null (default) for both
 






**Args:** 

**Args:**

 icon: an icon file or /icon object
 
 icon\_state: an optional text string, specifying a single icon state to load
 
 dir: an optional direction to extract
 
 frame: an optional animation frame to extract
 
 moving: Non-zero to extract only movement states, 0 for non-movement states,
 or null (default) for both
 





 icon\_state: an optional text string, specifying a single icon state to load
 
 dir: an optional direction to extract
 
 frame: an optional animation frame to extract
 
 moving: Non-zero to extract only movement states, 0 for non-movement states,
 or null (default) for both
 




 dir: an optional direction to extract
 
 frame: an optional animation frame to extract
 
 moving: Non-zero to extract only movement states, 0 for non-movement states,
 or null (default) for both
 



 frame: an optional animation frame to extract
 
 moving: Non-zero to extract only movement states, 0 for non-movement states,
 or null (default) for both
 


 moving: Non-zero to extract only movement states, 0 for non-movement states,
 or null (default) for both


 This is equivalent to new/icon(). It creates an /icon object, which is
initialized to contain the same graphical data as the given file. If an icon
state or direction are specified, only those parts of the original icon will
be included in the new icon object.





---



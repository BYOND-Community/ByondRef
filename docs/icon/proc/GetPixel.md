

 GetPixel proc (icon)
----------------------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[rgb proc](#/proc/rgb) 





**See also:** 

**See also:**

[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[rgb proc](#/proc/rgb) 



[icon](#/icon)

[procs (icon)](#/icon/proc) 

[rgb proc](#/proc/rgb) 


[procs (icon)](#/icon/proc)

[rgb proc](#/proc/rgb) 

[rgb proc](#/proc/rgb)


**Format:** 


 GetPixel(x, y, icon\_state, dir=0, frame=0, moving=-1)
 


**Format:** 

**Format:**

 GetPixel(x, y, icon\_state, dir=0, frame=0, moving=-1)



**Args:** 


 x,y: coordinates of the pixel to grab; 1,1 is the lower left corner
 
 icon\_state: a specific icon\_state to use (may be null)
 
 dir: a specific direction of this icon to use
 
 frame: a specific animation frame to use (1 is the 1st frame)
 
 moving: non-zero for only movement states, 0 for non-movement states,
 or null (default) for either
 






**Args:** 

**Args:**

 x,y: coordinates of the pixel to grab; 1,1 is the lower left corner
 
 icon\_state: a specific icon\_state to use (may be null)
 
 dir: a specific direction of this icon to use
 
 frame: a specific animation frame to use (1 is the 1st frame)
 
 moving: non-zero for only movement states, 0 for non-movement states,
 or null (default) for either
 





 icon\_state: a specific icon\_state to use (may be null)
 
 dir: a specific direction of this icon to use
 
 frame: a specific animation frame to use (1 is the 1st frame)
 
 moving: non-zero for only movement states, 0 for non-movement states,
 or null (default) for either
 




 dir: a specific direction of this icon to use
 
 frame: a specific animation frame to use (1 is the 1st frame)
 
 moving: non-zero for only movement states, 0 for non-movement states,
 or null (default) for either
 



 frame: a specific animation frame to use (1 is the 1st frame)
 
 moving: non-zero for only movement states, 0 for non-movement states,
 or null (default) for either
 


 moving: non-zero for only movement states, 0 for non-movement states,
 or null (default) for either


 This finds the icon\_state and the right animation/direction frame of your
choosing (it will pick the first one available if you don't specify) and
returns the rgb() value of a pixel at that location, in "#RRGGBB" form.
If the pixel is totally transparent, it returns null. If the pixel is
partially transparent, an alpha component is also returned in "#RRGGBBAA"
form.





---





 SwapColor proc (icon)
-----------------------




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


 SwapColor(old\_rgb,new\_rgb)
   

*or* 
  

 SwapColor(old\_rgba,new\_rgba)
 


**Format:** 

**Format:**

 SwapColor(old\_rgb,new\_rgb)
   

*or* 
  

 SwapColor(old\_rgba,new\_rgba)

  

*or*
  



**Args:** 


 old\_rgba: the old rgba value to be replaced
 
 new\_rgba: the new rgba value to use in its place
 



**Args:** 

**Args:**

 old\_rgba: the old rgba value to be replaced
 
 new\_rgba: the new rgba value to use in its place
 


 new\_rgba: the new rgba value to use in its place


 This causes a color value in the icon's palette to be changed. You can use
null in place of an RGB or RGBA value.




 If the old color is a full RGBA color with an alpha value, such as
rgb(1,2,3,4) or "#01020304", then that exact color is the only one changed.




 If the old color is an RGB value with no alpha specified, such as
rgb(1,2,3) or "#010203", then that color will change to the new one
regardless of its alpha value, and the original icon's alpha will be kept
intact. (If the new color is totally transparent, however, then the old color
will be replaced with full transparency.)





---



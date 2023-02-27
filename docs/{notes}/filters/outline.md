

 Outline filter
----------------




**See also:** 


[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 



**See also:** 

**See also:**

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow)


 Format:
 

 filter(type="outline", ...)
 


 Format:


 filter(type="outline", ...)



 Args:
 

 size: Width in pixels (defaults to 1)
 

 color: Outline color (defaults to black)
 

 flags: Defaults to 0 (see below)
 


 Args:


 size: Width in pixels (defaults to 1)


 color: Outline color (defaults to black)


 flags: Defaults to 0 (see below)


 Applies an outline to this image.




 At larger sizes, the outline is less accurate and will take more passes to
produce. Performance and appearance are best at sizes close to 1 or less.





 flags
 
 can be a combination of the following values:




 flags



 0
 

 Ordinary outline
 

 OUTLINE\_SHARP
 

 Avoid antialiasing in the outline
 

 OUTLINE\_SQUARE
 

 Extend the outline sharply from corner pixels; for a box this will maintain a box shape without rounded corners
 


 0


 Ordinary outline


 OUTLINE\_SHARP


 Avoid antialiasing in the outline


 OUTLINE\_SQUARE


 Extend the outline sharply from corner pixels; for a box this will maintain a box shape without rounded corners



---



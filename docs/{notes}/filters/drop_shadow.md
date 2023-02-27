

 Drop shadow filter
--------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Outline (filters)](#/{notes}/filters/outline) 




**See also:** 

**See also:**

[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Outline (filters)](#/{notes}/filters/outline) 


[Gaussian blur (filters)](#/{notes}/filters/blur)

[Outline (filters)](#/{notes}/filters/outline) 

[Outline (filters)](#/{notes}/filters/outline)


 Format:
 

 filter(type="drop\_shadow", ...)
 


 Format:


 filter(type="drop\_shadow", ...)



 Args:
 

 x: Shadow horizontal offset (defaults to 1)
 

 y: Shadow horizontal offset (defaults to -1)
 

 size: Blur amount (defaults to 1; negative values create inset shadows)
 

 offset: Size increase before blur (defaults to 0)
 

 color: Shadow color (defaults to 50% transparent black)
 


 Args:


 x: Shadow horizontal offset (defaults to 1)


 y: Shadow horizontal offset (defaults to -1)


 size: Blur amount (defaults to 1; negative values create inset shadows)


 offset: Size increase before blur (defaults to 0)


 color: Shadow color (defaults to 50% transparent black)


 Applies a drop shadow to this image. This is a combination of multiple
filters, since it will apply an outline if
 
 offset
 
 is included, a
Gaussian blur to the shadow, and will underlay the shadow beneath the image.




 offset


 You can also think of this filter as an outer glow.




 If you use a
 
 size
 
 less than 0, the shadow will appear inside the
image instead. This would be an inset shadow, or inner glow.




 size



---



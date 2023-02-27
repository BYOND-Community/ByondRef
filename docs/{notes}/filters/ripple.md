

 Ripple filter
---------------




**See also:** 


[Wave (filters)](#/{notes}/filters/wave) 



**See also:** 

**See also:**

[Wave (filters)](#/{notes}/filters/wave) 

[Wave (filters)](#/{notes}/filters/wave)


 Format:
 

 filter(type="ripple", ...)
 


 Format:


 filter(type="ripple", ...)



 Args:
 

 x: Horiztonal position of ripple center, relative to image center (defaults to 0)
 

 y: Vertical position of ripple center, relative to image center (defaults to 0)
 

 size: Maximum distortion in pixels (defaults to 1)
 

 repeat: Wave period, in pixels (defaults to 2)
 

 radius: Outer radius of ripple, in pixels (defaults to 0)
 

 falloff: How quickly ripples lose strength away from the outer edge (defaults to 1)
 

 flags: Defaults to 0; use
 
 WAVE\_BOUNDED
 
 to keep distortion within the image
 


 Args:


 x: Horiztonal position of ripple center, relative to image center (defaults to 0)


 y: Vertical position of ripple center, relative to image center (defaults to 0)


 size: Maximum distortion in pixels (defaults to 1)


 repeat: Wave period, in pixels (defaults to 2)


 radius: Outer radius of ripple, in pixels (defaults to 0)


 falloff: How quickly ripples lose strength away from the outer edge (defaults to 1)


 flags: Defaults to 0; use
 
 WAVE\_BOUNDED
 
 to keep distortion within the image


 WAVE\_BOUNDED


 Applies a ripple distortion effect to this image.




 This filter is meant to be animated. A good animation will typically start
at a
 
 radius
 
 of 0 and animate to a larger value, with
 
 size
 
 decreasing to 0.




 radius


 size


 The
 
 falloff
 
 parameter can be tweaked to your liking. A value of 1
should look reasonably like ripples in water, with the inner ripples losing
strength. A value of 0 will cause no reduction in strength.




 falloff


 The equation governing the ripple distortion is size × sin(2πr') ÷ (2.5 × falloff × r'
 2 
 + 1),
where r' = (radius - distance) ÷ repeat.



2

 Up to 10 ripples can be stacked together in a single pass of the filter, as
long as they have the same
 
 repeat
 
 ,
 
 falloff
 
 , and
 
 flags
 
 values. (See the wave filter for the
 
 WAVE\_BOUNDED
 
 flag.)




 repeat


 falloff


 flags


 WAVE\_BOUNDED



---



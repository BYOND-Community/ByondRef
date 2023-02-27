

 Displacement map filter
-------------------------




**See also:** 


[Alpha mask (filters)](#/{notes}/filters/alpha) 

[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 





**See also:** 

**See also:**

[Alpha mask (filters)](#/{notes}/filters/alpha) 

[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 



[Alpha mask (filters)](#/{notes}/filters/alpha)

[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 


[icon var (atom)](#/atom/var/icon)

[render\_target var (atom)](#/atom/var/render_target) 

[render\_target var (atom)](#/atom/var/render_target)


 Format:
 

 filter(type="displace", ...)
 


 Format:


 filter(type="displace", ...)



 Args:
 

 x: Horizontal offset of map (defaults to 0)
 

 y: Vertical offset of map (defaults to 0)
 

 size: Maximum distortion, in pixels
 

 icon: Icon to use as a displacement map
 

 render\_source:
 
 render\_target
 
 to use as a displacement map
 


 Args:


 x: Horizontal offset of map (defaults to 0)


 y: Vertical offset of map (defaults to 0)


 size: Maximum distortion, in pixels


 icon: Icon to use as a displacement map


 render\_source:
 
 render\_target
 
 to use as a displacement map


 render\_target


 Uses an icon or render target as a template for various warping effects on
the main image.




 In the displacement map, pixels that have a higher red component will make
the image appear to warp to the left, lower reds warp it to the right, and
gray (r=128) will cause no horizontal warping. The green component affects the
vertical: higher to warp upward, lower to warp downward. Transparent pixels in
the displacement map will have no effect.




 This can be used for very complex distortion, unlike other distortion
filters such as wave and ripple that are confined to specific equations.





---



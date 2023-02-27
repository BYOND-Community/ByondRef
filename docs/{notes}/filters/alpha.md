

 Alpha mask filter
-------------------




**See also:** 


[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 




**See also:** 

**See also:**

[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 


[icon var (atom)](#/atom/var/icon)

[render\_target var (atom)](#/atom/var/render_target) 

[render\_target var (atom)](#/atom/var/render_target)


 Format:
 

 filter(type="alpha", ...)
 


 Format:


 filter(type="alpha", ...)



 Args:
 

 x: Horizontal offset of mask (defaults to 0)
 

 y: Vertical offset of mask (defaults to 0)
 

 icon: Icon to use as a mask
 

 render\_source:
 
 render\_target
 
 to use as a mask
 

 flags: Defaults to 0; use see below for other flags
 


 Args:


 x: Horizontal offset of mask (defaults to 0)


 y: Vertical offset of mask (defaults to 0)


 icon: Icon to use as a mask


 render\_source:
 
 render\_target
 
 to use as a mask


 render\_target


 flags: Defaults to 0; use see below for other flags


 Uses an icon or render target as a mask over this image. Every pixel that
is transparent in either the image or the mask, is transparent in the result.




 The
 
 x
 
 and
 
 y
 
 values can move the mask from its normal
position. By default, the mask is centered over the center of the image.




 x


 y


 The
 
 MASK\_INVERSE
 
 flag will invert the alpha mask so that opaque
areas in the mask become transparent, and vice-versa. There is also a
 
 MASK\_SWAP
 
 flag which treats the source image as the mask and
vice-versa, which might be useful for some effects.




 MASK\_INVERSE


 MASK\_SWAP


 Note: Unlike many other filters, this filter
 **is** 
 taken into account
for mouse-hit purposes.



**is**


---



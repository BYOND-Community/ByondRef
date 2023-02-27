

 Layering (composite) filter
-----------------------------




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
 

 filter(type="layer", ...)
 


 Format:


 filter(type="layer", ...)



 Args:
 

 x: Horizontal offset of second image (defaults to 0)
 

 y: Vertical offset of second image (defaults to 0)
 

 icon: Icon to use as a second image
 

 render\_source:
 
 render\_target
 
 to use as a second image
 

 flags:
 
 FILTER\_OVERLAY
 
 (default) or
 
 FILTER\_UNDERLAY
 


 color:
 [Color](#/atom/var/color) 
 or color matrix to apply to second image
 

 transform:
 [Transform](#/atom/var/transform) 
 to apply to second image
 

 blend\_mode:
 [Blend mode](#/atom/var/blend_mode) 
 to apply to the top image
 


 Args:


 x: Horizontal offset of second image (defaults to 0)


 y: Vertical offset of second image (defaults to 0)


 icon: Icon to use as a second image


 render\_source:
 
 render\_target
 
 to use as a second image


 render\_target


 flags:
 
 FILTER\_OVERLAY
 
 (default) or
 
 FILTER\_UNDERLAY
 


 FILTER\_OVERLAY


 FILTER\_UNDERLAY


 color:
 [Color](#/atom/var/color) 
 or color matrix to apply to second image

[Color](#/atom/var/color)

 transform:
 [Transform](#/atom/var/transform) 
 to apply to second image

[Transform](#/atom/var/transform)

 blend\_mode:
 [Blend mode](#/atom/var/blend_mode) 
 to apply to the top image

[Blend mode](#/atom/var/blend_mode)

 Composites another image over or under this image. Using the
 
 FILTER\_OVERLAY
 
 flag, which is the default, puts the second image
on top of what's already here.
 
 FILTER\_UNDERLAY
 
 puts it underneath.




 FILTER\_OVERLAY


 FILTER\_UNDERLAY


 The
 
 x
 
 and
 
 y
 
 values can move the mask from its normal
position. By default, the second image is centered over the center of the
first.




 x


 y


 The
 
 color
 
 ,
 
 transform
 
 , and
 
 blend\_mode
 
 vars are
available for convenience. Because the bottom image is drawn over a blank
background,
 
 blend\_mode
 
 is always applied to the top image. All of
the other vars apply to the second image being drawn.




 color


 transform


 blend\_mode


 blend\_mode


 Note: Transforms use default bilinear scaling, since
 [PIXEL\_SCALE](#/atom/var/appearance_flags) 
 is not
available here.



[PIXEL\_SCALE](#/atom/var/appearance_flags)

 Note: Like most other filters, this filter is
 **not** 
 taken into account
for mouse-hit purposes. Any layered icons will be strictly visual.



**not**


---



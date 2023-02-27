

 Filter effects
----------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[filter proc](#/proc/filter) 

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 







**See also:** 

**See also:**

[filters var (atom)](#/atom/var/filters) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[filter proc](#/proc/filter) 

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 





[filters var (atom)](#/atom/var/filters)

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[filter proc](#/proc/filter) 

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 




[appearance\_flags var (atom)](#/atom/var/appearance_flags)

[filter proc](#/proc/filter) 

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 



[filter proc](#/proc/filter)

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 


[animate proc](#/proc/animate)

[Understanding the renderer](#/{notes}/renderer) 

[Understanding the renderer](#/{notes}/renderer)

 Filters are a way of adding special effects to an icon, or a group of icons
(see
 
 KEEP\_TOGETHER
 
 in
 [appearance\_flags](#/atom/var/appearance_flags) 
 ), by
post-processing the image. A filter object describes a specific form of image
processing, like for instance a blur or a drop shadow. Filters can be added or
removed at will, and can even be animated.




 KEEP\_TOGETHER

[appearance\_flags](#/atom/var/appearance_flags)

 A filter is created by using the
 [filter proc](#/proc/filter) 
 like
so:



[filter proc](#/proc/filter)

 // halo effect
mob.filters += filter(type="drop\_shadow", x=0, y=0,\
 size=5, offset=2, color=rgb(255,255,170))


 These are the filters currently supported:



* [Alpha mask](#/{notes}/filters/alpha)
* [Angular blur](#/{notes}/filters/angular_blur)
* [Bloom](#/{notes}/filters/bloom)
* [Color matrix](#/{notes}/filters/color)
* [Displacement map](#/{notes}/filters/displace)
* [Drop shadow](#/{notes}/filters/drop_shadow)
* [Gaussian blur](#/{notes}/filters/blur)
* [Layering (composite)](#/{notes}/filters/layer)
* [Motion blur](#/{notes}/filters/motion_blur)
* [Outline](#/{notes}/filters/outline)
* [Radial blur](#/{notes}/filters/radial_blur)
* [Rays](#/{notes}/filters/rays)
* [Ripple](#/{notes}/filters/ripple)
* [Wave](#/{notes}/filters/wave)


- [Alpha mask](#/{notes}/filters/alpha)

[Alpha mask](#/{notes}/filters/alpha)
- [Angular blur](#/{notes}/filters/angular_blur)

[Angular blur](#/{notes}/filters/angular_blur)
- [Bloom](#/{notes}/filters/bloom)

[Bloom](#/{notes}/filters/bloom)
- [Color matrix](#/{notes}/filters/color)

[Color matrix](#/{notes}/filters/color)
- [Displacement map](#/{notes}/filters/displace)

[Displacement map](#/{notes}/filters/displace)
- [Drop shadow](#/{notes}/filters/drop_shadow)

[Drop shadow](#/{notes}/filters/drop_shadow)
- [Gaussian blur](#/{notes}/filters/blur)

[Gaussian blur](#/{notes}/filters/blur)
- [Layering (composite)](#/{notes}/filters/layer)

[Layering (composite)](#/{notes}/filters/layer)
- [Motion blur](#/{notes}/filters/motion_blur)

[Motion blur](#/{notes}/filters/motion_blur)
- [Outline](#/{notes}/filters/outline)

[Outline](#/{notes}/filters/outline)
- [Radial blur](#/{notes}/filters/radial_blur)

[Radial blur](#/{notes}/filters/radial_blur)
- [Rays](#/{notes}/filters/rays)

[Rays](#/{notes}/filters/rays)
- [Ripple](#/{notes}/filters/ripple)

[Ripple](#/{notes}/filters/ripple)
- [Wave](#/{notes}/filters/wave)

[Wave](#/{notes}/filters/wave)


---



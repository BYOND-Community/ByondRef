

 Gaussian blur filter
----------------------




**See also:** 


[Motion blur (filters)](#/{notes}/filters/motion_blur) 

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 






**See also:** 

**See also:**

[Motion blur (filters)](#/{notes}/filters/motion_blur) 

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 




[Motion blur (filters)](#/{notes}/filters/motion_blur)

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 



[Radial blur (filters)](#/{notes}/filters/radial_blur)

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 


[Angular blur (filters)](#/{notes}/filters/angular_blur)

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow)


 Format:
 

 filter(type="blur", ...)
 


 Format:


 filter(type="blur", ...)



 Args:
 

 size: Amount of blur (defaults to 1)
 


 Args:


 size: Amount of blur (defaults to 1)


 Blurs the image by a certain amount. The size of the blur can roughly be
thought of in "pixels" worth of blur.




 Note: Large blurs will result in reduced performance. The
highest size that can be handled easily in this filter is 6. Higher sizes
require multiple passes, although the filter will "cheat" and use low-quality
passes for much higher sizes.





---



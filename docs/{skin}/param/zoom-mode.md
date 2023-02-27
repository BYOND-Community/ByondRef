

 zoom-mode parameter (skin)
----------------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 





**See also:** 

**See also:**

[letterbox parameter](#/{skin}/param/letterbox) 

[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 



[letterbox parameter](#/{skin}/param/letterbox)

[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 


[view-size parameter](#/{skin}/param/view-size)

[zoom parameter](#/{skin}/param/zoom) 

[zoom parameter](#/{skin}/param/zoom)


**Applies to:** 


[Map](#/{skin}/control/map) 



**Applies to:** 

**Applies to:**

[Map](#/{skin}/control/map) 

[Map](#/{skin}/control/map)


**Posisble values:** 


 normal
 
 distort
 
 blur
 




**Posisble values:** 

**Posisble values:**

 normal
 
 distort
 
 blur
 



 distort
 
 blur
 


 blur



**Default value:** 


 normal
 


**Default value:** 

**Default value:**

 normal


 Controls the way the map is upscaled.





 normal
 


 normal


 Preserves a pixelated look, but does some blending between adjacent pixels when the zoom factor is not an integer. This is equivalent to upscaling by the next highest integer, then downscaling.


 distort


 Uses nearest-neighbor sampling to upscale. This may look odd if the zoom factor is not an integer, since for instance some pixels might scale up to be 2 pixels wide, others 3 pixels wide. Some users prefer it anyway.


 blur


 Uses bilinear sampling to upscale. This will cause a blurry appearance if the zoom factor is high, but it may be desired in some cases.



---





 view-size parameter (skin)
----------------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 









**See also:** 

**See also:**

[letterbox parameter](#/{skin}/param/letterbox) 

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 







[letterbox parameter](#/{skin}/param/letterbox)

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 






[zoom parameter](#/{skin}/param/zoom)

[zoom-mode parameter](#/{skin}/param/zoom-mode) 

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 





[zoom-mode parameter](#/{skin}/param/zoom-mode)

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 




[icon\_size var (world)](#/world/var/icon_size)

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 



[view var (world)](#/world/var/view)

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 


[view var (client)](#/client/var/view)

[HUD / screen objects](#/{notes}/HUD) 

[HUD / screen objects](#/{notes}/HUD)


**Applies to:** 


[Map](#/{skin}/control/map) 
 (window only)
 


**Applies to:** 

**Applies to:**

[Map](#/{skin}/control/map) 
 (window only)

[Map](#/{skin}/control/map)


**Format:** 


*width* 
 x
 *height* 



**Format:** 

**Format:**

*width* 
 x
 *height* 

*width*
*height*

 The size, in pixels, of the map after
 
 zoom
 
 has been applied.




 zoom


 For instance, if the client view has 10×10 tiles (this includes any extended tiles caused by HUD objects) and
 
 world.icon\_size
 
 is 32x32, the map has a native size of 320×320 pixels. If the map has a zoom level of 2, then
 
 view-size
 
 will be 640x640.




 world.icon\_size


 view-size


 With a
 
 zoom
 
 value of 0, which is the default for most projects, the actual zoom level is automatically determined by the size of the map control, the map's native pixel size as explained above, and the value of the
 [letterbox](#/{skin}/param/letterbox) 
 parameter.




 zoom

[letterbox](#/{skin}/param/letterbox)


---



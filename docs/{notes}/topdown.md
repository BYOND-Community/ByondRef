

 Topdown maps
--------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 













**See also:** 

**See also:**

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 











[map\_format var (world)](#/world/var/map_format)

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 










[icon\_size var (world)](#/world/var/icon_size)

[dir var (client)](#/client/var/dir) 

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 









[dir var (client)](#/client/var/dir)

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 








[layer var (atom)](#/atom/var/layer)

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 







[plane var (atom)](#/atom/var/plane)

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 






[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc)

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 





[Big icons](#/{notes}/big-icons)

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 




[HUD](#/{notes}/HUD)

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 



[Isometric maps](#/{notes}/isometric)

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 


[Side-view maps](#/{notes}/side)

[Understanding the renderer](#/{notes}/renderer) 

[Understanding the renderer](#/{notes}/renderer)

 By default, BYOND displays all maps in top-down format, so
 
 world.map\_format
 
 is set to
 
 TOPDOWN\_MAP
 
 unless you say
otherwise. This view means players are looking down on the map, and
"north" corresponds to the top of their screen. (This can be changed by
setting
 
 client.dir
 
 .)




 world.map\_format


 TOPDOWN\_MAP


 client.dir


 A related map\_format, used by older games, is
 
 TILED\_ICON\_MAP
 
 . This
is also topdown but it handles icons differently.




 TILED\_ICON\_MAP


 In this form, the
 
 layer
 
 var behaves exactly as you would expect:
Icons with a lower layer are drawn beneath icons with a higher layer. The only
exception is when you use
 [big icons](#/{notes}/big-icons) 
 , which will
be drawn above any other icons on the same layer. Also an atom's underlays will
be drawn behind it unless their layer is changed, and its overlays will draw in
front of it unless otherwise stated.




 layer

[big icons](#/{notes}/big-icons)

 Topdown mode also guarantees that
 
 world.view
 
 or
 
 client.view
 
 will set the exact screen size used by the HUD, except for HUD objects that
appear outside of the normal bounds.




 world.view


 client.view


 Screen objects (also called the HUD) cannot be intermixed with topdown
icons. They will appear on top of other icons, unless using a lower plane or a
special layer like
 
 BACKGROUND\_LAYER
 
 .




 BACKGROUND\_LAYER



---



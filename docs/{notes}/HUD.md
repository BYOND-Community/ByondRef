

 HUD / screen objects
----------------------




**See also:** 


[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[screen var (client)](#/client/var/screen) 

[view var (client)](#/client/var/view) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 









**See also:** 

**See also:**

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[screen var (client)](#/client/var/screen) 

[view var (client)](#/client/var/view) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 







[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc)

[screen var (client)](#/client/var/screen) 

[view var (client)](#/client/var/view) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 






[screen var (client)](#/client/var/screen)

[view var (client)](#/client/var/view) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 





[view var (client)](#/client/var/view)

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 




[map\_format var (world)](#/world/var/map_format)

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 



[icon\_size var (world)](#/world/var/icon_size)

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 


[layer var (atom)](#/atom/var/layer)

[image objects](#/image) 

[image objects](#/image)

 HUD stands for Heads-Up Display, and refers to any atoms that appear on
the screen but don't move when the player moves. These are also called screen
objects. Any movable atom can be added to the HUD by setting its
 
 screen\_loc
 
 var, and adding it to
 
 client.screen
 
 for each user
who is supposed to see it. This can be used to display a character's vital
stats, scores, etc.




 screen\_loc


 client.screen


 If you want to have something like a health meter or name attached to a
moving atom, use overlays or
 
 /image
 
 objects instead. An
 
 /image
 
 object is similar to a screen object in that it can be shown
to only certain players instead of being shown to everyone.




 /image


 /image


 The size of the screen depends on
 
 client.view
 
 (or
 
 world.view
 
 ),
 
 world.map\_format
 
 , and
 
 world.icon\_size
 
 .
In a normal topdown map format,
 
 client.view
 
 is the same as the screen
size; in other map formats the screen might be a different size.




 client.view


 world.view


 world.map\_format


 world.icon\_size


 client.view


 The
 
 screen\_loc
 
 var can be set to a value like
 
 "1,1"
 
 (the
southwest tile of the screen),
 
 "4,NORTH"
 
 (fourth tile from the west,
along the north side of the screen),
 
 "SOUTHEAST"
 
 , and so on. You can
also include pixel offsets, percentages, and specify two corners to tile an
icon repeatedly from one end to the other. See
 [screen\_loc](#/atom/movable/var/screen_loc) 
 for more
details.




 screen\_loc


 "1,1"


 "4,NORTH"


 "SOUTHEAST"

[screen\_loc](#/atom/movable/var/screen_loc)


 screen\_loc
 
 can also be used to stretch the bounds of the HUD. A
value of
 
 "0,0"
 
 will cause the atom to appear to the southwest of the
southwest-most tile on the visible map, outside of the regular map bounds.
Using HUDs in this way, you can provide a nice decorative "frame" for your map.




 screen\_loc


 "0,0"


 More complex




 You can use HUDs in other map controls as well, by preceding screen\_loc with
the name of the map you will use followed by a colon. For instance,
 
 screen\_loc="map2:1,1"
 
 will show an icon in the southwest corner of the
 
 map2
 
 control. The actual size of a secondary HUD is based on how far
out the icons in it extend in any direction. If you have one icon at
 
 "map2:1,1"
 
 and another at
 
 "map2:4,3"
 
 , then that HUD will be
four tiles wide and three high.




 screen\_loc="map2:1,1"


 map2


 "map2:1,1"


 "map2:4,3"



---



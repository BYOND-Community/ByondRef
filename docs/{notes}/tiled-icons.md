

 Tiled icons
-------------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 







**See also:** 

**See also:**

[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 





[icon](#/icon)

[procs (icon)](#/icon/proc) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 




[procs (icon)](#/icon/proc)

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 



[map\_format var (world)](#/world/var/map_format)

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 


[icon\_size var (world)](#/world/var/icon_size)

[Big icons](#/{notes}/big-icons) 

[Big icons](#/{notes}/big-icons)

 In BYOND 3.0, any file like a large .bmp would be treated like a regular
icon that had been broken up into several tile-sized icon states. All tiles
then were 32x32 pixels. An image that was 100x100 would therefore take at
least 4x4 tiles to display. The icon was padded to the right and the top with
blank space to become an even multiple of 32x32, and then broken up into
sections. The lower left section was given an icon\_state of
 
 "0,0"
 
 ,
the next to the right was
 
 "1,0"
 
 , and so on, up to the upper right
which was
 
 "3,3"
 
 . Another icon state, a 32x32 thumbnail of the big
image, was also included.




 "0,0"


 "1,0"


 "3,3"


 BYOND 4.0 expanded on this concept by allowing icons to be defined that had
individual graphics bigger than 32x32, and it would break each one up into
tiles just like 3.0 did. If an icon had a state called
 
 "open"
 
 then it
might break down into
 
 "open 0,0"
 
 ,
 
 "open 1,0"
 
 , and so on,
while the actual
 
 "open"
 
 state would be a thumbnail image. To show the
whole image, you would have to have a separate atom or overlay for each
individual tile.




 "open"


 "open 0,0"


 "open 1,0"


 "open"


 In newer versions, breaking big icons into tiles is no longer done by
default. Instead, icons are shown and manipulated in their
 [native size](#/{notes}/big-icons) 
 . To use the old method of breaking
icons into tiles, set
 
 world.map\_format
 
 to
 
 TILED\_ICON\_MAP
 
 .
This is the default for all projects compiled before version 455.



[native size](#/{notes}/big-icons)

 world.map\_format


 TILED\_ICON\_MAP


 When using tiled icons, there are some important things to note:



* You need to use extra atoms or overlays to show any icon bigger than a
 single tile, where each atom/overlay shows an individual tile-sized piece
 of the big icon.
* The icon\_state names of each tile are always the original name followed
 by a space, followed by x,y tile coordinates such as 0,0 or 2,1, so the
 northeast corner of
 
 "flag"
 
 might for instance be
 
 "flag 3,2"
 
 . If the original icon\_state had no name, the space is
 left out and only the x,y coordinates are used.
* Every icon's size is a multiple of world.icon\_size. If an icon of an
 incompatible size is used, it will be padded to the nearest full tile
 size.
* Crop()
 
 and
 
 Scale()
 
 always pad their results to the
 nearest full tile size.
* icon.Insert()
 
 can insert a single-tile icon into a multi-tiled
 big icon using the appropriate icon\_state; e.g., inserting into
 
 "door 0,0"
 
 will replace the southwest corner of the
 
 "door"
 
 state.
* Using the
 
 icon()
 
 proc, you can extract a single tile from a
 multi-tiled big icon.


- You need to use extra atoms or overlays to show any icon bigger than a
 single tile, where each atom/overlay shows an individual tile-sized piece
 of the big icon.

- The icon\_state names of each tile are always the original name followed
 by a space, followed by x,y tile coordinates such as 0,0 or 2,1, so the
 northeast corner of
 
 "flag"
 
 might for instance be
 
 "flag 3,2"
 
 . If the original icon\_state had no name, the space is
 left out and only the x,y coordinates are used.


 "flag"


 "flag 3,2"

- Every icon's size is a multiple of world.icon\_size. If an icon of an
 incompatible size is used, it will be padded to the nearest full tile
 size.

- Crop()
 
 and
 
 Scale()
 
 always pad their results to the
 nearest full tile size.


 Crop()


 Scale()

- icon.Insert()
 
 can insert a single-tile icon into a multi-tiled
 big icon using the appropriate icon\_state; e.g., inserting into
 
 "door 0,0"
 
 will replace the southwest corner of the
 
 "door"
 
 state.


 icon.Insert()


 "door 0,0"


 "door"

- Using the
 
 icon()
 
 proc, you can extract a single tile from a
 multi-tiled big icon.


 icon()


 This example shows a big icon being applied to an atom in tiled mode, as
overlays:



### 
 Example:



 // icon is 3 tiles wide by 2 high
icon\_state = "0,0"

// A temporary object used for the overlays
var/obj/O = new
O.icon = icon
O.layer = FLOAT\_LAYER

for(var/tile\_y=0, tile\_y<2, ++tile\_y)
 for(var/tile\_x=0, tile\_x<3, ++tile\_x)
 if(tile\_x && tile\_y)
 O.pixel\_x = tile\_x \* 32
 O.pixel\_y = tile\_y \* 32
 O.icon\_state = "[tile\_x],[tile\_y]"
 overlays += O



---



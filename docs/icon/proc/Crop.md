

 Crop proc (icon)
------------------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 








**See also:** 

**See also:**

[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 






[icon](#/icon)

[procs (icon)](#/icon/proc) 

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 





[procs (icon)](#/icon/proc)

[icon\_size var (world)](#/world/var/icon_size) 

[map\_format var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 




[icon\_size var (world)](#/world/var/icon_size)

[map\_format var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 



[map\_format var (world)](#/world/var/icon_size)

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 


[Big icons](#/{notes}/big-icons)

[Tiled icons](#/{notes}/tiled-icons) 

[Tiled icons](#/{notes}/tiled-icons)


**Format:** 


 Crop(x1,y1,x2,y2)
 


**Format:** 

**Format:**

 Crop(x1,y1,x2,y2)



**Args:** 


 x1,y1: Coordinates of one corner of the rectangle (1,1 is the lower left)
 
 x2,y2: Coordinates of the other corner
 



**Args:** 

**Args:**

 x1,y1: Coordinates of one corner of the rectangle (1,1 is the lower left)
 
 x2,y2: Coordinates of the other corner
 


 x2,y2: Coordinates of the other corner


 A portion of the current icon is cropped (cut). If the crop region extends
outside the icon, it will be padded with transparent pixels.




 If using the TILED\_ICON\_MAP value for map\_format, all icons must be even
multiples of world.tile\_size, so the icon will be padded with transparent
pixels to the top and right as needed.



### 
 Example:



 // start with a simple icon
var/icon/I = new('circle.dmi')
// take the upper right 16x16 chunk
I.Crop(17,17,32,32)
// that chunk now appears in the lower left corner
icon = I



---



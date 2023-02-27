

 image proc
------------




**See also:** 


[<< operator](#/operator/%3c%3c) 

[del proc](#/proc/del) 

[icon](#/icon) 

[image objects](#/image) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 








**See also:** 

**See also:**

[<< operator](#/operator/%3c%3c) 

[del proc](#/proc/del) 

[icon](#/icon) 

[image objects](#/image) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 






[<< operator](#/operator/%3c%3c)

[del proc](#/proc/del) 

[icon](#/icon) 

[image objects](#/image) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 





[del proc](#/proc/del)

[icon](#/icon) 

[image objects](#/image) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 




[icon](#/icon)

[image objects](#/image) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 



[image objects](#/image)

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 


[images var (client)](#/client/var/images)

[overlays var (atom)](#/atom/var/overlays) 

[overlays var (atom)](#/atom/var/overlays)


**Format:** 


 image(icon,loc,icon\_state,layer,dir)
 

 (supports
 [named arguments](#/proc/arguments/named) 
 )
 




**Format:** 

**Format:**

 image(icon,loc,icon\_state,layer,dir)
 

 (supports
 [named arguments](#/proc/arguments/named) 
 )
 




 (supports
 [named arguments](#/proc/arguments/named) 
 )
 


 (supports
 [named arguments](#/proc/arguments/named) 
 )

[named arguments](#/proc/arguments/named)


**Returns:** 


 An image reference on success; 0 on failure.
 


**Returns:** 

**Returns:**

 An image reference on success; 0 on failure.



**Args:** 


 icon: An icon, object prototype, object instance, or other image.
 
 loc: The location at which to display the image.
 
 icon\_state: The icon state to use.
 
 layer: The drawing layer to use.
 
 dir: The direction to orient the image.
 






**Args:** 

**Args:**

 icon: An icon, object prototype, object instance, or other image.
 
 loc: The location at which to display the image.
 
 icon\_state: The icon state to use.
 
 layer: The drawing layer to use.
 
 dir: The direction to orient the image.
 





 loc: The location at which to display the image.
 
 icon\_state: The icon state to use.
 
 layer: The drawing layer to use.
 
 dir: The direction to orient the image.
 




 icon\_state: The icon state to use.
 
 layer: The drawing layer to use.
 
 dir: The direction to orient the image.
 



 layer: The drawing layer to use.
 
 dir: The direction to orient the image.
 


 dir: The direction to orient the image.


 Images are "virtual" objects, which have a purely visual effect. Once
created, they can be made to appear to selected players. The image()
instruction is simply a short-hand for new/image().




 The image remains attached to the location specified by
 
 loc
 
 .
For example, if
 
 loc
 
 is a mob, the image will appear above the mob
until it is destroyed.




 loc


 loc


 The arguments
 
 icon\_state
 
 ,
 
 layer
 
 , and
 
 dir
 
 may be used to override the settings associated with the icon or object used
to create the image. For example, the default drawing layer for an plain icon
is FLY\_LAYER (above all other objects), but you could change this to OBJ\_LAYER
to make it appear under mobs on the map.




 icon\_state


 layer


 dir

### 
 Example:



 var/Box
Box = image ('highlight.dmi', usr)
usr << Box
...
del(Box) //when done, remove image


 Another common use of images is in making an overlay:




 overlays += image('pants.dmi',icon\_state = "red")


 Since the
 `loc` 
 argument could never be a text string, the above
statement can be further shortened:



`loc`

 overlays += image('pants.dmi',"red")


 This is much preferable to achieving the same effect with
 `icon('pants.dmi',"red")` 
 , since that involves the
overhead of creating a new icon file, which should only be done when it is
really necessary.



`icon('pants.dmi',"red")`


---



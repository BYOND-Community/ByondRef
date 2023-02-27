

 image objects
---------------




**See also:** 


[icon var (atom)](#/atom/var/icon) 

[image proc](#/proc/image) 

[vars (image)](#/image/var) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 

[override var (atom)](#/atom/var/override) 








**See also:** 

**See also:**

[icon var (atom)](#/atom/var/icon) 

[image proc](#/proc/image) 

[vars (image)](#/image/var) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 

[override var (atom)](#/atom/var/override) 






[icon var (atom)](#/atom/var/icon)

[image proc](#/proc/image) 

[vars (image)](#/image/var) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 

[override var (atom)](#/atom/var/override) 





[image proc](#/proc/image)

[vars (image)](#/image/var) 

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 

[override var (atom)](#/atom/var/override) 




[vars (image)](#/image/var)

[images var (client)](#/client/var/images) 

[overlays var (atom)](#/atom/var/overlays) 

[override var (atom)](#/atom/var/override) 



[images var (client)](#/client/var/images)

[overlays var (atom)](#/atom/var/overlays) 

[override var (atom)](#/atom/var/override) 


[overlays var (atom)](#/atom/var/overlays)

[override var (atom)](#/atom/var/override) 

[override var (atom)](#/atom/var/override)

 The /image type contains data used to create a virtual image. Unlike other
atomic objects, this object is a purely visual effect. It always appears
attached to some other object and it behaves in every way as though it were
part of that object (e.g. if the user clicks on it, this counts as a click on
the atomic object, not the image).




 One reason for creating images is player-by-player control over visibility.
Images only become visible when they are explicitly output to players:



### 
 Example:



 var/image/I = image('icon.dmi',usr) //make an image attached to usr
usr << I //allow usr to see it


 Images are also useful in the creation of overlays. Overlays are like
images, since they are always attached to another object, but overlays obey
the normal rules of visibility, so they are more convenient when you do not
want to hide the effect from anybody. An overlay can be created directly from
an icon file (or icon state), but when one wishes to override some additional
parameter, the image() instruction is a convenient way to do it.



### 
 Example:



 usr.overlays += image('shirt.dmi',icon\_state = "red")


 In the above example, the icon state of an overlay was set by creating the
overlay from an image with the desired icon state. Note that after the
creation of an overlay, no link remains between the overlay and the object
that was used to create it. If you change the image after that time, it will
not change the overlay, which is simply a "snapshot" of the original image.





---





 mutable appearance
--------------------




**See also:** 


[appearance var (atom)](#/atom/var/appearance) 

[image objects](#/image) 

[vars (mutable appearance)](#/mutable_appearance/var) 





**See also:** 

**See also:**

[appearance var (atom)](#/atom/var/appearance) 

[image objects](#/image) 

[vars (mutable appearance)](#/mutable_appearance/var) 



[appearance var (atom)](#/atom/var/appearance)

[image objects](#/image) 

[vars (mutable appearance)](#/mutable_appearance/var) 


[image objects](#/image)

[vars (mutable appearance)](#/mutable_appearance/var) 

[vars (mutable appearance)](#/mutable_appearance/var)

 All atoms and images have an appearance, which is an immutable object
that can be shared by many atoms. Making changes to an object's appearance
generates new appearances, many of which may be temporary. For
high-performance games, this can be a drawback. The
 
 /mutable\_appearance
 
 type exists so that you can make multiple changes
to an appearance without creating all the temporary objects, then turn it into
a regular immutable appearance when finished.




 /mutable\_appearance


 A new mutable appearance is created via
 
 new/mutable\_appearance
 
 ,
and giving it an atom, image, or appearance as a source object. Assigning it
to an object's appearance var will create a new immutable appearance.




 new/mutable\_appearance

### 
 Example:



 mob/proc/GetAngry()
 var/mutable\_appearance/ma = new(src)
 ma.color = rgb(51,255,51) // green
 ma.transform = matrix(2,0,0,0,2,0) // scale x2
 appearance = ma


 Reading certain vars, such as
 
 overlays
 
 , will create a temporary
list object that can be modified easily. With regular appearances, making
many changes to the
 
 overlays
 
 list results in a lot of churn.




 overlays


 overlays


 The
 
 /mutable\_appearance
 
 datum is technically a descendant of
 
 /image
 
 , but this is only for convenience, and should not be relied
on for any other purpose as it is subject to change in future versions.




 /mutable\_appearance


 /image



---



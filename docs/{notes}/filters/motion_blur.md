

 Motion blur filter
--------------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[Gaussian blur (filters)](#/{notes}/filters/blur) 




**See also:** 

**See also:**

[filters var (atom)](#/atom/var/filters) 

[Gaussian blur (filters)](#/{notes}/filters/blur) 


[filters var (atom)](#/atom/var/filters)

[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Gaussian blur (filters)](#/{notes}/filters/blur)


 Format:
 

 filter(type="motion\_blur", ...)
 


 Format:


 filter(type="motion\_blur", ...)



 Args:
 

 x: Blur vector on the X axis (defaults to 0)
 

 y: Blur vector on the Y axis (defaults to 0)
 


 Args:


 x: Blur vector on the X axis (defaults to 0)


 y: Blur vector on the Y axis (defaults to 0)


 Applies Gaussian blur in one direction only. The amount and direction are
both specified by
 
 x
 
 and
 
 y
 
 . The size of the blur is equal to
 
 sqrt(x\*x + y\*y)
 
 .




 x


 y


 sqrt(x\*x + y\*y)


 See
 [Gaussian blur](#/{notes}/filters/blur) 
 for more information.



[Gaussian blur](#/{notes}/filters/blur)


---



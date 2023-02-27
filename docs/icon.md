

 icon object
-------------




**See also:** 


[procs (icon)](#/icon/proc) 

[icons](#/DM/icon) 

[image objects](#/image) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 






**See also:** 

**See also:**

[procs (icon)](#/icon/proc) 

[icons](#/DM/icon) 

[image objects](#/image) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 




[procs (icon)](#/icon/proc)

[icons](#/DM/icon) 

[image objects](#/image) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 



[icons](#/DM/icon)

[image objects](#/image) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 


[image objects](#/image)

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[stddef.dm file](#/{{appendix}}/stddef%2edm)

 An
 
 /icon
 
 object is created by loading an icon file into memory for
direct access and manipulation. In order to be displayed, an
 
 /icon
 
 object always gets converted back into an icon file; this happens
automatically when you assign atom.icon to an
 
 /icon
 
 object, since
that variable may only refer to a static icon file, rather than a dynamic
memory object.




 /icon


 /icon


 /icon


 To create an
 
 /icon
 
 object, simply use
 
 new/icon()
 
 , or the
short-cut
 
 icon()
 
 proc. The following example loads an icon file,
reddens it, and then assigns it back to the player's icon, which implicitly
creates a new icon file.




 /icon


 new/icon()


 icon()

### 
 Example:



 mob/verb/test()
 var/icon/I = new('player.dmi')
 I.Blend(rgb(40,0,0))
 usr.icon = I


 Note that merely displaying different icon states or directions can
generally be achieved without any icon manipulation, which saves quite a bit
of overhead. For example, the variables
 
 atom.icon\_state
 
 and
 
 atom.dir
 
 can be used to control how
 
 atom.icon
 
 is displayed,
without any need for generating a new icon file.




 atom.icon\_state


 atom.dir


 atom.icon


 Many things that used to require icon manipulation may not need you to do
so anymore, as DM has evolved new capabilities.





| 
 Operation
  | 
 /icon
 
 proc
  | 
 New method
  |
| --- | --- | --- |
| 
 Multiplying by color
  | [Blend](#/icon/proc/Blend)
 or
 [SetIntensity](#/icon/proc/SetIntensity) 
 procs
  | [color](#/atom/var/color) 
 var
  |
| 
 Adding color
  | [Blend](#/icon/proc/Blend) 
 proc
  | [color](#/atom/var/color) 
 var (using
 [color matrix](#/{notes}/color-matrix) 
 )
  |
| 
 Applying color matrix
  | [MapColors](#/icon/proc/MapColors) 
 proc
  |
| 
 Rotation
  | [Turn](#/icon/proc/Turn) 
 proc
  | [transform](#/atom/var/color) 
 var
  |
| 
 Flipping horizontal/vertical
  | [Flip](#/icon/proc/Flip) 
 proc
  |
| 
 Scaling
  | [Scale](#/icon/proc/Scale) 
 proc
  |
| 
 Overlaying/underlaying another icon
  | [Blend](#/icon/proc/Blend) 
 proc +
 
 ICON\_OVERLAY
  | 
 Overlay/underlay +
 [KEEP\_TOGETHER](#/atom/var/appearance_flags) 

[Layering filter](#/{notes}/filters/layer)  |


| 
 Operation
  | 
 /icon
 
 proc
  | 
 New method
  |

 
 Operation
 |
 
 /icon
 
 proc
 |

 /icon

 
 New method
 |
| 
 Multiplying by color
  | [Blend](#/icon/proc/Blend)
 or
 [SetIntensity](#/icon/proc/SetIntensity) 
 procs
  | [color](#/atom/var/color) 
 var
  |

 
 Multiplying by color
 |
 [Blend](#/icon/proc/Blend)
 or
 [SetIntensity](#/icon/proc/SetIntensity) 
 procs
 |
[Blend](#/icon/proc/Blend)

 Blend

[SetIntensity](#/icon/proc/SetIntensity)
 [color](#/atom/var/color) 
 var
 |
[color](#/atom/var/color)
| 
 Adding color
  | [Blend](#/icon/proc/Blend) 
 proc
  | [color](#/atom/var/color) 
 var (using
 [color matrix](#/{notes}/color-matrix) 
 )
  |

 
 Adding color
 |
 [Blend](#/icon/proc/Blend) 
 proc
 |
[Blend](#/icon/proc/Blend)
 [color](#/atom/var/color) 
 var (using
 [color matrix](#/{notes}/color-matrix) 
 )
 |
[color](#/atom/var/color)
[color matrix](#/{notes}/color-matrix)
| 
 Applying color matrix
  | [MapColors](#/icon/proc/MapColors) 
 proc
  |

 
 Applying color matrix
 |
 [MapColors](#/icon/proc/MapColors) 
 proc
 |
[MapColors](#/icon/proc/MapColors)
| 
 Rotation
  | [Turn](#/icon/proc/Turn) 
 proc
  | [transform](#/atom/var/color) 
 var
  |

 
 Rotation
 |
 [Turn](#/icon/proc/Turn) 
 proc
 |
[Turn](#/icon/proc/Turn)
 [transform](#/atom/var/color) 
 var
 |
[transform](#/atom/var/color)
| 
 Flipping horizontal/vertical
  | [Flip](#/icon/proc/Flip) 
 proc
  |

 
 Flipping horizontal/vertical
 |
 [Flip](#/icon/proc/Flip) 
 proc
 |
[Flip](#/icon/proc/Flip)
| 
 Scaling
  | [Scale](#/icon/proc/Scale) 
 proc
  |

 
 Scaling
 |
 [Scale](#/icon/proc/Scale) 
 proc
 |
[Scale](#/icon/proc/Scale)
| 
 Overlaying/underlaying another icon
  | [Blend](#/icon/proc/Blend) 
 proc +
 
 ICON\_OVERLAY
  | 
 Overlay/underlay +
 [KEEP\_TOGETHER](#/atom/var/appearance_flags) 

[Layering filter](#/{notes}/filters/layer)  |

 
 Overlaying/underlaying another icon
 |
 [Blend](#/icon/proc/Blend) 
 proc +
 
 ICON\_OVERLAY
  |
[Blend](#/icon/proc/Blend)

 ICON\_OVERLAY

 
 Overlay/underlay +
 [KEEP\_TOGETHER](#/atom/var/appearance_flags) 

[Layering filter](#/{notes}/filters/layer)  |
[KEEP\_TOGETHER](#/atom/var/appearance_flags)
  

[Layering filter](#/{notes}/filters/layer)

 Note: Anything you can do with an atom var instead of
using icon manipulation procs will usually perform much better. Games that use
the new methods use fewer resources, use less memory, and also usually look
better too.





---



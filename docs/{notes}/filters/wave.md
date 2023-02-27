

 Wave filter
-------------




**See also:** 


[Ripple (filters)](#/{notes}/filters/ripple) 



**See also:** 

**See also:**

[Ripple (filters)](#/{notes}/filters/ripple) 

[Ripple (filters)](#/{notes}/filters/ripple)


 Format:
 

 filter(type="wave", ...)
 


 Format:


 filter(type="wave", ...)



 Args:
 

 x: Horiztonal direction and period of wave
 

 y: Vertical direction and period of wave
 

 size: Maximum distortion in pixels (defaults to 1)
 

 offset: Phase of wave, in periods (e.g., 0 to 1)
 

 flags: Defaults to 0; see below for other flags
 


 Args:


 x: Horiztonal direction and period of wave


 y: Vertical direction and period of wave


 size: Maximum distortion in pixels (defaults to 1)


 offset: Phase of wave, in periods (e.g., 0 to 1)


 flags: Defaults to 0; see below for other flags


 Applies a wave distortion effect to this image.




 The
 
 x
 
 and
 
 y
 
 parameters specify both the direction and
period of the wave; the period is
 
 sqrt(x\*x + y\*y)
 
 .




 x


 y


 sqrt(x\*x + y\*y)


 This filter is meant to be animated, from whatever
 
 offset
 
 you want
to
 
 offset+1
 
 , and then repeating. With multiple waves, you can produce
a very convincing water effect.




 offset


 offset+1

### 
 Example



 #define WAVE\_COUNT 7
atom/proc/WaterEffect()
 var/start = filters.len
 var/X,Y,rsq,i,f
 for(i=1, i<=WAVE\_COUNT, ++i)
 // choose a wave with a random direction and a period between 10 and 30 pixels
 do
 X = 60\*rand() - 30
 Y = 60\*rand() - 30
 rsq = X\*X + Y\*Y
 while(rsq<100 || rsq>900) // keep trying if we don't like the numbers
 // keep distortion (size) small, from 0.5 to 3 pixels
 // choose a random phase (offset)
 filters += filter(type="wave", x=X, y=Y, size=rand()\*2.5+0.5, offset=rand())
 for(i=1, i<=WAVE\_COUNT, ++i)
 // animate phase of each wave from its original phase to phase-1 and then reset;
 // this moves the wave forward in the X,Y direction
 f = filters[start+i]
 animate(f, offset=f:offset, time=0, loop=-1, flags=ANIMATION\_PARALLEL)
 animate(offset=f:offset-1, time=rand()\*20+10)


 The equation governing the wave distortion is size × sin(2π(d - offset)),
where d is the number of wave periods' distance from the center along the x, y
direction.




 The
 
 WAVE\_SIDEWAYS
 
 flag will cause the distortion to be transverse
(perpendicular) to the wave instead of in the same direction as the wave. The
 
 WAVE\_BOUNDED
 
 flag limits the distortion to the confines of this image,
instead of lettings its pixels spill out a little further from the distortion
(and likewise, transparent pixels spill inward).




 WAVE\_SIDEWAYS


 WAVE\_BOUNDED


 Up to 10 waves can be stacked together in a single pass of the filter, as long as they
have the same
 
 WAVE\_BOUNDED
 
 flags.




 WAVE\_BOUNDED



---



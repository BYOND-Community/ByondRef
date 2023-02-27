

 MapColors proc (icon)
-----------------------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[rgb proc](#/proc/rgb) 





**See also:** 

**See also:**

[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[rgb proc](#/proc/rgb) 



[icon](#/icon)

[procs (icon)](#/icon/proc) 

[rgb proc](#/proc/rgb) 


[procs (icon)](#/icon/proc)

[rgb proc](#/proc/rgb) 

[rgb proc](#/proc/rgb)


**Format:** 


 MapColors(rr, rg, rb, gr, gg, gb, br, bg, bb, r0=0, g0=0, b0=0)
   

*or* 
  

 MapColors(r\_rgb, g\_rgb, b\_rgb, rgb0=rgb(0,0,0))
   

*or* 
  

 MapColors(rr, rg, rb, ra, gr, gg, gb, ga, br, bg, bb, ba, ar, ag, ab, aa, r0=0, g0=0, b0=0, a0=0)
   

*or* 
  

 MapColors(r\_rgba, g\_rgba, b\_rgba, a\_rgba, rgba0)
 


**Format:** 

**Format:**

 MapColors(rr, rg, rb, gr, gg, gb, br, bg, bb, r0=0, g0=0, b0=0)
   

*or* 
  

 MapColors(r\_rgb, g\_rgb, b\_rgb, rgb0=rgb(0,0,0))
   

*or* 
  

 MapColors(rr, rg, rb, ra, gr, gg, gb, ga, br, bg, bb, ba, ar, ag, ab, aa, r0=0, g0=0, b0=0, a0=0)
   

*or* 
  

 MapColors(r\_rgba, g\_rgba, b\_rgba, a\_rgba, rgba0)

  

*or*
  

  

*or*
  

  

*or*
  



**Args:** 


 rr: portion of old red component -> new red component
 
 rg: portion of old red component -> new green component
 
 rb: portion of old red component -> new blue component
 
 ra: portion of old red component -> new alpha component
 
 r0: new base red component
 
 ...
 






*or* 


 r\_rgb: red component is converted to this color
 
 g\_rgb: green component is converted to this color
 
 b\_rgb: blue component is converted to this color
 
 rgb0: this color is added to the result
 





**Args:** 

**Args:**

 rr: portion of old red component -> new red component
 
 rg: portion of old red component -> new green component
 
 rb: portion of old red component -> new blue component
 
 ra: portion of old red component -> new alpha component
 
 r0: new base red component
 
 ...
 






 rg: portion of old red component -> new green component
 
 rb: portion of old red component -> new blue component
 
 ra: portion of old red component -> new alpha component
 
 r0: new base red component
 
 ...
 





 rb: portion of old red component -> new blue component
 
 ra: portion of old red component -> new alpha component
 
 r0: new base red component
 
 ...
 




 ra: portion of old red component -> new alpha component
 
 r0: new base red component
 
 ...
 



 r0: new base red component
 
 ...
 


 ...


*or* 

*or*

 r\_rgb: red component is converted to this color
 
 g\_rgb: green component is converted to this color
 
 b\_rgb: blue component is converted to this color
 
 rgb0: this color is added to the result
 




 g\_rgb: green component is converted to this color
 
 b\_rgb: blue component is converted to this color
 
 rgb0: this color is added to the result
 



 b\_rgb: blue component is converted to this color
 
 rgb0: this color is added to the result
 


 rgb0: this color is added to the result


 This is used for complex color mapping that can be used for many special
effects. For the number form, values usually range from 0 to 1, but you can
use anything you like, including negative numbers. 1 means 100% of the
original color will be used. If rg=1, for example, then the amount of red in
the original icon becomes the same amount of green in the new icon's colors.




 There is also an alternate form that can use
 
 rgb()
 
 values
instead, though it is less flexible. r\_rgb is the color that will be used in
place of 100% red; any darker shades of red will become a darker shade of
that color. g\_rgb converts green to another color, and b\_rgb converts blue to
still another color, and all of them are added together.




 rgb()


 Either of these calls change the icon to grayscale:




 icon.MapColors(0.3,0.3,0.3, 0.59,0.59,0.59, 0.11,0.11,0.11, 0,0,0)
// or...
icon.MapColors(rgb(77,77,77), rgb(150,150,150), rgb(28,28,28), rgb(0,0,0))


 The calculations are as follows:



* For any red in the original icon, add 30% gray to the output.
* For any green in the original icon, add 59% gray to the output.
* For any blue in the original icon, add 11% gray to the output.
* Add an additional 0% (nothing).


- For any red in the original icon, add 30% gray to the output.

- For any green in the original icon, add 59% gray to the output.

- For any blue in the original icon, add 11% gray to the output.

- Add an additional 0% (nothing).


 Or this will make a nice moonlight effect:




 icon.MapColors(0.2,0.05,0.05, 0.1,0.3,0.2, 0.1,0.1,0.4, 0,0,0)
// or...
icon.MapColors(rgb(51,13,13), rgb(26,77,51), rgb(26,26,102), rgb(0,0,0))

* For any red in the original icon, add rgb(51,12.75,12.75) (dark pink) to the output.
* For any green in the original icon, add rgb(25.5,76.5,51) (dark bluish green) to the output.
* For any blue in the original icon, add rgb(25.5,25.5,102) (dark grayish blue) to the output.
* Add an additional 0% (nothing).


- For any red in the original icon, add rgb(51,12.75,12.75) (dark pink) to the output.

- For any green in the original icon, add rgb(25.5,76.5,51) (dark bluish green) to the output.

- For any blue in the original icon, add rgb(25.5,25.5,102) (dark grayish blue) to the output.

- Add an additional 0% (nothing).


 Or a negative icon (invert all colors):




 MapColors(-1,0,0, 0,-1,0, 0,0,-1, 1,1,1)


 The longer formats of MapColors() will allow you to also change alpha colors.





---



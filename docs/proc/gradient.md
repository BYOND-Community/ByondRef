

 gradient proc
---------------




**See also:** 


[Color gradient](#/{notes}/color-gradient) 

[rgb proc](#/proc/rgb) 

[rgb2num proc](#/proc/rgb2num) 

[Color space](#/{{appendix}}/color-space) 






**See also:** 

**See also:**

[Color gradient](#/{notes}/color-gradient) 

[rgb proc](#/proc/rgb) 

[rgb2num proc](#/proc/rgb2num) 

[Color space](#/{{appendix}}/color-space) 




[Color gradient](#/{notes}/color-gradient)

[rgb proc](#/proc/rgb) 

[rgb2num proc](#/proc/rgb2num) 

[Color space](#/{{appendix}}/color-space) 



[rgb proc](#/proc/rgb)

[rgb2num proc](#/proc/rgb2num) 

[Color space](#/{{appendix}}/color-space) 


[rgb2num proc](#/proc/rgb2num)

[Color space](#/{{appendix}}/color-space) 

[Color space](#/{{appendix}}/color-space)


**Format:** 


 gradient(Item1, Item2, ..., index)
 
 gradient(Gradient, index)
 



**Format:** 

**Format:**

 gradient(Item1, Item2, ..., index)
 
 gradient(Gradient, index)
 


 gradient(Gradient, index)



**Args:** 


 Gradient: A
 [color gradient](#/{notes}/color-gradient) 
 list
 
 Item1, Item2...: Elements of a
 [color gradient](#/{notes}/color-gradient) 
 list
 
 index: The index along the gradient where the interpolation is done.
 




**Args:** 

**Args:**

 Gradient: A
 [color gradient](#/{notes}/color-gradient) 
 list
 
 Item1, Item2...: Elements of a
 [color gradient](#/{notes}/color-gradient) 
 list
 
 index: The index along the gradient where the interpolation is done.
 


[color gradient](#/{notes}/color-gradient)

 Item1, Item2...: Elements of a
 [color gradient](#/{notes}/color-gradient) 
 list
 
 index: The index along the gradient where the interpolation is done.
 

[color gradient](#/{notes}/color-gradient)

 index: The index along the gradient where the interpolation is done.



**Returns:** 


 A color, represented by a text string in #RRGGBB or #RRGGBBAA format
 


**Returns:** 

**Returns:**

 A color, represented by a text string in #RRGGBB or #RRGGBBAA format


 Interpolates between two or more colors along a
 [color
gradient](#/{notes}/color-gradient) 
 . By default, gradients extend from an index of 0 to 1, but they
are allowed to go beyond that if you choose.



[color
gradient](#/{notes}/color-gradient)

 The simplest way to use this proc is to interpolate between two colors:



### 
 Example:



 // 20% of the way from red to black
// prints #cc0000 which is rgb(204,0,0)
src << gradient("red", "black", 0.2)


 Anything that applies to color gradients can be used in this proc, so you
can have a looping gradient, or a gradient that uses a color space other than
RGB.




 In the first format where you specify all the items separately, you can use
 [named arguments](#/proc/arguments/named) 
 for
 
 index
 
 and
 
 space
 
 (the gradient's color space). If you don't specify an argument called
"index", the last argument is assumed to be the index.



[named arguments](#/proc/arguments/named)

 index


 space

### 
 Example:



 // This gradient loops through all the hues and goes from 0 to 6.
// Because this is a looping gradient, index=10 becomes index=4.
// In HSL, this will give you blue (#0000ff).
src << gradient(0, "#f00", 3, "#0ff", 6, "#f00", "loop", space=COLORSPACE\_HSL, index=10)


 The
 
 gradient(Gradient, index)
 
 format is used for cases where you
want to pass an existing gradient to the proc.




 gradient(Gradient, index)

### 
 Example:



 var/candy\_cane\_gradient = list(0.5,"red",0.5,"white","loop")

// the color output alternates between red and white depending on the current time
src << gradient(candy\_cane\_gradient, world.time/100)



---



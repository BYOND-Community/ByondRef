

 size parameter (skin)
-----------------------




**See also:** 


[pos parameter](#/{skin}/param/pos) 

[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[on-size parameter](#/{skin}/param/on-size) 

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 







**See also:** 

**See also:**

[pos parameter](#/{skin}/param/pos) 

[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[on-size parameter](#/{skin}/param/on-size) 

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 





[pos parameter](#/{skin}/param/pos)

[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[on-size parameter](#/{skin}/param/on-size) 

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 




[anchor1, anchor2 parameters](#/{skin}/param/anchor)

[on-size parameter](#/{skin}/param/on-size) 

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 



[on-size parameter](#/{skin}/param/on-size)

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 


[inner-size parameter](#/{skin}/param/inner-size)

[outer-size parameter](#/{skin}/param/outer-size) 

[outer-size parameter](#/{skin}/param/outer-size)


**Applies to:** 


[All](#/{skin}/control) 



**Applies to:** 

**Applies to:**

[All](#/{skin}/control) 

[All](#/{skin}/control)


**Format:** 


*width* 
 x
 *height* 



**Format:** 

**Format:**

*width* 
 x
 *height* 

*width*
*height*

 The size of this control.




 Setting 0 for width or height uses up any available space right/downward.




 If the control is a window, this refers to its
 *interior size when not maximized or minimized* 
 . That is, it does not count borders, titlebar, menu, or statusbar, and if the window is minimized/maximized, this refers to the window's normal size when it is restored. See the
 [inner-size](#/{skin}/param/inner-size) 
 and
 [outer-size](#/{skin}/param/outer-size) 
 params for comparison.



*interior size when not maximized or minimized*
[inner-size](#/{skin}/param/inner-size)
[outer-size](#/{skin}/param/outer-size)

 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true,
 
 size
 
 refers to the total scrollable size of the pane, NOT the smaller size displayed. In this case,
 
 outer-size
 
 and
 
 inner-size
 
 refer to the display area with and without scrollbars, respectively.



[can-scroll](#/{skin}/param/can-scroll)

 size


 outer-size


 inner-size



---





 drop-zone parameter (skin)
----------------------------




**See also:** 


[mouse handling](#/DM/mouse) 



**See also:** 

**See also:**

[mouse handling](#/DM/mouse) 

[mouse handling](#/DM/mouse)


**Applies to:** 


[All](#/{skin}/control) 



**Applies to:** 

**Applies to:**

[All](#/{skin}/control) 

[All](#/{skin}/control)


**Format:** 


 true/false
 


**Format:** 

**Format:**

 true/false



**Default value:** 



 true
 
 for
 [Grid](#/{skin}/control/grid) 
 ,
 [Info](#/{skin}/control/info) 
 ,
 [Map](#/{skin}/control/map) 


 false
 
 for everything else
 



**Default value:** 

**Default value:**


 true
 
 for
 [Grid](#/{skin}/control/grid) 
 ,
 [Info](#/{skin}/control/info) 
 ,
 [Map](#/{skin}/control/map) 


 false
 
 for everything else
 


 true

[Grid](#/{skin}/control/grid)
[Info](#/{skin}/control/info)
[Map](#/{skin}/control/map)


 false
 
 for everything else


 false


 True if dragged objects may be dropped here. Default is true for Map, Info, and Grid controls, false for others. When in use, this will be the value of the
 
 over\_control
 
 argument in
 [MouseDrop()](#/client/proc/MouseDrop) 
 if you drop an atom here.




 over\_control

[MouseDrop()](#/client/proc/MouseDrop)

 Grids can also add
 
 drag-cell
 
 and
 
 drop-cell
 
 to mouse proc parameters. The mouse procs'
 
 src\_location
 
 and
 
 over\_location
 
 arguments are in the form
 
 "[column],[row]"
 
 (or
 
 "[item"]
 
 if
 [is-list](#/{skin}/param/is-list) 
 is true) when dragging to/from a grid cell.




 drag-cell


 drop-cell


 src\_location


 over\_location


 "[column],[row]"


 "[item"]

[is-list](#/{skin}/param/is-list)

 In Info controls,
 
 src\_location
 
 and
 
 over\_location
 
 in mouse procs will be the name of the statpanel tab.




 src\_location


 over\_location



---



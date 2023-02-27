

 is-default parameter (skin)
-----------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 





**See also:** 

**See also:**

[id parameter](#/{skin}/param/id) 

[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 



[id parameter](#/{skin}/param/id)

[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 


[parent parameter](#/{skin}/param/parent)

[type parameter](#/{skin}/param/type) 

[type parameter](#/{skin}/param/type)


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


 false
 


**Default value:** 

**Default value:**

 false


 Specifies that this is a default control. This should be true for your main window, and for your primary map, info, output, input, and browser controls.




 The default control of a given type can be referenced in
 [winset()](#/proc/winset) 
 and other skin-related procs by the name
 
 ":
 *type* 
 "
 
 , e.g.
 
 ":map"
 
 .



[winset()](#/proc/winset)

 ":
 *type* 
 "

*type*

 ":map"


 Changing this value at runtime should be avoided, especially for windows. Results may be unpredictable.





---



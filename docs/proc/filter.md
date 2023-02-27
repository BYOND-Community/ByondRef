

 filter proc
-------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[Filter effects](#/{notes}/filters) 




**See also:** 

**See also:**

[filters var (atom)](#/atom/var/filters) 

[Filter effects](#/{notes}/filters) 


[filters var (atom)](#/atom/var/filters)

[Filter effects](#/{notes}/filters) 

[Filter effects](#/{notes}/filters)


**Format:** 


 filter(type = Type, parameter = Value, ...)
 


**Format:** 

**Format:**

 filter(type = Type, parameter = Value, ...)


 Creates a graphical filter that can be assigned or added to a list of
filters on an atom or image.




 This proc uses named arguments, and the "type" value must always be
included. To see which types of filters are available and what parameters
they accept, see
 [Filter effects](#/{notes}/filters) 
 .



[Filter effects](#/{notes}/filters)
### 
 Example:



 atom/proc/Highlight(apply)
 if(apply)
 filters = filter(type="outline", size=1, color=rgb(255,0,0))
 else
 filters = null


 A filter created with this proc is an
 *abstract* 
 filter; it is not
associated with any atom. When you add it to atom's filters, the atom gets a
copy of this filter, so changing the abstract filter's values afterward will
not change the atom's filters. For the same reason, an abstract filter can't
be animated.



*abstract*

 A filter that is part of an atom's filters list, like obj.filters[1], is an
 *attached* 
 filter. Changing the values for an attached filter will change
how that atom is displayed, and attached filters can be animated.



*attached*


---



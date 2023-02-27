

 EFFECTS\_LAYER
----------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 









**See also:** 

**See also:**

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 







[layer var (atom)](#/atom/var/layer)

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 






[plane var (atom)](#/atom/var/plane)

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 





[map\_format var (world)](#/world/var/map_format)

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 




[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER)

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 



[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER)

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 


[stddef.dm file](#/{{appendix}}/stddef%2edm)

[Understanding the renderer](#/{notes}/renderer) 

[Understanding the renderer](#/{notes}/renderer)

 This is mostly no longer needed. A negative value for plane is the
preferred way to do show objects in the background. It can still be used
however when you want to rearrange objects in the same plane when using
 [PLANE\_MASTER](#/atom/var/appearance_flags) 
 for visual
effects.



[PLANE\_MASTER](#/atom/var/appearance_flags)


 EFFECTS\_LAYER
 
 is a special high value that can be added to the
regular layer of any atom.




 EFFECTS\_LAYER


 The purpose of this value is to make an atom appear above any regular
atoms. For instance, in an isometric map if you want to display a character's
name below them, it does not make much sense to have nearer objects cover up
that name, so you can tell the name overlay to use
 
 EFFECTS\_LAYER +
MOB\_LAYER
 
 and it will show up on top of all the normal icons on the map.
This has been somewhat obviated by
 
 plane
 
 but may still be useful in
some cases.




 EFFECTS\_LAYER +
MOB\_LAYER


 plane


 When using this special layer, it should be added to the layer an atom
normally uses. For instance an obj should have a layer of
 
 EFFECTS\_LAYER +
OBJ\_LAYER
 
 .




 EFFECTS\_LAYER +
OBJ\_LAYER


 This can be mixed with
 
 TOPDOWN\_LAYER
 
 , in non-topdown map formats.
Anything in
 
 TOPDOWN\_LAYER
 
 will display on top of
 
 EFFECTS\_LAYER
 
 , and
 
 TOPDOWN\_LAYER + EFFECTS\_LAYER
 
 will be
above both.




 TOPDOWN\_LAYER


 TOPDOWN\_LAYER


 EFFECTS\_LAYER


 TOPDOWN\_LAYER + EFFECTS\_LAYER


 This can also be mixed with
 
 BACKGROUND\_LAYER
 
 , which takes priority
over everything else.




 BACKGROUND\_LAYER


 Images or overlays with
 
 FLOAT\_LAYER
 
 can be left alone. They will
automatically have the same layer as whatever atom they are attached to.




 FLOAT\_LAYER



---



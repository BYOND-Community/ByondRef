

 BACKGROUND\_LAYER
-------------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 









**See also:** 

**See also:**

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 







[layer var (atom)](#/atom/var/layer)

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 






[plane var (atom)](#/atom/var/plane)

[map\_format var (world)](#/world/var/map_format) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 





[map\_format var (world)](#/world/var/map_format)

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 




[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER)

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


 BACKGROUND\_LAYER
 
 is a special high value that can be added to the
regular layer of any atom.




 BACKGROUND\_LAYER


 The purpose of this value is to make an atom appear below any regular
atoms, even if they share the same plane. In an isometric map for instance,
HUD objects will always appear above the map, but makeing a HUD object appear
behind the map was basically impossible without this feature until
 
 plane
 
 was implemented.




 plane


 When using this special layer, it should be added to the layer an atom
normally uses. For instance an obj should have a layer of
 
 BACKGROUND\_LAYER
+ OBJ\_LAYER
 
 .




 BACKGROUND\_LAYER
+ OBJ\_LAYER


 This can be mixed with
 
 TOPDOWN\_LAYER
 
 and
 
 EFFECTS\_LAYER
 
 ,
but it will take precedence over both. Anything with
 
 BACKGROUND\_LAYER
 
 will always appear below anything without it on the same plane.




 TOPDOWN\_LAYER


 EFFECTS\_LAYER


 BACKGROUND\_LAYER


 Images or overlays with
 
 FLOAT\_LAYER
 
 can be left alone. They will
automatically have the same layer as whatever atom they are attached to.




 FLOAT\_LAYER



---





 TOPDOWN\_LAYER
----------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







**See also:** 

**See also:**

[layer var (atom)](#/atom/var/layer) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 





[layer var (atom)](#/atom/var/layer)

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 




[map\_format var (world)](#/world/var/map_format)

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 



[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER)

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 


[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER)

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[stddef.dm file](#/{{appendix}}/stddef%2edm)

 TOPDOWN\_LAYER is a special high value that can be added to the regular layer
of any atom. This is only available when using a non-topdown world.map\_format,
such as isometric mapping.




 The purpose of this value is to make an atom appear as if it belongs in a
top-down map, when using a map\_format other than TOPDOWN\_MAP or TILED\_ICON\_MAP.
This can be handy for title screens, or for special battle maps or the inside
of a building in an RPG.




 When using this special layer, it should be added to the layer an atom
normally uses. For instance a turf should have a layer of TOPDOWN\_LAYER +
TURF\_LAYER. Usually you will want one part of the map to have TOPDOWN\_LAYER,
and for players to be unable to walk to there from the regular map. Mixing
topdown icons and icons in the normal map\_format in view of each other could
look very strange. For safety's sake, the easiest thing to do is to keep them
on separate z layers.




 This can be mixed with EFFECTS\_LAYER. Anything in TOPDOWN\_LAYER will
display on top of EFFECTS\_LAYER, and TOPDOWN\_LAYER + EFFECTS\_LAYER will be
above both.




 This can also be mixed with BACKGROUND\_LAYER, which takes priority over
everything else.




 Images or overlays with FLOAT\_LAYER can be left alone. They will
automatically have the same layer as whatever atom they are attached to.





---



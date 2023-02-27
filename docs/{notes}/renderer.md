

 Understanding the renderer
----------------------------



 .renderlist {position: relative; display: inline-block; margin-left: 3em; text-align: center;}
 .renderlist-label, .renderlist-caption, .renderlist-note {display: block; margin: 3px 0; width: 100%;}
 .renderlist-caption {font-size: 1.1em; font-weight: bold;}
 .renderlist-note {font-size: 0.9em;}
 .renderlist-box {background: #eee; border: 1px solid #333; padding: 3px 10px; margin: 3px 0; border-radius: 10px;}
 body.dark .renderlist-box {color: white; background: #333; border-color: #aaa;}
 .renderlist-box .renderlist-box {background: #ddd; width: 100%;}
 body.dark .renderlist-box .renderlist-box {background: #444; width: 100%;}
 .renderlist-box .renderlist-box .renderlist-box {background: #ccc;}
 body.dark .renderlist-box .renderlist-box .renderlist-box {background: #555;}


 To get the most out of BYOND's visual effects, it helps to understand how
the map is displayed.




 Every atom has an
 [appearance](#/atom/var/appearance) 
 that holds
all of its visual info (and sometimes a little non-visual info). This
appearance has to be turned into sprites in order to be rendered.



[appearance](#/atom/var/appearance)

 Although many atoms need little more than a simple
 [icon](#/atom/var/icon) 
 and
 [icon\_state](#/atom/var/icon_state) 
 and produce only a
single sprite, some are more complex with overlays, underlays, maptext, etc.
Also there may be
 [image objects](#/image) 
 and
 [visual contents](#/atom/var/vis_contents) 
 involved, although
they're not part of the atom's appearance.



[icon](#/atom/var/icon)
[icon\_state](#/atom/var/icon_state)
[image objects](#/image)
[visual contents](#/atom/var/vis_contents)

 For a simple
 
 icon
 
 and
 
 icon\_state
 
 , just one sprite is
generated. The client looks up the icon it's given. Then it looks up an icon
state, which may be influenced by whether the atom is moving or not since you
can have moving and non-moving icon states. Then it determines which
 [direction](#/atom/var/dir) 
 to draw and which frame of the icon's
animation (if any) to use.




 icon


 icon\_state

[direction](#/atom/var/dir)

 So with several simple icons, and not worrying about layers for now, a list
of sprites lays out like this:





 Atom #1
 

 Atom #2
 

 &vellip;
 

 Atom #N
 


 Atom #1


 Atom #2


 &vellip;


 Atom #N

### 
 Overlays and underlays



 Now let's consider what happens when an appearance has overlays.





 Underlay #1
 

 &vellip;
 

 Underlay #N
 

 Main icon
 

 Overlay #1
 

 &vellip;
 

 Overlay #N
 


 Underlay #1


 &vellip;


 Underlay #N


 Main icon


 Overlay #1


 &vellip;


 Overlay #N


 The
 [underlays](#/atom/var/underlays) 
 list is processed
first, then
 [overlays](#/atom/var/overlays) 
 . These lists
contain appearances themselves, rather than actual atoms. This means that
overlays are recursive: an overlay can have overlays itself. To picture how
that works, just replace
one of the overlays above with another list.



[underlays](#/atom/var/underlays)
[overlays](#/atom/var/overlays)


 Underlay #1
 

 Underlay #2
 

 Main icon
 

 Underlays of overlay #1
 

 Overlay #1 icon
 

 Overlays of overlay #1
 

 Overlay #2
 


 Underlay #1


 Underlay #2


 Main icon


 Underlays of overlay #1


 Overlay #1 icon


 Overlays of overlay #1


 Overlay #2

### 
 Image objects and visual contents



 Any atom can have an
 [image object](#/image) 
 attached, which can
be shown to only specific players. Most atoms, and image objects, can have
 [visual contents](#/atom/var/vis_contents) 
 that display other atoms
as if they're overlays.



[image object](#/image)
[visual contents](#/atom/var/vis_contents)


 Underlays
 

 Main icon
 

 Overlays
 

 Image objects
 

 Visual contents
 


 Underlays


 Main icon


 Overlays


 Image objects


 Visual contents


 As you see this is very similar to overlays. Just like overlays, image
objects and visual contents have appearances of their own (and may also have
their own images or visual contents), so this may be recursive as they add
new overlays, etc.




 A couple of things to keep in mind:



* If an image object uses the
 [override](#/atom/var/override) 
 var, it will replace the main appearance's icon and overlays, although it
 won't replace other images or visual contents.
* An object in visual contents can use
 [vis\_flags](#/atom/var/vis_flags) 
 to set
 
 VIS\_UNDERLAY
 
 and move itself before the parent's underlays.


- If an image object uses the
 [override](#/atom/var/override) 
 var, it will replace the main appearance's icon and overlays, although it
 won't replace other images or visual contents.

[override](#/atom/var/override)
- An object in visual contents can use
 [vis\_flags](#/atom/var/vis_flags) 
 to set
 
 VIS\_UNDERLAY
 
 and move itself before the parent's underlays.

[vis\_flags](#/atom/var/vis_flags)

 VIS\_UNDERLAY

### 
 Maptext and particles



 Any appearance may have
 [maptext](#/atom/var/maptext) 
 attached. That maptext draws above the icon but is grouped with it. That
grouping will be discussed further below.



[maptext](#/atom/var/maptext)

 Particle effects also get grouped with the main icon in a similar way to
maptext.




 For simplicity, from this point forward the diagram will just treat underlays,
overlays, image objects, and visual contents as overlays.






 Main icon
 

 Maptext
 

 Particles
 


 Overlays
 



 Main icon
 

 Maptext
 

 Particles
 


 Main icon


 Maptext


 Particles


 Overlays

### 
 Color, transform, and filters



 An appearance's
 [color](#/atom/var/color) 
 and
 [alpha](#/atom/var/alpha) 
 vars (from here forwarded
they'll just be referred to by
 
 color
 
 ) and
 [transform](#/atom/var/transform) 
 are inherited by any
overlays, which also includes images and visual contents. You can avoid that
inheritance by giving those overlays special
 [appearance\_flags](#/var/appearance_flags) 
 :
 
 RESET\_COLOR
 
 ,
 
 RESET\_ALPHA
 
 , and
 
 RESET\_TRANSFORM
 
 .



[color](#/atom/var/color)
[alpha](#/atom/var/alpha)

 color

[transform](#/atom/var/transform)
[appearance\_flags](#/var/appearance_flags)

 RESET\_COLOR


 RESET\_ALPHA


 RESET\_TRANSFORM


 The appearance's filters are only applied to the main icon.






 Main icon
 

 Maptext
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 



 Overlays
 


 color
 
 and
 
 transform
 
 are inherited from Main
   


 filters
 
 are not inherited from Main
 




 Main icon
 

 Maptext
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 


 Main icon


 Maptext


 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply


 color


 transform


 filters



 Overlays
 


 color
 
 and
 
 transform
 
 are inherited from Main
   


 filters
 
 are not inherited from Main
 


 Overlays



 color
 
 and
 
 transform
 
 are inherited from Main
   


 filters
 
 are not inherited from Main


 color


 transform

  


 filters


 When
 
 color
 
 and
 
 transform
 
 are inherited, they "stack". The
inherited color and transform values are applied after those of the overlays.




 color


 transform

### 

 KEEP\_TOGETHER
 
 and
 
 KEEP\_APART



 KEEP\_TOGETHER


 KEEP\_APART


 There are times it's desirable for an appearance and all its overlays to be
treated as a single unit so any colors or filters can be applied all at once.
One simple example is if the appearance has an
 
 alpha
 
 of 128 to make it
translucent, you probably want to draw the whole atom faded instead of drawing
each sprite faded, one on top of the other.




 alpha


 By using the
 
 KEEP\_TOGETHER
 
 value in
 [appearance\_flags](#/var/appearance_flags) 
 (called KT for
short), an appearance will group all of its underlays and overlays together.
If this is an atom with image objects and visual contents, those will be
grouped with it as well.




 KEEP\_TOGETHER

[appearance\_flags](#/var/appearance_flags)



 KT group
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 


 Main icon
 

 Maptext
 


 Overlays
 




 KT group
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 


 Main icon
 

 Maptext
 


 Overlays
 


 KT group


 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply


 color


 transform


 filters



 Main icon
 

 Maptext
 


 Main icon


 Maptext


 Overlays


 With
 
 KEEP\_TOGETHER
 
 all of these sprites are rendered to a
temporary drawing surface, and then the main appearance's
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 are all applied to the combined
drawing. This comes with a trade-off, since you can no longer use flags
such as
 
 RESET\_COLOR
 
 to opt out of inheritance.




 KEEP\_TOGETHER


 color


 transform


 filters


 RESET\_COLOR


 If an overlay doesn't want to be part of a KT group, it can use the
 
 KEEP\_APART
 
 flag (KA for short). If there are multiple nested
KT groups, KA will only escape the innermost group.




 KEEP\_APART


 If an overlay inside a KT group has a different
 [plane](#/atom/var/plane) 
 than the group's owner, it
will be separated as if it defined
 
 KEEP\_APART
 
 , except it can
escape multiple nested groups.



[plane](#/atom/var/plane)

 KEEP\_APART

### 
 Layers and planes



 Any appearance can have a
 [layer](#/atom/var/layer) 
 or
 [plane](#/atom/var/layer) 
 , and these influence how
it gets sorted. (There's also a concept called a "sub-plane" that's
influenced by whether an atom is a
 [HUD/screen object](#/{notes}/HUD) 
 or special layers like
 [BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 
 .)



[layer](#/atom/var/layer)
[plane](#/atom/var/layer)
[HUD/screen object](#/{notes}/HUD)
[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER)

 If a sprite is created with
 
 FLOAT\_LAYER
 
 (any negative value
counts as a floating layer) its layer has to be resolved, or "unfloated".
The main sprite for an atom can never float; it has to have a real layer.
Its overlays and underlays with floating layers will reorder themselves in
numerical order, then look for the next closest sprites in the rendering
list that has a non-negative layer.




 FLOAT\_LAYER


 A similar process happens with
 
 FLOAT\_PLANE
 
 . Planes can have
negative values but
 
 FLOAT\_PLANE
 
 and the values close to it are
special. Sprites with floating planes have to resolve those as well.




 FLOAT\_PLANE


 FLOAT\_PLANE


 Once all atoms that will appear on the map are assembled into a rendering
list of sprites, the order in which they're rendered on the map is determined
in this order:



1. The
 
 plane
 
 var matters most.
2. Subplane is counted next. E.g., HUD objects render above non-HUD objects.
3. Depending on
 [world.map\_format](#/world/var/map_format) 
 ,
 
 layer
 
 or physical position determine the drawing order from here.
4. After everything else has been checked, the order the sprites were generated in is the final tie-breaker.


- The
 
 plane
 
 var matters most.


 plane

- Subplane is counted next. E.g., HUD objects render above non-HUD objects.

- Depending on
 [world.map\_format](#/world/var/map_format) 
 ,
 
 layer
 
 or physical position determine the drawing order from here.

[world.map\_format](#/world/var/map_format)

 layer

- After everything else has been checked, the order the sprites were generated in is the final tie-breaker.


 In a typical topdown map,
 
 layer
 
 is basically all that matters
after the plane and subplane are taken into account. There is a legacy
concept called micro-layers that helps break ties between sprites with the
same layer; for instance if an atom is moving it's usually desirable to
draw it above other atoms with the same layer; this applies only to topdown
maps.




 layer

### 
 Plane masters



 Sometimes it's helpful to group multiple sprites on one plane as if the
plane itself were a KT group. For this,
 [appearance\_flags](#/var/appearance_flags) 
 has a value
called
 
 PLANE\_MASTER
 
 . An object with this flag will act as a "parent"
for everything else on the plane. All other sprites on the plane will be
grouped together and rendered on a temporary drawing surface, and then the
plane master's
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 will
be applied.



[appearance\_flags](#/var/appearance_flags)

 PLANE\_MASTER


 color


 transform


 filters


 A plane master does not, however, get an icon or maptext of its own;
they're simply ignored. It can have overlays added to the group.



### 
 Advanced topics



 There are other topics not covered in this article, such as
 [render targets](#/atom/var/render_target) 
 and special map formats.
Any details on how those features impact rendering are discussed in their
own articles.



[render targets](#/atom/var/render_target)


---



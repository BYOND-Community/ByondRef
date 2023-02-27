

 RenderIcon proc (client)
--------------------------




**See also:** 


[vis\_contents var (atom)](#/atom/var/vis_contents) 

[Filter effects](#/{notes}/filters) 




**See also:** 

**See also:**

[vis\_contents var (atom)](#/atom/var/vis_contents) 

[Filter effects](#/{notes}/filters) 


[vis\_contents var (atom)](#/atom/var/vis_contents)

[Filter effects](#/{notes}/filters) 

[Filter effects](#/{notes}/filters)


**Format:** 


 RenderIcon(object)
 


**Format:** 

**Format:**

 RenderIcon(object)



**Args:** 


 object: An atom or appearance to render.
 


**Args:** 

**Args:**

 object: An atom or appearance to render.



**Returns:** 


 A single-image icon file in which the object is rendered with all its
overlays, visual contents, etc.
 


**Returns:** 

**Returns:**

 A single-image icon file in which the object is rendered with all its
overlays, visual contents, etc.


 Use this proc to render an atom or an appearance as a single icon. This is
a client proc because the server is not capable of rendering anything on its
own.




 Any overlays, image objects known to this client that are attached to the
object, visual contents, maptext, and so on will be included in the render.
The returned icon is sized to fit all of the above, and to include room for
any expansion due to filter effects.



### 
 Example:



 mob/proc/GetFlatIcon()
 return client?.RenderIcon(src)


 Important notes regarding this proc:



* The returned icon is a cache file,
 *not* 
 an
 
 /icon
 
 datum.
* If
 
 object
 
 is an
 [/image
 
 object](#/image) 
 , the
 image must be known to the client. Otherwise the return value is null.
* If this object doesn't appear on the client's map, it will be sent to them
 on the next map tick, along with any visual contents. The server will hold a
 reference to the object until the map tick ends, so an object you create
 temporarily should remain valid long enough to be rendered.
* [render\_source](#/atom/var/render_source) 
 will not
 work unless the corresponding
 [render\_target](#/atom/var/render_target) 
 appears in the
 same render stack. That is, this object or appearance will be rendered in an
 isolated "scene" rather than as part of the map, so it won't be able to use
 other objects on the map as render sources.


- The returned icon is a cache file,
 *not* 
 an
 
 /icon
 
 datum.

*not*

 /icon

- If
 
 object
 
 is an
 [/image
 
 object](#/image) 
 , the
 image must be known to the client. Otherwise the return value is null.


 object

[/image
 
 object](#/image)

 /image

- If this object doesn't appear on the client's map, it will be sent to them
 on the next map tick, along with any visual contents. The server will hold a
 reference to the object until the map tick ends, so an object you create
 temporarily should remain valid long enough to be rendered.

- [render\_source](#/atom/var/render_source) 
 will not
 work unless the corresponding
 [render\_target](#/atom/var/render_target) 
 appears in the
 same render stack. That is, this object or appearance will be rendered in an
 isolated "scene" rather than as part of the map, so it won't be able to use
 other objects on the map as render sources.

[render\_source](#/atom/var/render_source)
[render\_target](#/atom/var/render_target)


---



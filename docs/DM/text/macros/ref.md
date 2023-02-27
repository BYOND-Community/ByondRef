

 ref text macro
----------------




**See also:** 


[Topic proc (client)](#/client/proc/Topic) 

[icon text macro](#/DM/text/macros/icon) 

[locate proc](#/proc/locate) 

[macros (text)](#/DM/text/macros) 

[tag var (datum)](#/datum/var/tag) 







**See also:** 

**See also:**

[Topic proc (client)](#/client/proc/Topic) 

[icon text macro](#/DM/text/macros/icon) 

[locate proc](#/proc/locate) 

[macros (text)](#/DM/text/macros) 

[tag var (datum)](#/datum/var/tag) 





[Topic proc (client)](#/client/proc/Topic)

[icon text macro](#/DM/text/macros/icon) 

[locate proc](#/proc/locate) 

[macros (text)](#/DM/text/macros) 

[tag var (datum)](#/datum/var/tag) 




[icon text macro](#/DM/text/macros/icon)

[locate proc](#/proc/locate) 

[macros (text)](#/DM/text/macros) 

[tag var (datum)](#/datum/var/tag) 



[locate proc](#/proc/locate)

[macros (text)](#/DM/text/macros) 

[tag var (datum)](#/datum/var/tag) 


[macros (text)](#/DM/text/macros)

[tag var (datum)](#/datum/var/tag) 

[tag var (datum)](#/datum/var/tag)

 The
 `\ref` 
 text macro inserts a unique identification number
or text string for the following embedded object (inside []'s).



`\ref`

 In older versions of BYOND, if an object had a tag, that was used instead.
However this has often proved to be problematic, so anything compiled from
version 512 onward should expect to output a reference number. If you want
to use the tag, which stands a better chance of still being valid if the
object is deleted and recreated (like in a world reboot), you can output the
object's tag explicitly.




 The primary use for object references embedded in text is in topic links.
This allows you to encode a reference to an object in the href value of a
hyperlink. (Just make sure the object does not get deleted before the user
executes the link. See
 [garbage collection](#/DM/garbage) 
 .)



[garbage collection](#/DM/garbage)

 Topic links that contain a parameter "src" assigned to an object reference
are treated somewhat specially. Unless you override client.Topic() to do
otherwise, the default behavior is to call the referenced object's own Topic()
procedure.



### 
 Example:



 mob/verb/test()
 usr << "Click
 [here](?src=\ref[src];action=start) 
 !"
mob/Topic(href,href\_list[])
 switch(href\_list["action"])
 if("start")
 usr << "Starting the game..."
 else
 return ..()

[here](?src=\ref[src];action=start)

 The above example uses an embedded reference to the player's own mob to
create a link to a topic handled by that mob's Topic() proc. The
 `href_list` 
 parameter is simply the result of
 `params2list(href)` 
 .



`href_list`
`params2list(href)`

 In that example, the embedded reference was automatically converted back
into an object (dereferenced) for you. If you embed references to additional
objects in the href data, you would have to dereference those yourself using
the locate() instruction.





---



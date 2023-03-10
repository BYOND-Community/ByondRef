

 Topic proc (client)
---------------------




**See also:** 


[New proc (client)](#/client/proc/New) 

[Topic proc (datum)](#/datum/proc/Topic) 

[link proc](#/proc/link) 

[ref text macro](#/DM/text/macros/ref) 






**See also:** 

**See also:**

[New proc (client)](#/client/proc/New) 

[Topic proc (datum)](#/datum/proc/Topic) 

[link proc](#/proc/link) 

[ref text macro](#/DM/text/macros/ref) 




[New proc (client)](#/client/proc/New)

[Topic proc (datum)](#/datum/proc/Topic) 

[link proc](#/proc/link) 

[ref text macro](#/DM/text/macros/ref) 



[Topic proc (datum)](#/datum/proc/Topic)

[link proc](#/proc/link) 

[ref text macro](#/DM/text/macros/ref) 


[link proc](#/proc/link)

[ref text macro](#/DM/text/macros/ref) 

[ref text macro](#/DM/text/macros/ref)


**Format:** 


 Topic(href,href\_list[],hsrc)
 


**Format:** 

**Format:**

 Topic(href,href\_list[],hsrc)



**When:** 


 Called when a player connects to a world with a "connection topic" or
 when the player runs a hyperlink in the current world by clicking one
 embedded in text or generated by the link() instruction.
 


**When:** 

**When:**

 Called when a player connects to a world with a "connection topic" or
 when the player runs a hyperlink in the current world by clicking one
 embedded in text or generated by the link() instruction.



**Args:** 


 href: The topic text (everything after the '?' in the full href).
 
 href\_list: List of key/value pairs in href (produced from params2list(href)).
 
 hsrc: The object referenced by the "src" parameter in href or null if none.
 




**Args:** 

**Args:**

 href: The topic text (everything after the '?' in the full href).
 
 href\_list: List of key/value pairs in href (produced from params2list(href)).
 
 hsrc: The object referenced by the "src" parameter in href or null if none.
 



 href\_list: List of key/value pairs in href (produced from params2list(href)).
 
 hsrc: The object referenced by the "src" parameter in href or null if none.
 


 hsrc: The object referenced by the "src" parameter in href or null if none.



**Default action:** 


 Call the hsrc object's own Topic() proc.
 


**Default action:** 

**Default action:**

 Call the hsrc object's own Topic() proc.


 The following example uses a very simple href value.



### 
 Example:



 mob/Login()
 src << "Click
 [here](?source) 
 to download the source code."
 return ..()

client/Topic(href)
 if(href == "source")
 usr << file("world.dm")
 usr << file("world.rsc")
 else ..()

[here](?source)

 Be sure to call the default handler unless you want to prevent rerouting
of topics to other objects.




 Always validate the input in
 
 Topic()
 
 calls
to make sure it's correct and the query you're recieving is legitimate. For
security reasons, you will probably want to control which objects a player has
access to, since a player could spoof a topic link containing any arbitrary
object reference. (Never trust those sneaky players!)




 Topic()


 The next example demonstrates an href that gets handled by another object.
This is how you would normally want to do things. It is best not to override
client/Topic() (as in the example above) unless you need to intervene in the
low-level details of routing the request to the right object.




 You specify the object that will handle the request by using a parameter
called "src".



### 
 Example:



 mob/Login()
 src << "Click
 [here](?src=\ref[src];action=startgame) 
 to start."
 return ..()

mob/Topic(href,href\_list[])
 switch(href\_list["action"])
 if("startgame")
 usr << "Starting game..."
 else
 return ..()

[here](?src=\ref[src];action=startgame)

 Although it is slightly more complex, the use of the parameter list allows
you to easily include extra data and new functionality. Just remember that
the data in the list is always stored as text, so if you are expecting a
number or an object, you must convert it yourself (with text2num(), locate(),
or whatever).





---



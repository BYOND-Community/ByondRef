

 New proc (client)
-------------------




**See also:** 


[Export proc (client)](#/client/proc/Export) 

[Import proc (client)](#/client/proc/Import) 

[Login proc (mob)](#/mob/proc/Login) 

[New proc (datum)](#/datum/proc/New) 

[Topic proc (client)](#/client/proc/Topic) 

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 









**See also:** 

**See also:**

[Export proc (client)](#/client/proc/Export) 

[Import proc (client)](#/client/proc/Import) 

[Login proc (mob)](#/mob/proc/Login) 

[New proc (datum)](#/datum/proc/New) 

[Topic proc (client)](#/client/proc/Topic) 

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 







[Export proc (client)](#/client/proc/Export)

[Import proc (client)](#/client/proc/Import) 

[Login proc (mob)](#/mob/proc/Login) 

[New proc (datum)](#/datum/proc/New) 

[Topic proc (client)](#/client/proc/Topic) 

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 






[Import proc (client)](#/client/proc/Import)

[Login proc (mob)](#/mob/proc/Login) 

[New proc (datum)](#/datum/proc/New) 

[Topic proc (client)](#/client/proc/Topic) 

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 





[Login proc (mob)](#/mob/proc/Login)

[New proc (datum)](#/datum/proc/New) 

[Topic proc (client)](#/client/proc/Topic) 

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 




[New proc (datum)](#/datum/proc/New)

[Topic proc (client)](#/client/proc/Topic) 

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 



[Topic proc (client)](#/client/proc/Topic)

[mob var (world)](#/world/var/mob) 

[savefile](#/savefile) 


[mob var (world)](#/world/var/mob)

[savefile](#/savefile) 

[savefile](#/savefile)


**Format:** 


 New(TopicData)
 


**Format:** 

**Format:**

 New(TopicData)



**Returns:** 


 The newly connected mob, client.mob, or null to disallow the connection.
 


**Returns:** 

**Returns:**

 The newly connected mob, client.mob, or null to disallow the connection.



**When:** 


 Called when the player first tries to connect to the world.
 


**When:** 

**When:**

 Called when the player first tries to connect to the world.



**Args:** 


 usr: The mob in the world with the same key as the player, if it exists.
 
 TopicData: If the player accessed the world with a "connection topic",
 this is the topic text. Otherwise it is null.
 



**Args:** 

**Args:**

 usr: The mob in the world with the same key as the player, if it exists.
 
 TopicData: If the player accessed the world with a "connection topic",
 this is the topic text. Otherwise it is null.
 


 TopicData: If the player accessed the world with a "connection topic",
 this is the topic text. Otherwise it is null.



**Default action:** 


 Look for an existing mob with the same key as the player. If found,
 connect the player to that mob (mob.Login()). Otherwise, look for a
 prototype mob with the same key as the player. If found, create a mob of
 that type and connect the player to it. Otherwise, create a mob of type
 world.mob, give it the same name and gender as the player's key, and
 connect the player to it. If TopicData is not null, call
 client.Topic(TopicData). Finally, the player's mob is returned.
 


**Default action:** 

**Default action:**

 Look for an existing mob with the same key as the player. If found,
 connect the player to that mob (mob.Login()). Otherwise, look for a
 prototype mob with the same key as the player. If found, create a mob of
 that type and connect the player to it. Otherwise, create a mob of type
 world.mob, give it the same name and gender as the player's key, and
 connect the player to it. If TopicData is not null, call
 client.Topic(TopicData). Finally, the player's mob is returned.


 This is a fairly low-level procedure that you would only want to override
if you cannot accomplish the same thing in
 `mob/Login()` 
 or
 `mob/New()` 
 . One reason to override
 `client/New()` 
 is
if player mobs are created from a savefile. In that case, you don't need a
temporary mob to be created first.



`mob/Login()`
`mob/New()`
`client/New()`
### 
 Example:



 client/New()
 if(usr) return ..() //reconnecting to existing mob
 else
 var/player\_sav = "players/[ckey].sav"
 if(length(file(player\_sav))) //if player savefile exists
 var/savefile/F = new(player\_sav) //open it
 F >> usr //create saved mob
 return ..() //creates a new mob if necessary
mob/Logout()
 var/player\_sav = "players/[ckey].sav"
 var/savefile/F = new(player\_sav)
 F << src
 del src


 If you want to do any user-interaction before loading the saved mob, you
will have to create a temporary mob first in order to interact with the
player. In that case, you are better off doing things in
 `mob/Login()` 
 , rather than
 `client/New()` 
 .



`mob/Login()`
`client/New()`

 Note that for the above example to work, you
 **must** 
 make
proper use of the
 [tmp](#/var/tmp) 
 flag when defining new object
variables. Otherwise, this can end up sucking large portions of your world
into each player savefile, which can have all sorts of unexpected
consequences!



**must**
[tmp](#/var/tmp)


---



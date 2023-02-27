

 IsSubscribed proc (world)
---------------------------




**Format:** 


 IsSubscribed(player)
 
 IsSubscribed(player, "BYOND") (to check BYOND Membership)
 



**Format:** 

**Format:**

 IsSubscribed(player)
 
 IsSubscribed(player, "BYOND") (to check BYOND Membership)
 


 IsSubscribed(player, "BYOND") (to check BYOND Membership)



**Returns:** 


 Number of days left in subscription, -1 for a lifetime subscriber,
 *or* 
 null if hub contact failed
 


**Returns:** 

**Returns:**

 Number of days left in subscription, -1 for a lifetime subscriber,
 *or* 
 null if hub contact failed

*or*


**Args:** 


 player: a mob, client, key, or ckey
 


**Args:** 

**Args:**

 player: a mob, client, key, or ckey


 Checks a player for their subscription status to this game. This is a
simpler alternative to
 
 client.CheckPassport()
 
 , which is deprecated,
and also allows you to check even when the player has gone offline.




 client.CheckPassport()


 This proc will return null if contacting the hub was required, but there
was no way to reach the hub. Contacting the hub may take a few moments, so it
is a good idea to use
 [spawn()](#/proc/spawn) 
 to avoid
holding up the rest of the game.



[spawn()](#/proc/spawn)
### 
 Example:



 mob/verb/JoinClub()
 if(!world.IsSubscribed(src))
 src << "Sorry, the club is only for subscribers."
 else
 // go to the turf with the tag "clubhouse"
 loc = locate("clubhouse")
 src << "Welcome to the clubhouse!"


 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.





---



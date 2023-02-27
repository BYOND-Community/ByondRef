

 GetMedal proc (world)
-----------------------




**See also:** 


[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 






**See also:** 

**See also:**

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 




[SetMedal proc (world)](#/world/proc/SetMedal)

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 



[ClearMedal proc (world)](#/world/proc/ClearMedal)

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 


[GetScores proc (world)](#/world/proc/GetScores)

[SetScores proc (world)](#/world/proc/SetScores) 

[SetScores proc (world)](#/world/proc/SetScores)


**Format:** 


 GetMedal(medal, player)
 


**Format:** 

**Format:**

 GetMedal(medal, player)



**Returns:** 


 1 if the medal has been earned by the player
 
 0 if the medal has not been earned
 
 A list of medals in list2params() format if checking all medals
 
 null if the hub cannot be contacted
 





**Returns:** 

**Returns:**

 1 if the medal has been earned by the player
 
 0 if the medal has not been earned
 
 A list of medals in list2params() format if checking all medals
 
 null if the hub cannot be contacted
 




 0 if the medal has not been earned
 
 A list of medals in list2params() format if checking all medals
 
 null if the hub cannot be contacted
 



 A list of medals in list2params() format if checking all medals
 
 null if the hub cannot be contacted
 


 null if the hub cannot be contacted



**Args:** 


 medal: name of the medal being checked
 
 player: a mob, client, key, or ckey
 



**Args:** 

**Args:**

 medal: name of the medal being checked
 
 player: a mob, client, key, or ckey
 


 player: a mob, client, key, or ckey


 Checks to see if a medal has been awarded to the player in question. If
the medal has been awarded, the return value is 1. If not, 0.




 You can also use GetMedal() to read a list of all medals a player has
earned for the hub entry, by leaving the medal argument blank. If you also
leave the player argument blank, you will get a list of all medals available
to the hub entry. In both cases the result can be parsed with params2list().




 This proc will return null if there was no way to reach the hub or
otherwise verify the medal's status. Use isnull() to check for a null value.




 Whenever possible, GetMedal() will avoid contacting the hub by using the
information it was given when the user logged in. If contacting the hub is
required, the proc may take a few moments to return a result. It is a good
idea to use spawn() to avoid holding up the rest of the game.



### 
 Example:



 turf/medal\_door
 density = 1
 icon\_state = "closed"
 var/medal = "Dragon slayer"

 verb/Knock()
 usr << "
 **Guard:** 
 Just checking your credentials...."
 var/hasmedal = world.GetMedal(medal, usr)
 if(hasmedal)
 usr << "
 **Guard:** 
 Go right in."
 icon\_state = "open"
 density = 0
 else if(!isnull(hasmedal))
 usr << "
 **Guard:** 
 Sorry, no admittance without a
 **[medal]** 
 badge."
 else
 usr << "
 **Guard:** 
 Sorry, I lost the paperwork. Try again later."

**Guard:**
**Guard:**
**Guard:**
**[medal]**
**Guard:**

 You can add an optional hub path argument if you want to look at a medal
for a different hub entry.





---





 ClearMedal proc (world)
-------------------------




**See also:** 


[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 






**See also:** 

**See also:**

[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 




[GetMedal proc (world)](#/world/proc/GetMedal)

[SetMedal proc (world)](#/world/proc/SetMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 



[SetMedal proc (world)](#/world/proc/SetMedal)

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 


[GetScores proc (world)](#/world/proc/GetScores)

[SetScores proc (world)](#/world/proc/SetScores) 

[SetScores proc (world)](#/world/proc/SetScores)


**Format:** 


 ClearMedal(medal, player)
 


**Format:** 

**Format:**

 ClearMedal(medal, player)



**Returns:** 


 1 if the medal was rescinded successfully, 0 or null otherwise.
 


**Returns:** 

**Returns:**

 1 if the medal was rescinded successfully, 0 or null otherwise.



**Args:** 


 medal: name of the medal being rescinded
 
 player: a mob, client, key, or ckey
 



**Args:** 

**Args:**

 medal: name of the medal being rescinded
 
 player: a mob, client, key, or ckey
 


 player: a mob, client, key, or ckey


 Removes a medal from a player. The proc will return 1 if it is successful, or
0 if the medal was not already awarded. If the world already knows this medal was
not earned, the hub will not be contacted.




 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is a good idea to use spawn() to avoid holding up the rest of
the game.



### 
 Example:



 mob/NPC
 Die(mob/killer) // assume Die() is a proc all mobs have
 spawn()
 if(ismob(killer) && killer.key)
 world.ClearMedal("Pacifist", killer)


 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.





---



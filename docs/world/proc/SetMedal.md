

 SetMedal proc (world)
-----------------------




**See also:** 


[GetMedal proc (world)](#/world/proc/GetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 






**See also:** 

**See also:**

[GetMedal proc (world)](#/world/proc/GetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 




[GetMedal proc (world)](#/world/proc/GetMedal)

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


 SetMedal(medal, player)
 


**Format:** 

**Format:**

 SetMedal(medal, player)



**Returns:** 


 1 if the medal was awarded successfully, 0 or null otherwise.
 


**Returns:** 

**Returns:**

 1 if the medal was awarded successfully, 0 or null otherwise.



**Args:** 


 medal: name of the medal being awarded
 
 player: a mob, client, key, or ckey
 



**Args:** 

**Args:**

 medal: name of the medal being awarded
 
 player: a mob, client, key, or ckey
 


 player: a mob, client, key, or ckey


 Awards a medal to a player. The proc will return 1 if it is successful, or
0 if the medal was already awarded. If the world already knows this medal was
earned before, the hub will not be contacted.




 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is a good idea to use spawn() to avoid holding up the rest of
the game.



### 
 Example:



 mob/monster/dragon
 Die(mob/killer) // assume Die() is a proc all mobs have
 spawn()
 if(ismob(killer) && killer.key)
 world.SetMedal("Dragon slayer", killer)


 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.





---



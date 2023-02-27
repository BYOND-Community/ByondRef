

 AddCredits proc (world)
-------------------------




**See also:** 


[GetCredits proc (world)](#/world/proc/GetCredits) 

[PayCredits proc (world)](#/world/proc/PayCredits) 




**See also:** 

**See also:**

[GetCredits proc (world)](#/world/proc/GetCredits) 

[PayCredits proc (world)](#/world/proc/PayCredits) 


[GetCredits proc (world)](#/world/proc/GetCredits)

[PayCredits proc (world)](#/world/proc/PayCredits) 

[PayCredits proc (world)](#/world/proc/PayCredits)


**Format:** 


 AddCredits(player, credits, note)
 


**Format:** 

**Format:**

 AddCredits(player, credits, note)



**Returns:** 


 1 if the credits were added successfully, 0 or null otherwise.
 


**Returns:** 

**Returns:**

 1 if the credits were added successfully, 0 or null otherwise.



**Args:** 


 player: a mob, client, key, or ckey
 
 credits: A number of credits to add to the player's account
 
 note: An optional note (for author purposes) for the credit change
 




**Args:** 

**Args:**

 player: a mob, client, key, or ckey
 
 credits: A number of credits to add to the player's account
 
 note: An optional note (for author purposes) for the credit change
 



 credits: A number of credits to add to the player's account
 
 note: An optional note (for author purposes) for the credit change
 


 note: An optional note (for author purposes) for the credit change


 Adds credits to a player's account. The proc will return 1 if it is
successful, or 0 if the attempt failed and should not be tried again. This
feature is intended for games that make use of the credit system, and for
security all such games must use a hub password.




 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is a good idea to use spawn() to avoid holding up the rest of
the game.



### 
 Example:



 mob/proc/QuestCompleted(name, credits)
 src << "Congratulations! You completed the [name] quest and earned [credits] credit\s!"
 world.AddCredits(name, credits, "Quest: [name]")


 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.





---



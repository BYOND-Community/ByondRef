

 Logout proc (mob)
-------------------




**See also:** 


[Login proc (mob)](#/mob/proc/Login) 

[client var (mob)](#/mob/var/client) 

[key var (mob)](#/mob/var/key) 





**See also:** 

**See also:**

[Login proc (mob)](#/mob/proc/Login) 

[client var (mob)](#/mob/var/client) 

[key var (mob)](#/mob/var/key) 



[Login proc (mob)](#/mob/proc/Login)

[client var (mob)](#/mob/var/client) 

[key var (mob)](#/mob/var/key) 


[client var (mob)](#/mob/var/client)

[key var (mob)](#/mob/var/key) 

[key var (mob)](#/mob/var/key)


**Format:** 


 Logout()
 


**Format:** 

**Format:**

 Logout()



**When:** 


 Called when a player's client has disconnected from a mob. This happens
 in client.Del() when the player logs out of the world. It may also
 happen when the player switches from one mob to another.
 


**When:** 

**When:**

 Called when a player's client has disconnected from a mob. This happens
 in client.Del() when the player logs out of the world. It may also
 happen when the player switches from one mob to another.



**Default action:** 


 None.
 


**Default action:** 

**Default action:**

 None.


 One may wish to distinguish between a player who has disconnected from
the game and one who is simply switching from one mob to another. In the
case of a player switching to another mob, by the time
 `Logout()` 
 is called, the original mob's key will be null, whereas the key will still
be non-null in the case of a player disconnecting from the game.



`Logout()`


---



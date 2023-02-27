

 client
--------




**See also:** 


[client var (mob)](#/mob/var/client) 

[key var (mob)](#/mob/var/key) 

[procs (client)](#/client/proc) 

[vars (client)](#/client/var) 






**See also:** 

**See also:**

[client var (mob)](#/mob/var/client) 

[key var (mob)](#/mob/var/key) 

[procs (client)](#/client/proc) 

[vars (client)](#/client/var) 




[client var (mob)](#/mob/var/client)

[key var (mob)](#/mob/var/key) 

[procs (client)](#/client/proc) 

[vars (client)](#/client/var) 



[key var (mob)](#/mob/var/key)

[procs (client)](#/client/proc) 

[vars (client)](#/client/var) 


[procs (client)](#/client/proc)

[vars (client)](#/client/var) 

[vars (client)](#/client/var)

 Each connected player has a corresponding client object. It has
variables and procedures which control aspects of player input/output. This
object is also responsible for linking the player up to a mob.




 The client can be reassigned from its original mob M to a new mob N by
setting N.client = M.client. This process disconnects the player from M
(calling M.Logout()) and connects the player to N (calling N.Login()).
Setting the mob's key has the same effect.




 Additional vars, procs, and verbs may be added to the client in order to
give the player properties that are independent of the mob.





---



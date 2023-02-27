

 view proc
-----------




**See also:** 


[<< output operator](#/operator/%3c%3c/output) 

[hearers](#/proc/hearers) 

[oview proc](#/proc/oview) 

[range proc](#/proc/range) 

[see\_in\_dark var (mob)](#/mob/var/see_in_dark) 

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 













**See also:** 

**See also:**

[<< output operator](#/operator/%3c%3c/output) 

[hearers](#/proc/hearers) 

[oview proc](#/proc/oview) 

[range proc](#/proc/range) 

[see\_in\_dark var (mob)](#/mob/var/see_in_dark) 

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 











[<< output operator](#/operator/%3c%3c/output)

[hearers](#/proc/hearers) 

[oview proc](#/proc/oview) 

[range proc](#/proc/range) 

[see\_in\_dark var (mob)](#/mob/var/see_in_dark) 

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 










[hearers](#/proc/hearers)

[oview proc](#/proc/oview) 

[range proc](#/proc/range) 

[see\_in\_dark var (mob)](#/mob/var/see_in_dark) 

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 









[oview proc](#/proc/oview)

[range proc](#/proc/range) 

[see\_in\_dark var (mob)](#/mob/var/see_in_dark) 

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 








[range proc](#/proc/range)

[see\_in\_dark var (mob)](#/mob/var/see_in_dark) 

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 







[see\_in\_dark var (mob)](#/mob/var/see_in_dark)

[see\_infrared var (mob)](#/mob/var/see_infrared) 

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 






[see\_infrared var (mob)](#/mob/var/see_infrared)

[see\_invisible var (mob)](#/mob/var/see_invisible) 

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 





[see\_invisible var (mob)](#/mob/var/see_invisible)

[sight var (mob)](#/mob/var/sight) 

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 




[sight var (mob)](#/mob/var/sight)

[view var (client)](#/client/var/view) 

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 



[view var (client)](#/client/var/view)

[view var (world)](#/world/var/view) 

[viewers](#/proc/viewers) 


[view var (world)](#/world/var/view)

[viewers](#/proc/viewers) 

[viewers](#/proc/viewers)


**Format:** 


 view(Dist=5,Center=usr)
 


**Format:** 

**Format:**

 view(Dist=5,Center=usr)



**Returns:** 


 A list of visible objects within Dist tiles of Center.
 


**Returns:** 

**Returns:**

 A list of visible objects within Dist tiles of Center.



**Args:** 


 Dist: A number.
 
 Center: An object on the map.
 



**Args:** 

**Args:**

 Dist: A number.
 
 Center: An object on the map.
 


 Center: An object on the map.


 A Dist of 0 includes Center, the contents of Center (normally
usr.contents), its location (normally the turf a mob is standing on), and
any other contents of that location. A value of 1 extends the region to the
neighboring squares on the map and so on. Both arguments are optional and
may be passed in any order.




 The default range is actually controlled by the size of the map viewport
size, which is configured with
 `world.view` 
 . Since the default
value of that variable is 5, the default range is also 5. You may use any
valid view size, so an explicit view size such as "11x17" is also valid.



`world.view`
### 
 Example:



 view() << "to all in sight of [usr]"
view(src) << "to all in sight of [src]"
view(1,src.loc) << "to all within reach of [src]"


 Be aware of the following distinctions:




 view(usr) //objects that usr can see
view(usr.loc) //objects visible from usr's position
view(usr.client) //objects visible to player


 In many cases, the three different statements could produce the same
result, but they are not identical in general. For example, the first
statement takes into account the visual capabilities of usr, which might
include such things as the ability to see in the dark or to see invisible
objects.




 The second statement, since it is from a non-mob would just do a plain
visibility calculation with no special visual capabilities. In many cases,
you would want to use viewers() or hearers() instead.




 The third statement produces a list of visible objects as the player sees
things, which might be different than how the mob sees things if
 `client.eye` 
 and
 `client.mob` 
 are different.



`client.eye`
`client.mob`


---



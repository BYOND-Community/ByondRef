

 range proc
------------




**See also:** 


[<< output operator](#/operator/%3c%3c/output) 

[block](#/proc/block) 

[view proc](#/proc/view) 

[orange proc](#/proc/orange) 






**See also:** 

**See also:**

[<< output operator](#/operator/%3c%3c/output) 

[block](#/proc/block) 

[view proc](#/proc/view) 

[orange proc](#/proc/orange) 




[<< output operator](#/operator/%3c%3c/output)

[block](#/proc/block) 

[view proc](#/proc/view) 

[orange proc](#/proc/orange) 



[block](#/proc/block)

[view proc](#/proc/view) 

[orange proc](#/proc/orange) 


[view proc](#/proc/view)

[orange proc](#/proc/orange) 

[orange proc](#/proc/orange)


**Format:** 


 range(Dist,Center=usr)
 


**Format:** 

**Format:**

 range(Dist,Center=usr)



**Returns:** 


 A list of objects within Dist tiles of Center.
 


**Returns:** 

**Returns:**

 A list of objects within Dist tiles of Center.



**Args:** 


 Dist: A number.
 
 Center: An object on the map.
 



**Args:** 

**Args:**

 Dist: A number.
 
 Center: An object on the map.
 


 Center: An object on the map.


 This instruction is identical to view() except visibility is ignored.
All objects are included in the list whether they are visible or not.




 A Dist of 0 includes Center, the contents of Center (normally
usr.contents), its location (normally the turf a mob is standing on), and any
other contents of that location. A value of 1 extends the region to the
neighboring squares on the map and so on. You can also use a rectangular box
size using a text string such as "13x11". Both arguments are optional and may
be passed in any order.





---



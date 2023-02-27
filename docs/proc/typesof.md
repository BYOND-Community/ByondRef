

 typesof proc
--------------




**See also:** 


[istype proc](#/proc/istype) 

[locate proc](#/proc/locate) 




**See also:** 

**See also:**

[istype proc](#/proc/istype) 

[locate proc](#/proc/locate) 


[istype proc](#/proc/istype)

[locate proc](#/proc/locate) 

[locate proc](#/proc/locate)


**Format:** 


 typesof(Type1,Type2,...)
 


**Format:** 

**Format:**

 typesof(Type1,Type2,...)



**Returns:** 


 A list of all types that are derived from the specified "base" types,
including the base types themselves.
 


**Returns:** 

**Returns:**

 A list of all types that are derived from the specified "base" types,
including the base types themselves.



**Args:** 


 The "base" types.
 


**Args:** 

**Args:**

 The "base" types.

### 
 Example:



 obj/fruit
 apple
 peach
 mango
var/list/fruit\_types = typesof(/obj/fruit)


 In this example, fruit\_types is initialized to contain /obj/fruit,
/obj/fruit/apple, /obj/fruit/peach, and /obj/fruit/mango.




 This procedure can also be used to list procs and verbs.



### 
 Example:



 mob/admin\_commands/verb
 shutdown\_world()
 world.Del()
 reboot\_world()
 world.Reboot()

//for testing
mob/verb/add\_admin()
 verbs += typesof(/mob/admin\_commands/verb)
mob/verb/remove\_admin()
 verbs -= typesof(/mob/admin\_commands/verb)



---



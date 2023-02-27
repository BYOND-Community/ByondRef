

 instant setting (verb)
------------------------




**See also:** 


[settings (verb)](#/verb/set) 



**See also:** 

**See also:**

[settings (verb)](#/verb/set) 

[settings (verb)](#/verb/set)


**Format:** 


 set instant = Setting
 


**Format:** 

**Format:**

 set instant = Setting



**Args:** 


 Setting: 1 for "instant" verbs; 0 otherwise.
 


**Args:** 

**Args:**

 Setting: 1 for "instant" verbs; 0 otherwise.



**Default value:** 


 0
 


**Default value:** 

**Default value:**

 0


 Normally a player can only call one verb per tick, but they can call any
number of "instant" verbs in the same tick. This setting is useful for commands
called by the game's interface, or for more responsive controls like for
instance the use of "combos" in fighting games.




 Verbs with the instant setting can be used on the same tick as a regular
verb, but only one regular verb can be used each tick. Commands are still
processed in the order they are received, so verbs that use this setting
may have to wait if several regular verbs are queued up ahead of them.




 Any verbs that are already built-in, such as movement commands and mouse
commands, cannot be modified to use this setting. You can, however, create
replacement verbs of your own for most of them.



### 
 Example:



 mob/verb/FastNorth()
 set instant = 1
 usr.Move(get\_step(usr,NORTH), NORTH)


 To avoid abuse by players, you should use this setting for commands that
are unlikely to cause "spam" or give players any kind of unfair advantage.





---



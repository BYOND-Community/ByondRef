

 Export proc (client)
----------------------




**See also:** 


[Import proc (client)](#/client/proc/Import) 

[New proc (client)](#/client/proc/New) 

[hub var (world)](#/world/var/hub) 

[savefile](#/savefile) 






**See also:** 

**See also:**

[Import proc (client)](#/client/proc/Import) 

[New proc (client)](#/client/proc/New) 

[hub var (world)](#/world/var/hub) 

[savefile](#/savefile) 




[Import proc (client)](#/client/proc/Import)

[New proc (client)](#/client/proc/New) 

[hub var (world)](#/world/var/hub) 

[savefile](#/savefile) 



[New proc (client)](#/client/proc/New)

[hub var (world)](#/world/var/hub) 

[savefile](#/savefile) 


[hub var (world)](#/world/var/hub)

[savefile](#/savefile) 

[savefile](#/savefile)


**Format:** 


 client.Export(file)
 


**Format:** 

**Format:**

 client.Export(file)



**Args:** 


 file: file to send to client
 


**Args:** 

**Args:**

 file: file to send to client


 This stores the file on the user's computer in a special location unique to 
each registered
 [world.hub](#/world/var/hub) 
 setting. This is most 
useful for writing a client-side savefile, but any type of file may be stored. 
The purpose of this is to exchange information between different worlds running 
under the same hub path.



[world.hub](#/world/var/hub)

 When a file is exported to the player's computer, it replaces any
previous file stored by a game with the same
 `world.hub` 
 value.
This should not be used for anything requiring high security, because any
other world could make use of the same hub path and access the file. It
is also possible for the user to tinker with the file, since it resides on
their computer.



`world.hub`

 To delete the client-side file completely, call
 `client.Export()` 
 with no argument at all.



`client.Export()`
### 
 Example:



 mob/verb/save()
 var/savefile/F = new()
 F << usr //write the player's mob
 usr.client.Export(F)

client/New()
 var/client\_file = Import()
 if(client\_file)
 var/savefile/F = new(client\_file) //open it as a savefile
 F >> usr //read the player's mob
 return ..()



---



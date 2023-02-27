

 IsBanned proc (world)
-----------------------




**See also:** 


[GetConfig proc (world)](#/world/proc/GetConfig) 

[params2list proc](#/proc/params2list) 

[address var (client)](#/client/var/address) 

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 








**See also:** 

**See also:**

[GetConfig proc (world)](#/world/proc/GetConfig) 

[params2list proc](#/proc/params2list) 

[address var (client)](#/client/var/address) 

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 






[GetConfig proc (world)](#/world/proc/GetConfig)

[params2list proc](#/proc/params2list) 

[address var (client)](#/client/var/address) 

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 





[params2list proc](#/proc/params2list)

[address var (client)](#/client/var/address) 

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 




[address var (client)](#/client/var/address)

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 



[computer\_id var (client)](#/client/var/computer_id)

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 


[connection var (client)](#/client/var/connection)

[hub var (world)](#/world/var/hub) 

[hub var (world)](#/world/var/hub)


**Format:** 


 IsBanned(key,address,computer\_id,type)
 


**Format:** 

**Format:**

 IsBanned(key,address,computer\_id,type)



**Returns:** 


 True value if user is banned from this world. This may be a list, in which case special meaning is attributed to certain list elements as described below.
 


**Returns:** 

**Returns:**

 True value if user is banned from this world. This may be a list, in which case special meaning is attributed to certain list elements as described below.



**Args:** 


 key: BYOND key of the user.
 
 address: current IP address of the user.
 
 computer\_id: current computer\_id of the user if known.
 
 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )
 





**Args:** 

**Args:**

 key: BYOND key of the user.
 
 address: current IP address of the user.
 
 computer\_id: current computer\_id of the user if known.
 
 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )
 




 address: current IP address of the user.
 
 computer\_id: current computer\_id of the user if known.
 
 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )
 



 computer\_id: current computer\_id of the user if known.
 
 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )
 


 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )

[client.connection](#/client/var/connection)

 By default, this procedure checks the "ban" configuration file. If an
entry is found for the current world (based on the value of world.hub), the
parameter text is converted into a list (using params2list()), and the result
is returned. Otherwise, null is returned.




 A ban that applies to all worlds on the host's computer will not call
IsBanned(). The connection will simply be denied.




 This procedure is called internally whenever a new user connects (before
client/New() is called). If the result is true, access is denied. If you
want to ban a user but still allow them to log in (perhaps with reduced
functionality), you can put "Login=1" in the parameter text. If you want to
display an explanation to the user about why they are banned, you can also put
"message=X" in the parameter text, where X is the message to display to the user.
A reason for the ban can be added with a "reason=X" field. Of course, you can
also override IsBanned() and insert these values directly into the list that is
returned.




 Example
---------



 world/IsBanned(key,address)
 . = ..() //check the ban lists
 if(istype(., /list))
 .["Login"] = 1 //allow banned user to login


 When you ban people from paging you, this also causes them to be added to
the keyban list. Even if they are already connected, IsBanned() will be
re-evaluated and acted upon at that time. When you remove pager ban, they are
removed from keyban as well.




 Additional data elements may be added to the ban list in the future.
The current definition includes just the following items:





 Login
 

 true if banned user should be allowed to log in
 

 reason
 

 text string describing the reason or origin of the ban. For example, when
people are banned from the pager, they are added to the "keyban" list with
reason = "pager ban". This text is internal information only and is not
displayed to the banned user.
 

 message
 

 text string explaining to the user why they were banned and possibly what
they should do to be forgiven.
 


 Login


 true if banned user should be allowed to log in


 reason


 text string describing the reason or origin of the ban. For example, when
people are banned from the pager, they are added to the "keyban" list with
reason = "pager ban". This text is internal information only and is not
displayed to the banned user.


 message


 text string explaining to the user why they were banned and possibly what
they should do to be forgiven.


 Since the data in the "ban" file is in
 [application/x-www-form-urlencoded](#/proc/list2params) 
 format, it is
probably not desirable to edit the file by hand. No built-in facilities for
editing the file have been provided (aside from automatic addition of pager
bans), but an interface could be created, using
 [GetConfig](#/world/proc/GetConfig) 
 and
 [SetConfig](#/world/proc/SetConfig) 
 to read and write the data.
Extra features could also be added such as automatic inference of key
associations by IP address.



[application/x-www-form-urlencoded](#/proc/list2params)
[GetConfig](#/world/proc/GetConfig)
[SetConfig](#/world/proc/SetConfig)


---



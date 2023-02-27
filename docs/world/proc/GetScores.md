

 GetScores proc (world)
------------------------




**See also:** 


[SetScores proc (world)](#/world/proc/SetScores) 

[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 






**See also:** 

**See also:**

[SetScores proc (world)](#/world/proc/SetScores) 

[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 




[SetScores proc (world)](#/world/proc/SetScores)

[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 



[GetMedal proc (world)](#/world/proc/GetMedal)

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 


[SetMedal proc (world)](#/world/proc/SetMedal)

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal)


**Formats:** 


 GetScores(key, fields)
 
 GetScores(count, field)
 
 GetScores(count, skip, field)
 




**Formats:** 

**Formats:**

 GetScores(key, fields)
 
 GetScores(count, field)
 
 GetScores(count, skip, field)
 



 GetScores(count, field)
 
 GetScores(count, skip, field)
 


 GetScores(count, skip, field)



**Returns:** 


 A parameter list of scores for a given entry. Use params2list() to
interpret the results.
 


**Returns:** 

**Returns:**

 A parameter list of scores for a given entry. Use params2list() to
interpret the results.



**Args:** 


 key: the name of the player, character, etc. for which scores have been set
 
 fields: The data fields to retrieve
 
 count: The number of top score records to look at
 
 skip: The number of top score records to skip over
 





**Args:** 

**Args:**

 key: the name of the player, character, etc. for which scores have been set
 
 fields: The data fields to retrieve
 
 count: The number of top score records to look at
 
 skip: The number of top score records to skip over
 




 fields: The data fields to retrieve
 
 count: The number of top score records to look at
 
 skip: The number of top score records to skip over
 



 count: The number of top score records to look at
 
 skip: The number of top score records to skip over
 


 skip: The number of top score records to skip over


 Retrieves information about scores that is kept on the BYOND hub.




 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is a good idea to use spawn() to avoid holding up the rest of
the game.



### 
 GetScores(key, fields)



 In this form, you can get information about individual scores. This is
the most common way to use GetScores().




 The key is an arbitrary text value. Usually a player's key is a good
choice, but you can also use the name of their character, or anything else
you like, as long as it is unique. The key is case-insensitive.




 Scores and stats use data fields, which might be things like "Score",
"Level", "Class", etc. To retrieve all the fields associated with a key,
leave the fields argument blank. To retrieve only certain fields, you can
send a separated list like "Score;Level" which is in the same format returned
by list2params().




 If you leave the key argument blank, you will get a complete list of keys
that have scores and stats associated with them.



### 
 Example 1:



 mob/var/scores\_found
mob/var/score = 0

mob/Login()
 ..()
 spawn()
 var/scores = world.GetScores(key)
 scores\_found = !isnull(scores)
 if(scores)
 var/list/params = params2list(scores)
 if(params["Score"])
 score = text2num(params["Score"])
 src << "You have [score] point\s!"

### 
 GetScores(count, field)
 
*and* 
 GetScores(count, skip, field)


  

*and*

 In this form, the proc gets a list of the top scores for a certain field,
and gives you the keys and scores in order. To get the top 10 players by
level, for instance, you would use GetScores(10,"level"). This returns a
parameter list with the top keys and scores, so it might be in a form like
"Bob=100;Anita=80;David=20;Charlie=5".




 The count and skip arguments are always numbers, not text. The count is
the number of scores to retrieve, and skip is the number to skip over to get
to them. So count=10 and skip=0 is the top 10, while count=10 and skip=5 is
#6 through #15. If you leave out skip, it's a 0.




 The way you set up your hub entry is how the top scores are determined.
If you told the hub that the "score" field is always sorted from highest
number to lowest, then that's what you'll get. If "birthplace" is set up to
use an alphabetical order, that's the order that GetScores() will use. If a
field cannot be sorted, this form of GetScores() will return an empty text
string.




 If you don't specify a field, your hub entry may have a default field to
use. For instance if your hub page displays "Score", then "Level", then the
"Score" field is the default.



### 
 Example 2:



 mob/var/scores\_found

mob/Login()
 ..()
 spawn()
 var/top\_scores = world.GetScores(10, "Booty")
 scores\_found = !isnull(scores)
 if(scores)
 var/list/params = params2list(scores)
 src << "
 **Top Buccaneers:** 
 "
 for(var/i=1, i
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---


Import proc (world)
---------------------




**See also:** 


[Export proc (world)](#/world/proc/Export) 

[Import proc (client)](#/client/proc/Import) 

[Topic proc (world)](#/world/proc/Topic) 

[fcopy proc](#/proc/fcopy) 







**Format:** 


 Import()
 



**Returns:** 


 The file sent by the remote server. The file will be downloaded to the
 local server's resource cache. Note that this will cause the caller to
 sleep while waiting for the necessary data to be transfered.
 



**When:** 


 Call this inside world.Topic() if you are expecting a file from the
 remote server.
 

### 
 Example:



 //sending the file
mob/proc/Export(Addr)
 var/savefile/F = new()
 F.Write(src)
 world.Export(Addr,F)

//receiving the file
world/Topic()
 var/savefile/F = new(world.Import())
 F.Read() //read the mob
 

 This example defines a mob proc called Export() which writes the mob to a
savefile and sends it to another server (specified by Addr). The remote
server opens it as a savefile and creates the mob (if the same mob type is
defined on both servers and mob.Read() is compatible with the sending
server's mob.Write()).
 



 Note that another method of transferring player mobs is to use the key
savefile (accessed by client.Export() and client.Import()). Direct server
to server communication on the other hand could transfer data (like
non-players) without the need for player involvement at all.
 



 Savefiles are the most common type of file to transfer, but world.Import()
simply returns a reference to an item in the world's .rsc file, which could be
any type of file. This particular example demonstrates how to open such a
file as a temporary savefile. (It gets dumped from the cache into a separate
temporary file, which is then opened as a savefile.) Other types of files
would be handled differently. For example, you could use fcopy() to dump the
cached item to its own separate file.
 




---
IsBanned proc (world)
-----------------------




**See also:** 


[GetConfig proc (world)](#/world/proc/GetConfig) 

[params2list proc](#/proc/params2list) 

[address var (client)](#/client/var/address) 

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 









**Format:** 


 IsBanned(key,address,computer\_id,type)
 



**Returns:** 


 True value if user is banned from this world. This may be a list, in which case special meaning is attributed to certain list elements as described below.
 



**Args:** 


 key: BYOND key of the user.
 
 address: current IP address of the user.
 
 computer\_id: current computer\_id of the user if known.
 
 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )
 





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
 




---
IsSubscribed proc (world)
---------------------------




**Format:** 


 IsSubscribed(player)
 
 IsSubscribed(player, "BYOND") (to check BYOND Membership)
 




**Returns:** 


 Number of days left in subscription, -1 for a lifetime subscriber,
 *or* 
 null if hub contact failed
 



**Args:** 


 player: a mob, client, key, or ckey
 


 Checks a player for their subscription status to this game. This is a
simpler alternative to
 
 client.CheckPassport()
 
 , which is deprecated,
and also allows you to check even when the player has gone offline.
 



 This proc will return null if contacting the hub was required, but there
was no way to reach the hub. Contacting the hub may take a few moments, so it
is a good idea to use
 [spawn()](#/proc/spawn) 
 to avoid
holding up the rest of the game.
 


### 
 Example:



 mob/verb/JoinClub()
 if(!world.IsSubscribed(src))
 src << "Sorry, the club is only for subscribers."
 else
 // go to the turf with the tag "clubhouse"
 loc = locate("clubhouse")
 src << "Welcome to the clubhouse!"
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---
New proc (world)
------------------




**Format:** 


 New()
 



**When:** 


 Called after the world is initially loaded. The only procs preceding
 this one would be in the initialization of global variables and objects
 on the map.
 



**Default action:** 


 None.
 



---
OpenPort proc (world)
-----------------------




**See also:** 


[port var (world)](#/world/var/port) 

[visibility var (world)](#/world/var/visibility) 





**See also:** 


 OpenPort(port=0)
 



**Args:** 


 port: the network port to open
 



**Returns:** 


 1 on success; 0 on failure
 


 This causes the world to be hosted on the specified network port. A value
of 0 or "any" requests that any available port be used. The value "none"
causes the port to be closed so that no new connections are possible.
 



 This proc may be overridden. If it is, calling ..() is necessary to open
the port. If ..() is not called, it will not open.
 


### 
 Example:



 world/OpenPort(port)
 // only allow subscribers to host
 if(host\_is\_subscribed)
 return ..()
 

 The "ports" configuration option in cfg/byond.txt can be used to control
what ports worlds may open. The -ports command-line option may also be used.
See
 [startup](#/proc/startup) 
 for the syntax.
 




---
PayCredits proc (world)
-------------------------




**See also:** 


[AddCredits proc (world)](#/world/proc/AddCredits) 

[GetCredits proc (world)](#/world/proc/GetCredits) 





**Format:** 


 PayCredits(player, credits, note)
 



**Returns:** 


 1 if the credits were spent successfully, 0 or null otherwise.
 



**Args:** 


 player: a mob, client, key, or ckey
 
 credits: A number of credits to deduct from the player's account
 
 note: An optional note (for author purposes) for the credit change
 




 Removes credits from a player's account, if they have enough. The proc
will return 1 if it is successful, or 0 if the attempt failed (usually
because the player doesn't have enough credits). This feature is intended
for games that make use of the credit system, and for security all such
games must use a hub password.
 



 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is often a good idea to use spawn() to avoid holding up the
rest of the game.
 


### 
 Example:



 mob/proc/ItemShop()
 var/items = list("Get credits!", "Magic sword"=10, "Skeleton key"=50)
 var/choices[0]
 var/item,price
 for(item in items)
 price = items[item]
 choices["[item]: [price] credit\s"] = item

 var/credits = world.GetCredits(key)
 if(isnull(credits))
 src << "Sorry, the item shop isn't available right now."
 return

 var/choice = input(src,\
 "You have [credits] credit\s. What would you like to purchase?",\
 "Item Shop")\
 as null|anything in choices
 if(!choice) return // cancel

 if(choice == "Get credits")
 src << link("http://www.byond.com/games/Author/MyGame/credits")
 return

 item = choices[choice]
 price = items[item]
 if(!price) return

 src << "Contacting item shop..."
 var/result = world.PayCredits(name, price, "Item shop: [item]")

 if(isnull(result))
 src << "Sorry, the item shop isn't available right now."
 else if(!result)
 src << "You need [price-credits] more credit\s to buy [item]."
 else
 src << "You bought \a [item]!"

 // Now give the user the item and save their character
 // These procs are for you to define
 src.AddEquipment(item)
 src.SaveCharacter()
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---
Profile proc (world)
----------------------




**Format:** 


 Profile(command, format)
 
 Profile(command, type, format)
 




**Returns:** 


 Profilng data or null
 



**Args:** 


 command: A numerical value that says whether to start, stop, refresh, etc.
 
 type: A type of profile to use, other than proc profiling.
 
 format: Optional format for output data
 




 Interacts with the built-in server profiler without requiring the host to do
so via Dream Daemon, or an authorized player via Dream Seeker.
 



 The
 
 command
 
 value is built from bitflags, so it can combine any of
these three values via the
 
 |
 
 operator:
 




 PROFILE\_STOP
 

 Stop profiling. Not using this flag will start/continue profiling.
 

 PROFILE\_CLEAR
 

 Clear all profile data. This will also cause the proc to return null.
 

 PROFILE\_AVERAGE
 

 Any output data should use average times instead of total times.
 


 These additional values are also defined for convenience:
 




 PROFILE\_START
 

 Start/continue profiling but don't clear any existing data.
 

 PROFILE\_REFRESH
 

 Currently this is the same as
 
 PROFILE\_START
 
 .
 

 PROFILE\_RESTART
 

 Start profiling and clear existing data.
 

### 
 Profiling procs



 By default, data will be returned as a list. The first six values are the
column names:
 
 "name"
 
 ,
 
 "self"
 
 ,
 
 "total"
 
 ,
 
 "real"
 
 ,
 
 "over"
 
 , and
 
 "calls"
 
 , corresponding to the
columns in the profiler. These are followed by the profile data for each proc,
with the data being in the same column order. E.g. the next six items
represent the first proc in the profile.
 



 The optional
 
 format
 
 argument however can be used to return the
data in other formats. Currently the only accepted value is
 
 "json"
 
 ,
which will output the same data in JSON format.
 


### 
 SendMaps profile



 Using
 
 "sendmaps"
 
 in the
 
 type
 
 argument will profile the
routines used to send map informaiton to players. Unlike the proc profiling
this only has three data columns:
 
 "name"
 
 ,
 
 "value"
 
 , and
 
 "calls"
 
 . The value column might be a time or number value, depending
on what's being measured.
 



 The JSON format will include a
 
 unit
 
 property data that is not a
raw number, such as a time value.
 




---
Reboot proc (world)
---------------------




**Format:** 


 Reboot(reason)
 



**Args:** 


 reason: the reason
 
 Reboot()
 
 was called:
 * 0 or null: Called by game code
* 1: By host (Ctrl+R in Dream Seeker)
* 2: By
 [world.Topic()](#/world/proc/Topic)
* 3: By SIGUSR1 in UNIX






**Default action:** 





 Reload the world from scratch. Any connected players will automatically
relogin. This would be useful if you needed to recompile the world after
changing some code.
 



 In a UNIX environment, you can cause a running server to reboot by
sending it the signal SIGUSR1.
 



 If you override this proc, you must call ..() if you want the reboot to
complete normally.
 



 For reboots initiated by Dream Seeker, usr will be the mob belonging to
the player who sent the command.
 




---
Repop proc (world)
--------------------




**Format:** 


 Repop()
 



**Default action:** 


 Reload the obj and mob instances defined in the world map. This
 "repopulates" a world to its initial state. Only objects that were
 destroyed will be recreated.
 



---
SetConfig proc (world)
------------------------




**See also:** 


[GetConfig proc (world)](#/world/proc/GetConfig) 




**Format:** 


 SetConfig(config\_set,param,value)
 



**Args:** 


 config\_set: name of the configuration set (see below)
 
 param: name of the configuration parameter
 
 value: data to store (or null to delete this entry)
 




 This command is for storing configuration information that is shared by
applications installed on the same system. The configuration data is
accessed by specifying the configuration "set" and the parameter within that
set.
 



 For more information, see
 [GetConfig](#/world/proc/GetConfig) 
 .
 




---
SetMedal proc (world)
-----------------------




**See also:** 


[GetMedal proc (world)](#/world/proc/GetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 







**Format:** 


 SetMedal(medal, player)
 



**Returns:** 


 1 if the medal was awarded successfully, 0 or null otherwise.
 



**Args:** 


 medal: name of the medal being awarded
 
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
SetScores proc (world)
------------------------




**See also:** 


[GetScores proc (world)](#/world/proc/GetScores) 

[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 







**Format:** 


 SetScores(key, fields)
 



**Returns:** 


 The key, if the scores were successfully updated; null otherwise.
 



**Args:** 


 key: the name of the player, character, etc. for which scores should be set
 
 fields: The data fields to set
 



 Updates scores that are kept on the BYOND hub.
 



 The key is an arbitrary text value. Usually a player's key is a good
choice, but you can also use the name of their character, or anything else
you like, as long as it is unique. The key is case-insensitive.
 



 Scores and stats use data fields, which might be things like "Score",
"Level", "Class", etc. Use list2params() to set the fields that you want to
change. Fields that you do not include in the list will not be changed. A
field with a blank value will be deleted.
 



 Sending an empty text string for the fields will erase the scores for that
key.
 



 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is a good idea to use spawn() to avoid holding up the rest of
the game.
 


### 
 Example:



 var/params

// Change the Score and Pet fields
params = list("Score"=123, "Pet"="Dog")
world.SetScores("Tom", list2params(params))

// Delete the Pet field
params = list("Pet"="")
world.SetScores("Tom", list2params(params))

// Delete Tom's scores entirely
world.SetScores("Tom", "")
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---
Tick proc (world)
-------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_usage var (world)](#/world/var/tick_usage) 






**Format:** 


 Tick()
 



**When:** 


 Called during the server tick, after sleeping procs and queued commands,
just before map information is sent to the clients.
 



**Default action:** 


 None.
 


 This proc allows you to do any updates just before map info is sent out.
One possible use for this is to run a movement loop, or sync up any user
interface input that might have arrived and deal with it all at once.
 


### 
 Example:



 world/Tick()
 for(var/client/C)
 if(C.mob?.move\_dir)
 try
 step(C.mob, move\_dir)
 catch
 // empty catch, just so a failed step won't break the loop
 

 Note: The tick will not wait if this proc sleeps. It effectively has
 [set waitfor=0](#/proc/set/waitfor) 
 already built in.
It's a good idea not to sleep in this proc or any of its callees at all,
since it will keep getting called every tick.
 




---
Topic proc (world)
--------------------




**See also:** 


[Del proc (world)](#/world/proc/Del) 

[Export proc (world)](#/world/proc/Export) 

[Import proc (client)](#/client/proc/Import) 

[Import proc (world)](#/world/proc/Import) 

[Reboot proc (world)](#/world/proc/Reboot) 








**Format:** 


 Topic(T,Addr,Master,Keys)
 



**When:** 


 Called when a message is received from another server by using
 world.Export(). If a file is expected, world.Import() may be called to
 get it. The return value of Topic() will be passed back to the remote
 server.
 



**Args:** 


 T: The topic text string specified by the remote server (everything following ? in the URL).
 
 Addr: The address of the remote server.
 
 Master: 1 if remote server is the server which started this one.
 
 Keys: List of keys belonging to users who are logged in on the remote server
 






**Default action:** 


 The topic "ping" returns a true value (number of players plus one),
 which may be useful for telling if a server is alive. The topics
 "Reboot" and "Del" will call world.Reboot() and world.Del()
 respectively if the message was sent by the master server.
 

### 
 Example:



 world/Topic(T)
 if(findtext(T,"shout:") == 1)
 world << copytext(T,7)
 

 This example allows other servers to send this server topic text of the
form "shout:msg" and will broadcast the message to all the players in this
world.
 



 The Keys argument is either null, or a list of user keys. Any keys in the
list are logged in to the remote server.
 



 Always validate the input in
 
 Topic()
 
 calls
to make sure it's correct and the query you're recieving is legitimate.
 




---
vars (world)
--------------



 Built-in world vars:
 




 world/var
 

[address](#/world/var/address) 

[area](#/world/var/area) 

[byond\_build](#/world/var/byond_build) 

[byond\_version](#/world/var/byond_version) 

[cache\_lifespan](#/world/var/cache_lifespan) 

[contents](#/world/var/contents) 

[cpu](#/world/var/cpu) 

[executor](#/world/var/executor) 

[fps](#/world/var/fps) 

[game\_state](#/world/var/game_state) 

[host](#/world/var/host) 

[hub](#/world/var/hub) 

[hub\_password](#/world/var/hub_password) 

[icon\_size](#/world/var/icon_size) 

[internet\_address](#/world/var/internet_address) 

[log](#/world/var/log) 

[loop\_checks](#/world/var/loop_checks) 

[map\_format](#/world/var/map_format) 

[map\_cpu](#/world/var/map_cpu) 

[maxx](#/world/var/maxx) 

[maxy](#/world/var/maxy) 

[maxz](#/world/var/maxz) 

[mob](#/world/var/mob) 

[movement\_mode](#/world/var/movement_mode) 

[name](#/world/var/name) 

[params](#/world/var/params) 

[port](#/world/var/port) 

[process](#/world/var/process) 

[realtime](#/world/var/realtime) 

[reachable](#/world/var/reachable) 

[sleep\_offline](#/world/var/sleep_offline) 

[status](#/world/var/status) 

[system\_type](#/world/var/system_type) 

[tick\_lag](#/world/var/tick_lag) 

[tick\_usage](#/world/var/tick_usage) 

[time](#/world/var/time) 

[timeofday](#/world/var/timeofday) 

[timezone](#/world/var/timezone) 

[turf](#/world/var/turf) 

[url](#/world/var/url) 

[vars](#/datum/var/vars) 

[version](#/world/var/version) 

[view](#/world/var/view) 

[visibility](#/world/var/visibility) 















































---
address var (world)
---------------------




**See also:** 


[port var (world)](#/world/var/port) 

[url var (world)](#/world/var/url) 

[internet\_address var (world)](#/world/var/internet_address) 





 This is the network address of the machine hosting the world. If it
cannot be determined, it will be null.
 



 The full network address of the world may be formed by concatenating the
world address and port: "byond://[address]:[port]".
 



 In CGI mode, this is the web address of the world.
 



 This is the local address only. If the world is hosted via a router, the
external IP address may be different. Use
 
 internet\_address
 
 to find
the external address, if available.
 




---
area var (world)
------------------




**Default value:** 


 /area.
 


 This is the default area type to be placed on the map wherever no area is
specified. A value of 0 turns off the default area.
 




---
byond\_build var (world)
--------------------------




**See also:** 


[DM\_VERSION macro](#/DM/preprocessor/DM_VERSION) 

[byond\_version var (world)](#/world/var/byond_version) 

[byond\_version var (client)](#/client/var/byond_version) 

[byond\_build var (savefile)](#/savefile/var/byond_build) 

[byond\_version var (savefile)](#/savefile/var/byond_version) 







 This is the build number (minor version) of BYOND being run by this server.
Typically this is not useful information, but it can come in handy when
diagnosing issues reported by players when hosting with a beta build.
 




---
byond\_version var (world)
----------------------------




**See also:** 


[DM\_VERSION macro](#/DM/preprocessor/DM_VERSION) 

[byond\_build var (world)](#/world/var/byond_build) 

[system\_type var (world)](#/world/var/system_type) 

[byond\_version var (client)](#/client/var/byond_version) 

[byond\_build var (savefile)](#/savefile/var/byond_build) 

[byond\_version var (savefile)](#/savefile/var/byond_version) 








 This is the version of BYOND at run-time. A game designed to work around
known bugs in older versions could use this to adapt its behavior accordingly.
 




---
cache\_lifespan var (world)
-----------------------------




**See also:** 


[cache](#/DM/cache) 




**Default value:** 


 30 (days)
 


 Number of days items that are not in use will be saved in the resource
cache (.rsc file). Files uploaded by players are stored in the world's .rsc
file for future use. If the file is not used for the specified amount of
time, it will be removed to save space.
 



 Setting this value to 0 causes items to be saved for the current session
only. This is used by the CGI library, because web browsers cannot make use
of server-side caches when uploading files anyway.
 



 This value must be a whole number.
 




---
contents list var (world)
---------------------------




**See also:** 


[list](#/list) 




**Default value:** 


 List of all areas, turfs, mobs, and objs initially in the world.
 


 This is a list of every object in the world. Objects in this list are in
no particular order.
 


### 
 Example:



 proc/ListAreas(mob/M)
 var/area/A
 M << "Areas:"
 for (A in world.contents)
 M << A
 

 This example displays a list of every area in existence. As a convenient
short-hand, one may simply write for(A) or for(A in world) instead of the
full for(A in world.contents).
 




---
cpu var (world)
-----------------




**See also:** 


[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_lag var (world)](#/world/var/tick_lag) 

[tick\_usage var (world)](#/world/var/tick_usage) 

[Tick proc (world)](#/world/proc/Tick) 






 This is the percentage of a server tick that the server spends processing
running procs and the work of sending map information to players. A value of 0
would indicate very little cpu usage. A value of 100 would indicate full cpu
usage, which could mean that the server cannot complete all the necessary
computations during a tick to finish in time for the next tick. In this case,
timed events (such as sleep) may take
longer than requested.
 



 When deciding on a value for tick\_lag, one could use this value to
determine if the CPU is fast enough to tick at a higher rate.
 



 The
 
 map\_cpu
 
 var is a subset of this, measuring only time used for
sending map information.
 




---
executor var (world)
----------------------




**See also:** 


[startup proc](#/proc/startup) 




**Format:** 


 executor = "/usr/local/byond/bin/DreamDaemon [params]"
 


 This option is for direct execution of
 `.dmb` 
 files in UNIX.
The most common use is for writing CGI programs that are executed by the web
server.
 



 The first parameter in the
 
 executor
 
 text string is the path to
DreamDaemon. The one listed above is the standard UNIX location.
 



 Optional parameters may follow. The most common are -CGI and -logself.
 


### 
 Example:



 world/executor = "/usr/local/byond/bin/DreamDaemon -CGI -logself"
 

 This example creates a CGI program to be executed by a web server. It
puts its error output in the file
 `projname
 
 .log` 
 .
 



 All of this is configured for you when you include
 `html/CGI.dm` 
 from the html library.
 




---
fps var (world)
-----------------




**See also:** 


[tick\_lag var (world)](#/world/var/tick_lag) 

[fps var (client)](#/client/var/fps) 

[Pixel movement](#/{notes}/pixel-movement) 






**Default value:** 


 10
 


 The value of
 
 world.fps
 
 defines the speed of the world in frames
(server ticks) per second. By default this is 10 fps, which is a good speed if
all objects move in full tiles. Higher values yield smoother results, but at a
cost to performance. Timing of many events may be limited by the system clock,
so
 
 fps
 
 values beyond 40 or 50 may cause unwanted effects like jitter
even for projects that are not very demanding in terms of performance.
 



 For projects making use of pixel movement, higher
 
 fps
 
 is usually
desired. 40 seems to be a good value for general use, but in worlds that have
a large number of players, you may wish to lower the value and give players a
higher
 
 step\_size
 
 per tick instead.
 



 This var exists for convenience; it is calculated by
 
 10 /
world.tick\_lag
 
 . The value of
 
 world.tick\_lag
 
 is actually more
accurate, but it is easier to think of world speed in terms of frames per
second. The actual tick rate has a resolution of 1 ms.
 



 When reading
 
 world.fps
 
 , the result is always given as a whole
number to gloss over rounding error.
 



 If you set
 
 client.tick\_lag
 
 or
 
 client.fps
 
 to a value other
than 0, you can make the client tick at a different (usually faster) rate.
 




---
game\_state var (world)
-------------------------




**See also:** 


[name var (world)](#/world/var/name) 

[status var (world)](#/world/var/status) 

[visibility var (world)](#/world/var/visibility) 






**Default value:** 


 0
 


 At runtime, this value may be changed to let the BYOND hub know about
certain changes in the game's status. An example for using this value is if
the number of players in the game gets too high and most new logins are
rejected, you can set game\_state to 1 to let the hub know this server is
full.
 



 The following values are accepted:
 




 0
 

 Normal status
 

 1
 

 Server is full
 


 Note that this value does not affect how your world actually reacts to new
players logging in. It is only used by the hub and website.
 




---
host var (world)
------------------




**See also:** 


[game\_state var (world)](#/world/var/game_state) 

[name var (world)](#/world/var/name) 

[status var (world)](#/world/var/status) 

[visibility var (world)](#/world/var/visibility) 







**Default value:** 


 null
 


 If the information is made available by the pager, this will provide the
key of the world's host. If the host is not known, this value will be either
null or an empty string.
 




---
hub var (world)
-----------------




**See also:** 


[hub\_password var (world)](#/world/var/hub_password) 

[name var (world)](#/world/var/name) 

[status var (world)](#/world/var/status) 

[game\_state var (world)](#/world/var/game_state) 

[version var (world)](#/world/var/version) 

[visibility var (world)](#/world/var/visibility) 









**Default value:** 


 null
 


 This is a registered
 [BYOND hub](http://www.byond.com/hub/) 
 path.
The default value of null is for unregistered games. Registered games (don't
worry, it's free!) have their own hub page showing a brief description of the
game, the author, an optional installation package, and links to online games.
The hub path is a string of the form "YourName.GameName" and can be found in your
 [hub console](https://secure.byond.com/members/?command=edit_hub) 
 .
 



 Even unregistered games show up in the hub when they are live (that is
online with people connected). It just doesn't show any of the extra info
like a description, and there is no way for people to find out about it when
nobody is logged in.
 



 If you do not want your game to show up in the hub (like while you are in
the initial stages of development), just compile with
 `visibility=0` 
 . Either that, or turn off your pager or your BYOND
locator when you are connected to it.
 



 You (or the players) might also wish to turn off the notice of a live
game in the hub when there is no longer any room for new players or if it is
too late in the game for new people to join. At such times, you can simply
set the visibility to 0.
 


### 
 Example:



 world
 hub = "Dan.PipeStock" //registered hub path

mob/verb/start\_game()
 world.visibility = 0
 //...
 

 If you configure your hub page to require a hub password, you must also
specify
 `world.hub_password` 
 .
 




---
hub\_password var (world)
---------------------------




**See also:** 


[hub var (world)](#/world/var/hub) 

[visibility var (world)](#/world/var/visibility) 





**Default value:** 


 null
 


 If
 `world.hub` 
 is set, any live session of the game will be
attached to the specified BYOND Hub page. Under the default settings,
any game can set
 `world.hub` 
 and attach itself to any BYOND
Hub page.
 



 To beef up security, you can set a hub password in your hub's
configuration page via the BYOND website. This will ensure that
only authorized copies of your game can attach themselves to your
hub page when live. Then simply copy that password into your code as
 `world.hub_password` 
 so that your game's live broadcast will
be accepted by the hub.
 


### 
 Example:



 world
 hub = "Dan.PipeStock" //registered hub path
 hub\_password = "UPAggnJaeXmSBoKK" //password for live game authentication
 

 Note that for security reasons, reading this variable at runtime will
return a hashed version of the value that was set.
 




---
icon\_size var (world)
------------------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[step\_size var (movable atoms)](#/atom/movable/var/step_size) 

[Gliding](#/{notes}/gliding) 

[Pixel movement](#/{notes}/pixel-movement) 







**Default value:** 


 32
 


 This is the tile size that will be used as a default for icons in the
world. It can be set to a single number that represents both the width and
height, or you can use a format like "[width]x[height]" (such as "16x48") to
specify width and height separately.
 



 This value affects several calculations, including icon operations and
gliding between turfs.
 



 Note: If you do not use a square icon size and you are using a topdown map
format, you may experience display issues if setting
 
 client.dir
 
 to
 
 EAST
 
 or
 
 WEST
 
 . A non-square tile with a topdown map format
will also interfere with pixel movement. For this reason, square sizes are
recommended when using any topdown-view map format.
 




---
internet\_address var (world)
-------------------------------




**See also:** 


[port var (world)](#/world/var/port) 

[url var (world)](#/world/var/url) 

[address var (world)](#/world/var/address) 





 This is the network address of the machine hosting the world, as it is
seen by the outside network (from the Internet) and the hub. If it cannot
be determined, it will be null.
 



 The full network address of the world may be formed by concatenating the
world address and port: "byond://[address]:[port]".
 



 This var exists because
 
 world.address
 
 may not be accurate if the
world is hosted on a machine behind a router using NAT. The value returned
by
 
 internet\_address
 
 can be given to other players who wish to log
in.
 




---
log var (world)
-----------------




**See also:** 


[file proc](#/proc/file) 

[startup proc](#/proc/startup) 




 Sending output to world.log may be useful for debugging purposes. The
output goes to the same place run-time proc errors are displayed.
 


### 
 Example:



 if(1+1 != 2)
 world.log << "Uh oh."
 

 You can assign world.log to a file name or file() object to redirect output
to that file. (There is also a command-line option to Dream Daemon that does
this.)
 


### 
 Example:



 world.log = file("mylog.txt")
 


---
loop\_checks var (world)
--------------------------




**Default value:** 


 1
 


 Setting this to 0 disables the very long loop protection. By default,
loops in the code which undergo a very large number of iterations or
recursions are aborted (by crashing the proc). This prevents the proc from
locking up the server for too long.
 



 You may need to disable this feature if your code has some very long loops
in it. Before doing that, make sure it's not
 *infinitely* 
 long! Your
program will utterly crash if it runs out of system stack space, which can
happen in a very deep or infinite recursion.
 



 Note: The compiler will now generate a warning when you disable
 
 loop\_checks
 
 . It is not advisable to disable the check unless you're
trying to debug something, since you can cause the server to hang. Generally
if you have a loop so long it can cause the regular loop checks to freak out,
you need to make a change to the loop behavior anyway.
 




---
map\_format var (world)
-------------------------




**See also:** 


[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Topdown maps](#/{notes}/topdown) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 

[Understanding the renderer](#/{notes}/renderer) 













**Default value:** 


 TOPDOWN\_MAP
 



**Possible values:** 


* TOPDOWN\_MAP
* ISOMETRIC\_MAP
* SIDE\_MAP
* TILED\_ICON\_MAP





 This value says how the world will display maps. In a normal overhead
tiled map the value is
 
 TOPDOWN\_MAP
 
 for the top-down format. For older
games that predate this feature, the value is
 
 TILED\_ICON\_MAP
 
 .
 



 If you use a map format other than top-down, the HUD will still use a
tile format like it would in top-down display. HUD objects are not projected
into whatever map\_format you use and they are not affected by changing
client.dir. The size of the HUD is rounded up to the nearest number of full
screen tiles; the size of each tile is defined by world.icon\_size.
 


### 
 Top-down format


 (See more at
[Topdown maps](#/{notes}/topdown) 
 .)
 
 This is the default map format. Icons are drawn in a tile form and viewed
from overhead. In this layout, the layer assigned to each atom is very
important. The number of tiles shown is set by client.view or world.view.
 



 Because this format is familiar and easy to understand, it is the default
setting. Most of the vars related to maps and atoms are designed and
documented with this format in mind.
 


### 
 Tiled icon format


 (See more at
 [Tiled icons](#/{notes}/tiled-icons) 
 .)

In BYOND 4.0 a new feature was introduced for using "big" icons, bigger than
the standard tile size, by splitting them up into states like "0,0", "1,0",
and so on. This functionality is no longer needed since BYOND now has the
ability to display icons in their natural size. Some games that were designed
before this, however, may still need to make use of this splitting feature
that breaks icons into smaller tile-sized pieces.

When an icon is broken into chunks, each state in the icon is given a
thumbail version of the full image, and then new states are added to show
each chunk. For instance if world.icon\_size is the default 32×32, and
the icon is 64×64, then the "door" state would become a thumbnail of
the full door image while "door 0,0" (the lower left corner), "door 1,0",
"door 0,1", and "door 1,1" were created to show each smaller section of the
image. If the default "" state is broken into chunks, those chunks are just
named "0,0" and so on without a space.

This format is deprecated. It exists to support older games and allow them to
be compiled without causing them to break, until they can be redesigned for
one of the newer formats.
 ### 
 Isometric format


 (See more at
 [Isometric maps](#/{notes}/isometric) 
 .)
 
 If map\_format is set to
 
 ISOMETRIC\_MAP
 
 , the map is displayed in
isometric form. Isometric tiles are displayed in a foreshortened diagonal
perspective, where the "north" direction actually displays as northeast on
the player's screen, and "east" shows up as southeast. The value of
 
 client.view
 
 or
 
 world.view
 
 is used to calculate the
 *minimum* 
 number of tiles to display, and extra tiles to each side will
be shown to fill in the corners.
 



 In an isometric map, the tile width set in world.icon\_size is the most
important factor. This should be a multiple of 4 for best results. The
minimum tile height is half that value, and any extra height is used to show
vertical structures that "stick up" off the map surface. When you draw an
isometric tile icon, start with a flattened diamond shape at the bottom that
is only half as high as it is wide.
 



 Isometric maps behave differently during drawing than top-down maps. In
isometric, tiles that are nearer to the viewer's perspective are drawn in
front of tiles farther back, regardless of layer. Layers only count within an
individual tile. This means that if you want to have a vertical structure
"stick up" to partially hide something behind it, the icon sticking up should
always be on a tile forward from the one being partly covered. E.g. if you
have a wall taking up part of your tile, it needs to be at the "back" end of
the tile to properly hide anything on the tiles behind it.
 



 The
 
 pixel\_x
 
 and
 
 pixel\_y
 
 values,
 
 step\_x
 
 and
 
 step\_y
 
 values, and the gliding that happens when moving between
tiles, are based on the width set by
 
 world.icon\_size
 
 . If you set
 
 world.icon\_size="64x128"
 
 to show tall buildings, only the 64 matters
for pixel offsets. Use
 
 pixel\_w
 
 and
 
 pixel\_z
 
 to adjust the
position of atoms (or the client) horizontally or vertically without respect
to
 
 client.dir
 
 or the map format.
 



 Note: Offsets for x and y also affect the layering order used to draw
the icons. Any object with a pixel offset onto another tile is considered
part of whichever tile is closer.
 



 If you use an icon wider than one tile, the "footprint" of the isometric
icon (the actual map tiles it takes up) will always be a square. That is, if
your normal tile size is 64 and you want to show a 128x128 icon, the icon is
two tiles wide and so it will take up a 2×2-tile area on the map. The
height of a big icon is irrelevant--any excess height beyond width/2 is used
to show vertical features. To draw this icon properly, other tiles on that
same ground will be moved behind it in the drawing order.
 



 One important warning about using big icons in isometric mode is that you
should only do this with dense atoms. If part of a big mob icon covers the
same tile as a tall building for instance, the tall building is moved back
and it could be partially covered by other turfs that are actually behind it.
A mob walking onto a very large non-dense turf icon would experience similar
irregularities.
 


### 
 Side-view format


 (See more at
 [Side-view maps](#/{notes}/side) 
 .)
 
 The
 
 SIDE\_MAP
 
 format is like a cross between
 
 TOPDOWN\_MAP
 
 and
 
 ISOMETRIC\_MAP
 
 . It looks very similar to a top-down view but it is
intended for more of a 3/4 perspective, where tiles lower on the screen are
considered closer to the viewer. Because this impacts the way layers work,
most of the layering behavior is the same as with isometric.
 



 In a 3/4 perspective the tiles are often foreshortened, so pixel offsets
are adjusted to account for this. For example, you may set
 
 world.icon\_size
 
 to
 
 "32x24"
 
 , but the tile is considered to be
a perfect square if you look at it from the top down. Because the width is 32
pixels, the virtual height is also 32, so if you use pixel\_y=32 the atom will
appear one tile further back than it normally is. (This adjustment doesn't
affect screen objects or
 
 pixel\_w
 
 /
 
 pixel\_z
 
 .)
 



 Changing
 
 client.dir
 
 preserves the same tile size regardless of
orientation.
 




---


map\_cpu var (world)
----------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[tick\_lag var (world)](#/world/var/tick_lag) 

[tick\_usage var (world)](#/world/var/tick_usage) 

[Tick proc (world)](#/world/proc/Tick) 






 This is the percentage of a server tick that the server spends processing
information about the map to send to players. A value of 0 would indicate very
little cpu usage. A value of 100 would indicate full cpu usage, which means
that the server cannot complete all the necessary computations during a tick to
finish in time for the next tick. In this case, timed events (such as sleep)
may take longer than requested.
 




---
maxx var (world)
------------------




**See also:** 


[area var (world)](#/world/var/area) 

[maxy var (world)](#/world/var/maxy) 

[maxz var (world)](#/world/var/maxz) 

[turf var (world)](#/world/var/turf) 

[Map](#/map) 








**Default value:** 


 0
 


 The world map is a three-dimensional block of turfs with coordinates
ranging from (1,1,1) to (maxx,maxy,maxz). If set at compile time, it
provides a lower bound and will be increased as needed by the map files.
 



 The default value is 0, indicating no map. If any of the map dimensions
are set to non-zero values at compile time, the others will default to 1.
 



 New territory created by increasing the map boundaries is filled in with
the default turf and area (world.turf, and world.area).
 




---
maxy var (world)
------------------




**See also:** 


[area var (world)](#/world/var/area) 

[maxx var (world)](#/world/var/maxx) 

[maxz var (world)](#/world/var/maxz) 

[turf var (world)](#/world/var/turf) 







**Default value:** 


 0
 


 The world map is a three-dimensional block of turfs with coordinates
ranging from (1,1,1) to (maxx,maxy,maxz). If set at compile time, it
provides a lower bound and will be increased as needed by the map files.
 



 The default value is 0, indicating no map. If any of the map dimensions
are set to non-zero values at compile time, the others will default to 1.
 



 New territory created by increasing the map boundaries is filled in with
the default turf and area (world.turf, and world.area).
 




---
maxz var (world)
------------------




**See also:** 


[area var (world)](#/world/var/area) 

[maxx var (world)](#/world/var/maxx) 

[maxy var (world)](#/world/var/maxy) 

[turf var (world)](#/world/var/turf) 







**Default value:** 


 0
 


 The world map is a three-dimensional block of turfs with coordinates
ranging from (1,1,1) to (maxx,maxy,maxz). If set at compile time, it
provides a lower bound and will be increased as needed by the map files.
 



 The default value is 0, indicating no map. If any of the map dimensions
are set to non-zero values at compile time, the others will default to 1.
 



 New territory created by increasing the map boundaries is filled in with
the default turf and area (world.turf, and world.area).
 




---
mob var (world)
-----------------




**See also:** 


[New proc (client)](#/client/proc/New) 




**Default value:** 


 /mob.
 


 When a player connects to the world, the world is searched for a mob with
the player's key. If one is found, the player is connected to that mob. If
none is found, a new mob of type world.mob is created and the player is
connected to this new mob.
 



 The default value is /mob. Setting world.mob to 0 prevents the creation
of default mobs.
 


### 
 Example:



 world
 mob = /mob/newbie

mob/newbie
 Login()
 src << "Welcome, [name]."
 ..()
 

 This example will connect new players to mobs of type /mob/newbie. They
are welcomed when they connect.
 




---
movement\_mode var (world)
----------------------------




**See also:** 


[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[Enter proc (atom)](#/atom/proc/Enter) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Pixel movement](#/{notes}/pixel-movement) 

[Gliding](#/{notes}/gliding) 










**Possible values:** 



 LEGACY\_MOVEMENT\_MODE
 
 : Old BYOND behavior regarding pixel movement and turf contents (see below)
 

 TILE\_MOVEMENT\_MODE
 
 : All atoms are locked to the tile grid
 

 PIXEL\_MOVEMENT\_MODE
 
 : All movable atoms can use pixel movement unless otherwise specified (see below), but legacy behavior for turf contents is ignored
 





**Default value:** 


 LEGACY\_MOVEMENT\_MODE
 


 Controls how movement works on the map.
 




 TILE\_MOVEMENT\_MODE
 
 allows you to easily discard any and all pixel
movement, so if step\_x or step\_y coordinates or unexpected atom bounds were
loaded from a savefile, for instance, they would be eliminated. If you use any
other movement mode, you can give an atom the
 [TILE\_MOVER](#/atom/var/appearance_flags) 
 flag and it will
behave as if it were in this mode, while other atoms are free to do their own
thing.
 




 LEGACY\_MOVEMENT\_MODE
 
 exists to distinguish between old and new
movement behavior. In older versions of BYOND before pixel movement, turfs
took their contents into consideration by default in Enter() and Exit(). This
doesn't really make sense for newer games, so in any other movement mode the
turf behavior will ignore its contents. mob.Cross() is also affected, since
it would return 0 by default in legacy mode when both mobs were dense; now
by default it checks
 
 mob.group
 
 .
 




---
name var (world)
------------------




**Default value:** 


 The <world> part of the <world>.dmb file.
 


 This is the name of the world.
 


### 
 Example:



 world
 name = "The Void"
 


---
params var (world)
--------------------




**See also:** 


[list associations](#/list/associations) 

[params2list proc](#/proc/params2list) 

[startup proc](#/proc/startup) 






**Default value:** 


 null
 


 This is a list of parameters passed to the world from the command-line
-params option when the server was started. The parameter text is passed
through params2list() to generate the world.params list.
 


### 
 Example:



 world/New()
 var/p
 if(params.len) world.log << "Command-line parameters:"
 for(p in params)
 world.log << "[p] = [params[p]]"
 

 This example displays the value of each parameter.
 




---
port var (world)
------------------




**See also:** 


[OpenPort proc (world)](#/world/proc/OpenPort) 

[address var (world)](#/world/var/address) 

[reachable var (world)](#/world/var/reachable) 

[visibility var (world)](#/world/var/visibility) 






 This is the network port of the world. If the world does not have an
open network port, this is 0.
 




---
process var (world)
---------------------




**See also:** 


[byond\_version var (world)](#/world/var/byond_version) 

[system\_type var (world)](#/world/var/system_type) 

[shell proc](#/proc/shell) 





 This read-only variable indicates the ID of the server's process on the
system running it. The result is a number, unless for some unexpected
reason the number won't fit in a
 
 num
 
 type, in which case it will
be text. (In practice it should always be a number.)
 




---
realtime var (world)
----------------------




**See also:** 


[time var (world)](#/world/var/time) 

[timeofday var (world)](#/world/var/timeofday) 

[time2text proc](#/proc/time2text) 





 This is the time (in 1/10 seconds) since 00:00:00 GMT, January 1, 2000
(also known as the BYOND era).
 



 Because this is a large number, BYOND's number system isn't capable of
enough precision to deliver the exact number of 1/10 second ticks. It usually
rounds off to the nearest several seconds. For more accurate readings use
 `world.timeofday` 
 .
 




---
reachable var (world)
-----------------------




**See also:** 


[port var (world)](#/world/var/port) 

[OpenPort proc (world)](#/world/proc/OpenPort) 




 Returns 1 if the world is currently hosted and the port can be reached by
players (as determined by the BYOND hub), 0 if not.
 



 If the port is not reachable, there may be a brief period during which the
hub is still attempting to make contact; during that time the port is assumed
to be reachable. Currently, the reachability test times out and fails after
30 seconds.
 




---
sleep\_offline var (world)
----------------------------




**Default value:** 


 0
 


 Setting this to 1 causes the world to be suspended when there are no
players, even if you have sleeping procs waiting to happen. The default
value is 0, which means the server will only sleep if there are no players
and no procs waiting to happen. The main purpose of the variable is to save
the cpu from doing work when there is nobody around to appreciate it. On the
other hand, that doesn't give the poor NPC's a break from the nasty humans.
 




---
status var (world)
--------------------




**See also:** 


[hub var (world)](#/world/var/hub) 

[game\_state var (world)](#/world/var/game_state) 

[visibility var (world)](#/world/var/visibility) 





 This is a short text string used in BYOND hub to describe the state of a
game in progress. For example, you might want to indicate if new players
will be able to actively play, or whether they would have to join as
spectators.
 


### 
 Example:



 world
 status = "accepting players"
mob/verb/start\_game()
 world.status = "accepting spectators"
 //...
 


---
system\_type var (world)
--------------------------




**See also:** 


[byond\_version var (world)](#/world/var/byond_version) 

[process var (world)](#/world/var/process) 

[shell proc](#/proc/shell) 





 This variable indicates the operating system type at run-time. It will be
one of the following constants:
 


* MS\_WINDOWS
* UNIX




---
tick\_lag var (world)
-----------------------




**See also:** 


[fps var (world)](#/world/var/fps) 

[tick\_lag var (client)](#/client/var/tick_lag) 

[tick\_usage var (world)](#/world/var/tick_usage) 

[sleep proc](#/proc/sleep) 







**Default value:** 


 1
 


 This is the smallest unit of time (one server tick) measured in 1/10
seconds. The duration of events that take some finite amount of time (like
sleep) will be rounded to a whole number of ticks.
 



 Players are limited to one command (including movements) per server tick,
so this value can be used to adjust the responsiveness of the game. If the
network is too slow to keep up with players, their commands will get queued
up, which can be annoying when trying to move. In this case, tick\_lag
should be increased so that the stored up movement commands are discarded.
On the other hand, if you have a very fast network, you may wish to decrease
tick\_lag to speed up the response time to player commands.
 



 Often it is more convenient to set world.fps instead of world.tick\_lag,
since fps (frames per second) is an easier way to think of server ticks.
world.tick\_lag is 10 / world.fps and vice-versa, so a tick\_lag of 0.25 is
equal to 40 fps.
 



 If you set client.tick\_lag or client.fps to a value other than 0, you can
make the client tick at a different (usually faster) rate.
 




---
tick\_usage var (world)
-------------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[tick\_lag var (world)](#/world/var/tick_lag) 

[Tick proc (world)](#/world/proc/Tick) 





 This is the approximate percentage of the server tick that has been used
already. A value under 100 means there's time to do more calculations, which
can include any pending procs that are still waiting to run on this tick.
When the value is over 100, the tick is running long and your world will
experience lag.
 



 Keep in mind that sending maps to clients is the last thing that happens
during a tick, except for handling any events such as player commands that
might arrive before the next tick begins. Therefore in a verb,
 
 tick\_usage
 
 might have a higher value than you would expect to see in
a proc that loops and sleeps.
 




---
time var (world)
------------------




**See also:** 


[realtime var (world)](#/world/var/realtime) 

[tick\_lag var (world)](#/world/var/tick_lag) 




 This gives the amount of time (in 1/10 seconds) that the world has been
running. In actual fact, it is the number of server ticks that have passed
multiplied by world.tick\_lag. Therefore if the server sleeps (when no
players are connected) this time is not counted. Also, if the server runs
overtime during a tick (because procs take longer than tick\_lag to finish)
this still only counts as one tick. This value is therefore a measure of
"game time" rather than real time.
 




---
timeofday var (world)
-----------------------




**See also:** 


[realtime var (world)](#/world/var/realtime) 

[time var (world)](#/world/var/time) 

[time2text proc](#/proc/time2text) 





 This is the time (in 1/10 seconds) since 00:00:00 GMT today. It is
basically identical to
 `world.realtime` 
 but doesn't include any
information about the date. This is a much smaller number; hence it is more
accurate.
 




---
timezone var (world)
----------------------




**See also:** 


[realtime var (world)](#/world/var/realtime) 

[timeofday var (world)](#/world/var/timeofday) 

[timezone var (client)](#/client/var/timezone) 

[time2text proc](#/proc/time2text) 






 This is the time offset from UTC, in hours, for the world's time zone. It
can be used in the
 
 time2text()
 
 proc, although it is the default time
zone for that proc.
 




---
turf var (world)
------------------




**Default value:** 


 /turf.
 


 This is the default turf type to be placed on the map wherever no turf is
specified. A value of 0 turns off the default turf.
 




---
url var (world)
-----------------




**See also:** 


[address var (world)](#/world/var/address) 



 This is the full network address of the world. (For example,
byond://dan.byond.com:6005.)
 




---
version var (world)
---------------------




**See also:** 


[hub var (world)](#/world/var/hub) 




**Default value:** 


 0
 


 If you are distributing your game to players, you can use this variable
to automatically notify them of new releases. To do so, you will first need
to set
 [`world.hub`](#/world/var/hub)
 to the hub
path of your game. You can then advertise the current version by
configuring that value in your
 [hub console](https://secure.byond.com/members/?command=edit_hub) 
 .
 



 When players boot up an outdated version of your game (as indicated by
comparing
 `world.version` 
 with the version advertised by BYOND
hub), they will be notified of the new release.
 




---
view var (world)
------------------




**See also:** 


[lazy\_eye var (client)](#/client/var/lazy_eye) 

[show\_map var (client)](#/client/var/show_map) 

[view proc](#/proc/view) 

[view var (client)](#/client/var/view) 







**Default value:** 


 5
 



**Possible values:** 


 -1 to 34 or "WIDTHxHEIGHT"
 


 This is the default map viewport range. The default value of 5 produces an
11x11 viewport. A value of -1 turns off the map display altogether. The client may automatically
scale down icons in order to conveniently fit the map on the player's screen.
 



 For non-square views, you can assign this to a text string of the form
"WIDTHxHEIGHT". For example, "11x11" is equivalent to a view depth of 5, but
you could make it wider like this: "13x11".
 



 This setting also affects the default range of the
 `view()` 
 ,
 `oview()` 
 ,
 `range()` 
 , and
 `orange()` 
 procedures.
 



 If the entire map is small enough to fit on one screen 
(arbitrarily defined to be 21x21 or less),
the default
 `view` 
 is automatically adjusted to fit the map. In
this case,
 `client.lazy_eye` 
 is also automatically turned on by
default, since you probably don't want the map to scroll around.
 




---
visibility var (world)
------------------------




**See also:** 


[OpenPort proc (world)](#/world/proc/OpenPort) 

[hub var (world)](#/world/var/hub) 





**Default value:** 


 1 (visible)
 


 This controls whether the world advertises itself in the
 [BYOND Hub](http://www.byond.com/games/) 
 when it has an open network
port for accepting players. The visibility of the world still depends on
whether any of the connected players has their location reporter turned on,
and that in turn relies on the pager being turned on.
 




---
Special notes
---------------



 This section of the reference should help explain some concepts that
may be harder to understand or that can use more clarification.
 





**Language features** 



[Numbers](#/{notes}/numbers) 

[Regular expressions](#/{notes}/regex) 

[Unicode](#/{notes}/Unicode) 




**Icons** 


[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 



**Map formats** 


[Topdown maps](#/{notes}/topdown) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 





**Movement** 



[Gliding](#/{notes}/gliding) 

[Pixel movement](#/{notes}/pixel-movement) 




**Display** 



[Understanding the renderer](#/{notes}/renderer) 

[HUD / screen objects](#/{notes}/HUD) 

[Color matrix](#/{notes}/color-matrix) 

[Filter effects](#/{notes}/filters) 

[Particle effects](#/{notes}/particles) 


[Color gradient](#/{notes}/color-gradient) 

[Generators](#/{notes}/generators) 




[Projection matrix](#/{notes}/projection-matrix) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 












---
BACKGROUND\_LAYER
-------------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 









 This is mostly no longer needed. A negative value for plane is the
preferred way to do show objects in the background. It can still be used
however when you want to rearrange objects in the same plane when using
 [PLANE\_MASTER](#/atom/var/appearance_flags) 
 for visual
effects.
 




 BACKGROUND\_LAYER
 
 is a special high value that can be added to the
regular layer of any atom.
 



 The purpose of this value is to make an atom appear below any regular
atoms, even if they share the same plane. In an isometric map for instance,
HUD objects will always appear above the map, but makeing a HUD object appear
behind the map was basically impossible without this feature until
 
 plane
 
 was implemented.
 



 When using this special layer, it should be added to the layer an atom
normally uses. For instance an obj should have a layer of
 
 BACKGROUND\_LAYER
+ OBJ\_LAYER
 
 .
 



 This can be mixed with
 
 TOPDOWN\_LAYER
 
 and
 
 EFFECTS\_LAYER
 
 ,
but it will take precedence over both. Anything with
 
 BACKGROUND\_LAYER
 
 will always appear below anything without it on the same plane.
 



 Images or overlays with
 
 FLOAT\_LAYER
 
 can be left alone. They will
automatically have the same layer as whatever atom they are attached to.
 




---
Big icons
-----------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[Blend proc (icon)](#/icon/proc/Blend) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Tiled icons](#/{notes}/tiled-icons) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 










 BYOND allows you to use icons that are not the same size as the tile size
defined in world.icon\_size. These icons can be manipulated with the /icon datum
using their raw, native size, and shown on the map in full size. To use the old
behavior where an atom can display only an icon of the normal tile size, use
the TILED\_ICON\_MAP value for map\_format instead.
 



 When you use an icon of non-standard size on an atom, the icon is "anchored"
to the southwest corner of the atom. If you are using a top-down view
(world.map\_format=TOPDOWN\_MAP), the icon will appear to spread out further to
the east and north. In an isometric map (world.map\_format=ISOMETRIC\_MAP), the
icon will cover additional tiles north and east as well. The "footprint" of an
isometric icon--the actual map tiles it covers--is always square, so if your
tile size is 64x64 and you use a 128x64 icon, the 128-pixel width means the
icon will cover a 2x2 section of map tiles.
 



 It is important to remember that using a big icon is a visual effect
 *only* 
 . It will not affect how the atom bumps into other atoms or
vice-versa.
 



 Big icons will affect layering--the order in which icons are drawn. In
general, because a big icon is covering more than one tile of the map, it will
try to draw above any other tiles in that space that are on the same layer.
This way, you can set a turf to use a big icon without having to change the
turfs to the north and east. If an atom has a big icon, any overlays and
underlays attached to it will be pulled forward as well, so they will draw in
front of anything on their same layer. In isometric mode this is about the same,
except that the layer isn't that important--anything in the way will just be
moved back behind the big icon.
 



 Note: Big overlays will not "pull forward" on their own. If the main atom
uses a single-tile icon, a big overlay attached to it will not try to draw in
front of other icons on the same layer. This is so that name labels, health
bar overlays, etc. will not cause any odd behavior. To be safe, you should
always specify a layer when adding an overlay.
 



 In isometric mode, layering is affected by the "distance" between the atom
and the viewer, so putting a regular-sized icon and part of a big icon on the
same tile could cause layering oddities. Tiles that are covered by a big icon
will tend to be drawn behind the big icon as mentioned above. For this reason,
any atoms whose icons cover more than one tile (the extra height of an
isometric icon doesn't count) should always be dense, and you should block
movement onto any tile covered by them.
 



 When manipulating icons with the /icon datum, you can still use Blend() to
combine icons of different sizes. By default, the icons will be lined up at
their southwest corners. You can change the position at which the second icon
is blended.
 




---
Color gradient
----------------




**See also:** 


[gradient proc](#/proc/gradient) 

[color var (atom)](#/atom/var/color) 

[Particle effects](#/{notes}/particles) 

[Color space](#/{{appendix}}/color-space) 






 A color gradient is a special list that defines a range of colors that you
can smoothly interpolate between. A simple example is a gradient from red to
white:
 


### 
 Example:



 list("red", "white")
// OR
list(0, "red", 1, "white")
 

 Applying a number like 0.2 to this gradient would give you a color that's
20% of the way from red to white. More complex gradients however are also
possible.
 



 The format of a gradient is a list that contains a number (the position
along the gradient, from 0 to 1 unless you use values outside that range)
followed by a color. You can have as complex a gradient as you like. If you
reuse the same number twice in a row, the gradient will have a sudden color
change at that point.
 



 It is also possible to skip numbers or colors, and they will be filled in
automatically with the previous number or color. The exceptions are at the
beginning and ends of the list; at the end of the gradient, the last color is
assigned a number 1 by default, and the first is assigned 0. If you skip
colors at the beginning, they will be filled in with the first color you use.
 



 Include "loop" anywhere in the list to make this a looped gradient. If you
don't, any numbers outside the gradient's range will be clamped to that range.
E.g., in a normal gradient ranging from 0 to 1, a number of 1.2 is
interpreted as 1 without a loop and 0.2 with a loop.
 



 Here are some more examples:
 


### 
 Example:



 // color wheel; ranges 0 to 6 and loops
list(0, "#f00", 1, "#ff0", 2, "#0f0", 3, "#0ff", 4, "#00f", 5, "#f0f", 6, "#f00", "loop")

// 10% each red, yellow, green, blue, with a 20% transition zone between each
// notice no color follows 0.4 or 0.7, so the previous color is used
list(0.1, "#f00", 0.3, "#ff0", 0.4, 0.6, "#008000", 0.7, 0.9, "#00f")

// green and black stripes
list(0.5, "#008000", 0.5, "#000000", "loop")
 

 You can also include "space" in the list, and give it an associated value
that describes the color space this gradient uses to interpolate between
colors. For instance,
 
 "space"=COLORSPACE\_HSL
 
 will use HSL
interpolation instead of the default RGB. See
 [Color space](#/{{appendix}}/color-space) 
 for more information.
 


### 
 Example:



 // color wheel with a different color space
list(0, "#f00", 3, "#0ff", 6, "#f00", "loop", "space"=COLORSPACE\_HSLA)
 

 Currently, color gradients are only used by particle effects and the
 [gradient
 
 proc](#/proc/gradient) 
 . With particles, if you use
a gradient the particle's color is given as a number, and that number is used
to look up its real color from the gradient. The number can change over time,
thus changing the particle's color.
 




---
Color matrix
--------------




**See also:** 


[color var (atom)](#/atom/var/color) 

[color var (client)](#/client/var/color) 

[MapColors proc (icon)](#/icon/proc/MapColors) 





 A color matrix is used to transform colors, in the same way that a matrix
represented by the
 
 /matrix
 
 datum is used to transform 2D coordinates.
A transformation matrix is 3x3, of which only 6 values are needed because the
last column is always the same. A color matrix, because it transforms four
different numbers instead of two, is 5x5.
 



```
                |rr rg rb ra 0|
                |gr gg gb ga 0|
[r g b a 255] x |br bg bb ba 0| = [r' g' b' a' 255]
                |ar ag ab aa 0|
                |cr cg cb ca 1|

```


 In easier-to-understand terms, this is how the result is calculated:
 



 new\_red = red \* rr + green \* gr + blue \* br + alpha \* ar + 255 \* cr
new\_green = red \* rg + green \* gg + blue \* bg + alpha \* ag + 255 \* cg
new\_blue = red \* rb + green \* gb + blue \* bb + alpha \* ab + 255 \* cb
new\_alpha = red \* ra + green \* ga + blue \* ba + alpha \* aa + 255 \* ca
 

 It is helpful to think of each row in the matrix as what each component of
the original color will become. The first row of the matrix is the rgba value
you'll get for each unit of red; the second is what each green becomes, and so
on.
 



 Because the fifth column of the matrix is always the same, only 20 of the
values need to be provided. You can use a color matrix with atom.color or
client.color in any of the following ways:
 




 RGB-only (9 to 12 values)
 

 list(rr,rg,rb, gr,gg,gb, br,bg,bb, cr,cg,cb)
 

 RGBA (16 to 20 values)
 

 list(rr,rg,rb,ra, gr,gg,gb,ga, br,bg,bb,ba, ar,ag,ab,aa, cr,cg,cb,ca)
 

 Row-by-row (3 to 5
 
 rgb()
 
 values, or null to use the default row)
 

 list(red\_row, green\_row, blue\_row, alpha\_row, constant\_row)
 


 Reading a color var that has been set to a matrix will return the full
20-item list, where every 4 items represent a row in the matrix (without the
fifth column).
 



 In the
 
 MapColors()
 
 icon proc, the values are sent as arguments,
not as a list.
 




---
EFFECTS\_LAYER
----------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 









 This is mostly no longer needed. A negative value for plane is the
preferred way to do show objects in the background. It can still be used
however when you want to rearrange objects in the same plane when using
 [PLANE\_MASTER](#/atom/var/appearance_flags) 
 for visual
effects.
 




 EFFECTS\_LAYER
 
 is a special high value that can be added to the
regular layer of any atom.
 



 The purpose of this value is to make an atom appear above any regular
atoms. For instance, in an isometric map if you want to display a character's
name below them, it does not make much sense to have nearer objects cover up
that name, so you can tell the name overlay to use
 
 EFFECTS\_LAYER +
MOB\_LAYER
 
 and it will show up on top of all the normal icons on the map.
This has been somewhat obviated by
 
 plane
 
 but may still be useful in
some cases.
 



 When using this special layer, it should be added to the layer an atom
normally uses. For instance an obj should have a layer of
 
 EFFECTS\_LAYER +
OBJ\_LAYER
 
 .
 



 This can be mixed with
 
 TOPDOWN\_LAYER
 
 , in non-topdown map formats.
Anything in
 
 TOPDOWN\_LAYER
 
 will display on top of
 
 EFFECTS\_LAYER
 
 , and
 
 TOPDOWN\_LAYER + EFFECTS\_LAYER
 
 will be
above both.
 



 This can also be mixed with
 
 BACKGROUND\_LAYER
 
 , which takes priority
over everything else.
 



 Images or overlays with
 
 FLOAT\_LAYER
 
 can be left alone. They will
automatically have the same layer as whatever atom they are attached to.
 




---
Filter effects
----------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[filter proc](#/proc/filter) 

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 







 Filters are a way of adding special effects to an icon, or a group of icons
(see
 
 KEEP\_TOGETHER
 
 in
 [appearance\_flags](#/atom/var/appearance_flags) 
 ), by
post-processing the image. A filter object describes a specific form of image
processing, like for instance a blur or a drop shadow. Filters can be added or
removed at will, and can even be animated.
 



 A filter is created by using the
 [filter proc](#/proc/filter) 
 like
so:
 



 // halo effect
mob.filters += filter(type="drop\_shadow", x=0, y=0,\
 size=5, offset=2, color=rgb(255,255,170))
 

 These are the filters currently supported:
 


* [Alpha mask](#/{notes}/filters/alpha)
* [Angular blur](#/{notes}/filters/angular_blur)
* [Bloom](#/{notes}/filters/bloom)
* [Color matrix](#/{notes}/filters/color)
* [Displacement map](#/{notes}/filters/displace)
* [Drop shadow](#/{notes}/filters/drop_shadow)
* [Gaussian blur](#/{notes}/filters/blur)
* [Layering (composite)](#/{notes}/filters/layer)
* [Motion blur](#/{notes}/filters/motion_blur)
* [Outline](#/{notes}/filters/outline)
* [Radial blur](#/{notes}/filters/radial_blur)
* [Rays](#/{notes}/filters/rays)
* [Ripple](#/{notes}/filters/ripple)
* [Wave](#/{notes}/filters/wave)




---
Alpha mask filter
-------------------




**See also:** 


[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 





 Format:
 

 filter(type="alpha", ...)
 



 Args:
 

 x: Horizontal offset of mask (defaults to 0)
 

 y: Vertical offset of mask (defaults to 0)
 

 icon: Icon to use as a mask
 

 render\_source:
 
 render\_target
 
 to use as a mask
 

 flags: Defaults to 0; use see below for other flags
 


 Uses an icon or render target as a mask over this image. Every pixel that
is transparent in either the image or the mask, is transparent in the result.
 



 The
 
 x
 
 and
 
 y
 
 values can move the mask from its normal
position. By default, the mask is centered over the center of the image.
 



 The
 
 MASK\_INVERSE
 
 flag will invert the alpha mask so that opaque
areas in the mask become transparent, and vice-versa. There is also a
 
 MASK\_SWAP
 
 flag which treats the source image as the mask and
vice-versa, which might be useful for some effects.
 



 Note: Unlike many other filters, this filter
 **is** 
 taken into account
for mouse-hit purposes.
 




---
Angular blur filter
---------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Motion blur (filters)](#/{notes}/filters/motion_blur) 






 Format:
 

 filter(type="angular\_blur", ...)
 



 Args:
 

 x: Horizontal center of effect, in pixels, relative to image center
 

 y: Vertical center of effect, in pixels, relative to image center
 

 size: Amount of blur (defaults to 1)
 


 Blurs the image by a certain amount in a circular formation, as if the
image is spinning. The size of the blur can roughly be thought of in "degrees"
worth of blur. As the distance from the center increases, the blur becomes
more noticeable since the same amount of angular motion has to travel farther
along a circle.
 



 Typically this blur is used with an entire plane, but it could be used to
give a sense of motion blur to a spinning object.
 



 Note: Large blurs will look worse toward the edges due to limited sampling.
Loss of accuracy will appear where
 
 size
 
 × distance is greater
than about 300. You can increase accuracy by breaking up large sizes into
multiple filter passes with differing sizes. The blur used is Gaussian, so
combining blur sizes A and B will give a total size of
sqrt(A
 2 
 +B
 2 
 ).
 




---
Bloom filter
--------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 





 Format:
 

 filter(type="bloom", ...)
 



 Args:
 

 threshold: Color threshold for bloom
 

 size: Blur radius of bloom effect (see Gaussian blur)
 

 offset: Growth/outline radius of bloom effect before blur
 

 alpha: Opacity of effect (default is 255, max opacity)
 


 Post-processing effect that makes bright colors look like they're a strong
light source, spreading their light additively to other nearby pixels. This is
a complex effect that involves multiple shader passes. For both performance and
visual reasons, it is usually best applied to an entire plane rather than to
individual objects.
 



 The color
 
 threshold
 
 determines which pixels this effect applies to.
If any of the red, green, or blue components of the pixel are greater than the
same component for the threshold, that pixel will bloom. The blooming pixels
then have their colors spread outward to create a glow that gets added to the
original image.
 



 The
 
 offset
 
 and
 
 size
 
 parameters are used to control the
glow effect. They work the same as they do in the drop shadow filter:
 
 offset
 
 causes the light to grow outwards, and a blur of
 
 size
 
 is then applied to soften it. Often just using a blur alone will produce a
pleasing effect. By playing with these two values you can make the bloom effect
appear differently.
 



 The
 
 alpha
 
 value is applied to any light contributions from bloomed
pixels that get added to the original image, so values lower than 255 can make
the effect less pronounced. This can be very useful if you choose to animate
the filter.
 




---
Gaussian blur filter
----------------------




**See also:** 


[Motion blur (filters)](#/{notes}/filters/motion_blur) 

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 







 Format:
 

 filter(type="blur", ...)
 



 Args:
 

 size: Amount of blur (defaults to 1)
 


 Blurs the image by a certain amount. The size of the blur can roughly be
thought of in "pixels" worth of blur.
 



 Note: Large blurs will result in reduced performance. The
highest size that can be handled easily in this filter is 6. Higher sizes
require multiple passes, although the filter will "cheat" and use low-quality
passes for much higher sizes.
 




---
Color matrix filter
---------------------




**See also:** 


[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 

[Color space](#/{{appendix}}/color-space) 






 Format:
 

 filter(type="color", ...)
 



 Args:
 

 color: A color matrix
 

 space: Value indicating color space: defaults to
 
 FILTER\_COLOR\_RGB
 



 Applies a color matrix to this image. Unlike with the atom.color var, you
can apply color conversions other than the regular RGBA color space, depending
on the value of
 
 space
 
 . See
 [Color
space](#/{{appendix}}/color-space) 
 for more information.
 




---
Displacement map filter
-------------------------




**See also:** 


[Alpha mask (filters)](#/{notes}/filters/alpha) 

[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 






 Format:
 

 filter(type="displace", ...)
 



 Args:
 

 x: Horizontal offset of map (defaults to 0)
 

 y: Vertical offset of map (defaults to 0)
 

 size: Maximum distortion, in pixels
 

 icon: Icon to use as a displacement map
 

 render\_source:
 
 render\_target
 
 to use as a displacement map
 


 Uses an icon or render target as a template for various warping effects on
the main image.
 



 In the displacement map, pixels that have a higher red component will make
the image appear to warp to the left, lower reds warp it to the right, and
gray (r=128) will cause no horizontal warping. The green component affects the
vertical: higher to warp upward, lower to warp downward. Transparent pixels in
the displacement map will have no effect.
 



 This can be used for very complex distortion, unlike other distortion
filters such as wave and ripple that are confined to specific equations.
 




---
Drop shadow filter
--------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Outline (filters)](#/{notes}/filters/outline) 





 Format:
 

 filter(type="drop\_shadow", ...)
 



 Args:
 

 x: Shadow horizontal offset (defaults to 1)
 

 y: Shadow horizontal offset (defaults to -1)
 

 size: Blur amount (defaults to 1; negative values create inset shadows)
 

 offset: Size increase before blur (defaults to 0)
 

 color: Shadow color (defaults to 50% transparent black)
 


 Applies a drop shadow to this image. This is a combination of multiple
filters, since it will apply an outline if
 
 offset
 
 is included, a
Gaussian blur to the shadow, and will underlay the shadow beneath the image.
 



 You can also think of this filter as an outer glow.
 



 If you use a
 
 size
 
 less than 0, the shadow will appear inside the
image instead. This would be an inset shadow, or inner glow.
 




---
Layering (composite) filter
-----------------------------




**See also:** 


[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 





 Format:
 

 filter(type="layer", ...)
 



 Args:
 

 x: Horizontal offset of second image (defaults to 0)
 

 y: Vertical offset of second image (defaults to 0)
 

 icon: Icon to use as a second image
 

 render\_source:
 
 render\_target
 
 to use as a second image
 

 flags:
 
 FILTER\_OVERLAY
 
 (default) or
 
 FILTER\_UNDERLAY
 


 color:
 [Color](#/atom/var/color) 
 or color matrix to apply to second image
 

 transform:
 [Transform](#/atom/var/transform) 
 to apply to second image
 

 blend\_mode:
 [Blend mode](#/atom/var/blend_mode) 
 to apply to the top image
 


 Composites another image over or under this image. Using the
 
 FILTER\_OVERLAY
 
 flag, which is the default, puts the second image
on top of what's already here.
 
 FILTER\_UNDERLAY
 
 puts it underneath.
 



 The
 
 x
 
 and
 
 y
 
 values can move the mask from its normal
position. By default, the second image is centered over the center of the
first.
 



 The
 
 color
 
 ,
 
 transform
 
 , and
 
 blend\_mode
 
 vars are
available for convenience. Because the bottom image is drawn over a blank
background,
 
 blend\_mode
 
 is always applied to the top image. All of
the other vars apply to the second image being drawn.
 



 Note: Transforms use default bilinear scaling, since
 [PIXEL\_SCALE](#/atom/var/appearance_flags) 
 is not
available here.
 



 Note: Like most other filters, this filter is
 **not** 
 taken into account
for mouse-hit purposes. Any layered icons will be strictly visual.
 




---
Motion blur filter
--------------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[Gaussian blur (filters)](#/{notes}/filters/blur) 





 Format:
 

 filter(type="motion\_blur", ...)
 



 Args:
 

 x: Blur vector on the X axis (defaults to 0)
 

 y: Blur vector on the Y axis (defaults to 0)
 


 Applies Gaussian blur in one direction only. The amount and direction are
both specified by
 
 x
 
 and
 
 y
 
 . The size of the blur is equal to
 
 sqrt(x\*x + y\*y)
 
 .
 



 See
 [Gaussian blur](#/{notes}/filters/blur) 
 for more information.
 




---
Outline filter
----------------




**See also:** 


[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 




 Format:
 

 filter(type="outline", ...)
 



 Args:
 

 size: Width in pixels (defaults to 1)
 

 color: Outline color (defaults to black)
 

 flags: Defaults to 0 (see below)
 


 Applies an outline to this image.
 



 At larger sizes, the outline is less accurate and will take more passes to
produce. Performance and appearance are best at sizes close to 1 or less.
 




 flags
 
 can be a combination of the following values:
 




 0
 

 Ordinary outline
 

 OUTLINE\_SHARP
 

 Avoid antialiasing in the outline
 

 OUTLINE\_SQUARE
 

 Extend the outline sharply from corner pixels; for a box this will maintain a box shape without rounded corners
 



---
Radial blur filter
--------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Motion blur (filters)](#/{notes}/filters/motion_blur) 






 Format:
 

 filter(type="radial\_blur", ...)
 



 Args:
 

 x: Horizontal center of effect, in pixels, relative to image center
 

 y: Vertical center of effect, in pixels, relative to image center
 

 size: Amount of blur per pixel of distance (defaults to 0.01)
 


 Blurs the image by a certain amount outward from the center, as if the
image is zooming in or out. As the distance from the center increases, the
amount of blurring increases, and near the center the blur is hardly visible
at all. The
 
 size
 
 value is smaller by default for this filter than it
is for other filters, since it's typically used with an entire plane where the
distance from the center can easily be several hundred pixels.
 



 Typically this blur is used with an entire plane.
 



 Note: Large blurs will look worse toward the edges due to limited sampling.
Loss of accuracy will begin when
 
 size
 
 × distance is greather
than 6. You can increase accuracy by breaking up large sizes into multiple
filter passes. The blur used is Gaussian, so combining blur sizes A and B will
give a total size of sqrt(A
 2 
 +B
 2 
 ).
 




---
Rays filter
-------------




 Format:
 

 filter(type="rays", ...)
 



 Args:
 

 x: Horiztonal position of ray center, relative to image center (defaults to 0)
 

 y: Vertical position of ray center, relative to image center (defaults to 0)
 

 size: Maximum length of rays (defaults to 1/2 tile width)
 

 color: Ray color (defaults to white)
 

 offset: "Time" offset of rays (defaults to 0, repeats after 1000)
 

 density: Higher values mean more, narrower rays (defaults to 10, must be whole number)
 

 threshold: Low-end cutoff for ray strength (defaults to 0.5, can be 0 to 1)
 

 factor: How much ray strength is related to ray length (defaults to 0, can be 0 to 1)
 

 flags: Defaults to
 
 FILTER\_OVERLAY | FILTER\_UNDERLAY
 
 (see below)
 


 Draws random rays that radiate outward from a center point. (That point may
be outside of the image.) As they move outward, their alpha value diminishes
linearly. These are meant to be animated. The
 
 offset
 
 value determines
the "time", where every jump of +1 can be a very different set of rays, and
every 1000 units this filter will repeat.
 



 The
 
 threshold
 
 value can be thought of as a way of culling
lower-strength rays. Ray strength is anywhere from 0 to 1 at any given angle,
but values below
 
 threshold
 
 may as well be 0. Values above that are
re-scaled into a range of 0 to 1.
 



 The
 
 factor
 
 parameter allows you to tie the ray's length to its
strength. At 0, the length of every ray is the same. At 1, the length ranges
from 0 to
 
 size
 
 . Generally speaking, the higher
 
 factor
 
 is,
the more the rays will appear to move outward as they strengthen and inward
as they weaken.
 



 Ray
 
 color
 
 can be provided as a matrix. Only the diagonal values of the
color matrix will be used, but using a matrix will allow you to set values
outside of the normal color range.
 




 flags
 
 can have the following values:
 




 0
 

 The rays are drawn alone, erasing the existing image (useful for some effects).
 

 FILTER\_OVERLAY
 

 The rays are overlaid on top of the existing image.
 

 FILTER\_UNDERLAY
 

 The rays are drawn underneath the existing image.
 

 FILTER\_OVERLAY | FILTER\_UNDERLAY
 

 Default. For plane masters, this will use the
 
 FILTER\_OVERLAY
 
 behavior and draw the rays over the plane, and for all other images it will default to
 
 FILTER\_UNDERLAY
 
 to draw the rays beneath them.
 



---
Ripple filter
---------------




**See also:** 


[Wave (filters)](#/{notes}/filters/wave) 




 Format:
 

 filter(type="ripple", ...)
 



 Args:
 

 x: Horiztonal position of ripple center, relative to image center (defaults to 0)
 

 y: Vertical position of ripple center, relative to image center (defaults to 0)
 

 size: Maximum distortion in pixels (defaults to 1)
 

 repeat: Wave period, in pixels (defaults to 2)
 

 radius: Outer radius of ripple, in pixels (defaults to 0)
 

 falloff: How quickly ripples lose strength away from the outer edge (defaults to 1)
 

 flags: Defaults to 0; use
 
 WAVE\_BOUNDED
 
 to keep distortion within the image
 


 Applies a ripple distortion effect to this image.
 



 This filter is meant to be animated. A good animation will typically start
at a
 
 radius
 
 of 0 and animate to a larger value, with
 
 size
 
 decreasing to 0.
 



 The
 
 falloff
 
 parameter can be tweaked to your liking. A value of 1
should look reasonably like ripples in water, with the inner ripples losing
strength. A value of 0 will cause no reduction in strength.
 



 The equation governing the ripple distortion is size × sin(2πr') ÷ (2.5 × falloff × r'
 2 
 + 1),
where r' = (radius - distance) ÷ repeat.
 



 Up to 10 ripples can be stacked together in a single pass of the filter, as
long as they have the same
 
 repeat
 
 ,
 
 falloff
 
 , and
 
 flags
 
 values. (See the wave filter for the
 
 WAVE\_BOUNDED
 
 flag.)
 




---
Wave filter
-------------




**See also:** 


[Ripple (filters)](#/{notes}/filters/ripple) 




 Format:
 

 filter(type="wave", ...)
 



 Args:
 

 x: Horiztonal direction and period of wave
 

 y: Vertical direction and period of wave
 

 size: Maximum distortion in pixels (defaults to 1)
 

 offset: Phase of wave, in periods (e.g., 0 to 1)
 

 flags: Defaults to 0; see below for other flags
 


 Applies a wave distortion effect to this image.
 



 The
 
 x
 
 and
 
 y
 
 parameters specify both the direction and
period of the wave; the period is
 
 sqrt(x\*x + y\*y)
 
 .
 



 This filter is meant to be animated, from whatever
 
 offset
 
 you want
to
 
 offset+1
 
 , and then repeating. With multiple waves, you can produce
a very convincing water effect.
 


### 
 Example



 #define WAVE\_COUNT 7
atom/proc/WaterEffect()
 var/start = filters.len
 var/X,Y,rsq,i,f
 for(i=1, i<=WAVE\_COUNT, ++i)
 // choose a wave with a random direction and a period between 10 and 30 pixels
 do
 X = 60\*rand() - 30
 Y = 60\*rand() - 30
 rsq = X\*X + Y\*Y
 while(rsq<100 || rsq>900) // keep trying if we don't like the numbers
 // keep distortion (size) small, from 0.5 to 3 pixels
 // choose a random phase (offset)
 filters += filter(type="wave", x=X, y=Y, size=rand()\*2.5+0.5, offset=rand())
 for(i=1, i<=WAVE\_COUNT, ++i)
 // animate phase of each wave from its original phase to phase-1 and then reset;
 // this moves the wave forward in the X,Y direction
 f = filters[start+i]
 animate(f, offset=f:offset, time=0, loop=-1, flags=ANIMATION\_PARALLEL)
 animate(offset=f:offset-1, time=rand()\*20+10)
 

 The equation governing the wave distortion is size × sin(2π(d - offset)),
where d is the number of wave periods' distance from the center along the x, y
direction.
 



 The
 
 WAVE\_SIDEWAYS
 
 flag will cause the distortion to be transverse
(perpendicular) to the wave instead of in the same direction as the wave. The
 
 WAVE\_BOUNDED
 
 flag limits the distortion to the confines of this image,
instead of lettings its pixels spill out a little further from the distortion
(and likewise, transparent pixels spill inward).
 



 Up to 10 waves can be stacked together in a single pass of the filter, as long as they
have the same
 
 WAVE\_BOUNDED
 
 flags.
 




---
Generators
------------




**See also:** 


[Particle effects](#/{notes}/particles) 

[generator proc](#/proc/generator) 

[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 






 A generator is an object that can produce a random number, vector (list of 3 numbers), color (as a text string), or color matrix (list of 20 numbers) in a specified range according to rules you set down. It is used primarily for particle effects, since it can run on the client.
 



 There are several types of generators:
 


* **Numbers:** 
 Generate a random real number.
* **Vectors:** 
 Generate a random vector.
* **Shapes:** 
 Generate a random vector within a specific shaped region.
* **Colors:** 
 Generate a random color or color matrix.



 Generators can also be chained together with math operators and some procs. The second value can be a regular value instead of a generator, so for instance you can multiply a vector by 2, or by a matrix to transform it.


| 
 Operators
  | 
 Action
  |
| --- | --- |
| 
 + - \* /
  | 
 Arithmetic operators. You can multiply a 3D vector by a color matrix (where red,green,blue in the matrix correspond to x,y,z) to do a 3D transform, or by a 2D matrix for a 2D transform.
  |
| 
 - (unary)
  | 
 Negate the value, same as multiplying by -1.
  |
| 
 turn(), generator.Turn()
  | 
 Rotate a vector clockwise in the XY plane.
  |




---


Gliding
---------




**See also:** 


[Pixel movement](#/{notes}/pixel-movement) 

[animate\_movement var (movable atom)](#/atom/movable/var/animate_movement) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[glide\_size var (movable atom)](#/atom/movable/var/glide_size) 

[bound\_x var (movable atom)](#/atom/movable/var/bound_x) 

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[fps var (client)](#/client/var/fps) 















 Gliding is a "glitz" effect applied by BYOND to cover up the visual sins
of tile-based movement, by making objects and the map appear to move smoothly
from one tile to another instead of immediately jumping. It is also available to
smooth over small jumps in pixel movement that might occur, for instance if the
client FPS is set higher than the server's.
 



 To control the gliding speed of an atom, set
 `glide_size` 
 to the
value of your choice. If this is not set, the client will attempt to adjust
the speed manually.
 `glide_size` 
 is measured in server ticks, so
if
 `client.fps` 
 is set to a value greater than
 `world.fps` 
 ,
it will be scaled appropriately.
 



 Whether an object glides or jumps is based on how far it moves relative to
its
 
 step\_size
 
 value, which by default is a full tile width. If the
movement goes too far past
 
 step\_size
 
 in the X or Y directions, it's
no longer a glide.
 



 The
 
 animate\_movement
 
 var can be used to control the way in which
an object glides, or suppress gliding altogether.
 



 By using the
 
 LONG\_GLIDE
 
 flag in
 
 appearance\_flags
 
 , a
diagonal glide will take just as long as a cardinal-direction glide by moving
a fullt
 
 glide\_size
 
 pixels in the dominant X or Y direction.
Otherwise, gliding tries to move by that many pixels in strict Euclidean
distance (a straight line) and diagonal glides take longer.
 



 In
 [LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode) 
 ,
gliding is turned off if you set any of the bound or step vars for an atom to
a non-default value. The only gliding that occurs in this case is when
client.fps is higher than world.fps. All other movement modes base gliding on
an atom's
 
 glide\_size
 
 value.
 




---
HUD / screen objects
----------------------




**See also:** 


[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[screen var (client)](#/client/var/screen) 

[view var (client)](#/client/var/view) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 









 HUD stands for Heads-Up Display, and refers to any atoms that appear on
the screen but don't move when the player moves. These are also called screen
objects. Any movable atom can be added to the HUD by setting its
 
 screen\_loc
 
 var, and adding it to
 
 client.screen
 
 for each user
who is supposed to see it. This can be used to display a character's vital
stats, scores, etc.
 



 If you want to have something like a health meter or name attached to a
moving atom, use overlays or
 
 /image
 
 objects instead. An
 
 /image
 
 object is similar to a screen object in that it can be shown
to only certain players instead of being shown to everyone.
 



 The size of the screen depends on
 
 client.view
 
 (or
 
 world.view
 
 ),
 
 world.map\_format
 
 , and
 
 world.icon\_size
 
 .
In a normal topdown map format,
 
 client.view
 
 is the same as the screen
size; in other map formats the screen might be a different size.
 



 The
 
 screen\_loc
 
 var can be set to a value like
 
 "1,1"
 
 (the
southwest tile of the screen),
 
 "4,NORTH"
 
 (fourth tile from the west,
along the north side of the screen),
 
 "SOUTHEAST"
 
 , and so on. You can
also include pixel offsets, percentages, and specify two corners to tile an
icon repeatedly from one end to the other. See
 [screen\_loc](#/atom/movable/var/screen_loc) 
 for more
details.
 




 screen\_loc
 
 can also be used to stretch the bounds of the HUD. A
value of
 
 "0,0"
 
 will cause the atom to appear to the southwest of the
southwest-most tile on the visible map, outside of the regular map bounds.
Using HUDs in this way, you can provide a nice decorative "frame" for your map.
 



 More complex
 



 You can use HUDs in other map controls as well, by preceding screen\_loc with
the name of the map you will use followed by a colon. For instance,
 
 screen\_loc="map2:1,1"
 
 will show an icon in the southwest corner of the
 
 map2
 
 control. The actual size of a secondary HUD is based on how far
out the icons in it extend in any direction. If you have one icon at
 
 "map2:1,1"
 
 and another at
 
 "map2:4,3"
 
 , then that HUD will be
four tiles wide and three high.
 




---
Isometric maps
----------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[pixel\_w var (atom)](#/atom/var/pixel_w) 

[pixel\_z var (atom)](#/atom/var/pixel_z) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[Side-view maps](#/{notes}/side) 

[Topdown maps](#/{notes}/topdown) 

[HUD](#/{notes}/HUD) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/topdown_layer) 















![](data:image/png;charset=utf-8;base64,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)


 Isometric projection is a form of pseudo-3D in which the 2D icons used by
BYOND can be arranged in a way to give the appearance of three dimensions. If
you look at a map top-down, each tile on the map is a square. The map is
rotated 45° clockwise and then tilted at an angle (30°) so that each
square now looks like a foreshortened diamond from the viewer's perspective.
What was once north now points to the northeast end of the viewer's screen;
what was once east now points southeast to the viewer. Tiles that are more to
the south or east are "nearer" to the viewer, and tiles that are north or west
are "farther". The actual direction the map faces can be changed by using
 
 client.dir
 
 .
 



 It is important to remember that this is an illusion of 3D, not real 3D.
 



 To use isometric mapping, set
 
 world.map\_format
 
 to
 
 ISOMETRIC\_MAP
 
 . You should set
 
 world.icon\_size
 
 so the tile
width is a multiple of 4 pixels. The width of the tile is highly important.
The height of your tiles should be at least half that value. BYOND uses a 2:1
isometric format, meaning that the diamond base of each tile is half as high
as its width. For example if you have a 64x64 tile size, every diamond in the
map will be 64 pixels wide by 32 high, and you have an extra 32 pixels at the
top of your icon for vertical projections like buildings. If you set the tile
size to 64x80, the base is still a 64x32 diamond and you have 48 pixels left
over for vertical structures.
 



 In this mode
 
 pixel\_x
 
 and
 
 pixel\_y
 
 will offset icons along the
"ground". To adjust horizontal and vertical positions, use the
 
 pixel\_w
 
 and
 
 pixel\_z
 
 vars.
 


### 
 Layers



 The
 
 layer
 
 var behaves differently in isometric mode. Because some
tiles are nearer to the viewer than others, the tiles that are farther back
need to be drawn first so they are behind any tiles that should go in front of
them. So in isometric mode, the back row of tiles (a diagonal line of them) is
drawn first, followed by the next row forward, and so on. The
 
 layer
 
 var only matters when icons overlap each other in the "physical" space, like
an obj sitting on a turf.
 



 When pixel or step offsets, or gliding, place an object on multiple turfs,
it is drawn on top of the nearer turf (assuming its layer is higher).
 



 Using icons wider than the regular tile size can have an impact on layering
as well. See
 [Big icons](#/{notes}/big-icons) 
 for more information.
 



 Because of the order in which icons are drawn, you may want to limit the
ability of an atom to cut diagonally around corners. While moving northeast
behind a dense wall, for instance, a mob might temporarily appear in front of
the wall because its pixel offsets (from gliding) temporarily put it on the
same tile as the wall. If you do not want to limit corner-cutting, a simple
workaround for this case is to give the wall a higher layer than the mob.
 



 Screen objects (in
 
 client.screen
 
 ) are always drawn on top of all
isometric tiles, as is the case in other map modes as well.
 



 Since it may be desirable in some games to use a topdown map for some
situations (like a special battle map), you can add
 
 TOPDOWN\_LAYER
 
 to
any atom's layer—e.g.,
 
 TOPDOWN\_LAYER+TURF\_LAYER
 
 —to make
it appear in topdown mode. Topdown and isometric tiles really aren't meant to
be mixed, but if they do mix you'll see topdown tiles always display above
isometric tiles, just like screen objects do. The best way to use this is to
apply
 
 TOPDOWN\_LAYER
 
 to every tile in a certain part of the map that
the players can't walk to.
 



 If you want to use an overlay that should not be covered by other "nearer"
icons on the map, such as a name or health meter, you can add
 
 EFFECTS\_LAYER
 
 to the overlay's layer. Icons with
 
 EFFECTS\_LAYER
 
 will draw above regular icons. Then objects with
 
 TOPDOWN\_LAYER
 
 will draw on top of everything else. However, be aware
that
 
 EFFECTS\_LAYER
 
 has largely been superseded by the
 
 plane
 
 var.
 


### 
 Screen size



 In this mode,
 
 world.view
 
 or
 
 client.view
 
 is used to define
the minimum number of map tiles you will see,
 *not* 
 the screen/HUD size
which is calculated from client.view. Extra map tiles are shown to fill out
the screen size. HUD objects use screen coordinates, so 1,1 is still the lower
left.
 



 The actual HUD size is always a full number of tiles, whose size is defined
by
 
 world.icon\_size
 
 . If you have a tile size of
 
 64x64
 
 , and
 
 world.view=6
 
 (a 13x13 map), a full 13x13 diamond of map tiles will be
shown. The width of this diamond is 13 tiles. The height is only half that,
plus whatever vertical space is needed to show the icons in that area. Then
everything is rounded up to a full tile size, so the result is a 13x7-tile
screen. This is the formula you need if you want to calculate the screen size:
 



 pixel\_width = round(icon\_width \* (view\_width + view\_height) / 2)
pixel\_height = round(icon\_width \* (view\_width + view\_height - 2) / 4) + icon\_height

screen\_width = round((pixel\_width + icon\_width - 1) / icon\_width)
screen\_height = round((pixel\_height + icon\_height - 1) / icon\_height)
 

 If you use
 
 TOPDOWN\_LAYER
 
 , any topdown sections of the map will be
limited to this same view.
 




---
Numbers
---------



 In DM, all numbers are stored in floating point format. Specifically,
single-precision (32-bit) floating point. This is important to know if you
think you will be working with large numbers or decimal values a lot, because
the accuracy of the numbers is limited.
 



 32-bit floating point numbers can represent integers from -16777216
to 16777216 (2
 24 
 ). Non-integer values can get about as small as
2
 -126 
 and as large as 2
 127 
 .
 



 Floating point numbers do not handle most decimal values precisely. For
instance, 0.1 is not exactly 0.1, because floating point numbers are stored
in a binary format and in binary, 1/10 is a fraction that repeats
forever—the same way 1/3 repeats as 0.33333... in decimal numbers. It
ends up being rounded off, either a little higher or a littler lower than
its true value. This means that the following loop won't work like you might
expect:
 


### 
 Example:



 for(i = 0, i < 100, i += 0.1)
 world << i
 

 You might expect that code to loop exactly 1000 times, with
 
 i
 
 going from 0 up to 99.9 before stopping. The truth is more complicated,
because 0.1 stored in floating point is actually greater than the exact value
of 0.1. Other values might be more or less than their exact numbers, and as
you add these numbers together repeatedly you'll introduce more and more
rounding error.
 



 Even more insidious, if you add 0.1 a bunch of times starting from 0, and
then subtract it out again the same number of times, the result you get may
not be 0. This is counterintuitive, because you might expect rounding errors
to reverse themselves in the same order they crept in. Unfortunately it
doesn't work that way.
 



 You can correct for rounding error somewhat by using the
 [round
 
 proc](#/proc/round) 
 to adjust the loop var each time,
although for performance reasons it might be preferable to find another
alternative.
 



 for(i = 0, i < 100, i = round(i + 0.1, 0.1))
 world << i
 

 Only fractions whose denominators are powers of 2 are immune to this
rounding error, so 0.5 is in fact stored as an exact value.
 



 Another place floating point may lose accuracy is when you try to add
numbers of very different sizes. For instance as stated above, the upper
limit for accurate integers is 16777216. If you try to use a number such
as 100 million it will only be approximate, so adding 1 to that number
won't actually change it because the 1 is so much smaller, it will be
gobbled up by rounding error.
 



 Also for the same reasons stated above, division will cost you
accuracy. Again you can divide by powers of 2 easily enough, and you can
divide an integer by any of its factors (like dividing 9 by 3) without a
problem, but a fraction like 1/3 will repeat forever so it gets rounded
to as much precision as floating point can manage.
 



 In decimal, floating point numbers have at least six decimal digits of
precision. Since they're actually stored in binary, their true precision
is exactly 24 bits.
 




---
Particle effects
------------------




**See also:** 


[particles (movable atom var)](#/atom/movable/var/particles) 

[Generators](#/{notes}/generators) 

[generator proc](#/proc/generator) 

[Projection matrix](#/{notes}/projection-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







 A particle set is a special effect, whose computations are handled entirely
on the client, that spawns and tracks multiple pixels or icons with a
temporary lifespan. Examples of this might be confetti, sparks, rocket
exhaust, or rain or snow. Particles are rendered on a special surface and that
gets attached to an obj or a mob like an overlay.
 



 Particles can exist in 3 dimensions instead of the usual 2, so a particle's
position, velocity, and other values may have a z coordinate. To make use of
this z coordinate, you can use a
 [projection
matrix](#/{notes}/projection-matrix) 
 . (The value of the z coordinate must be between -100 and
100 after projection. Otherwise it's not guaranteed the particle will be
displayed.)
 



 To create a particle set, use
 
 new
 
 to create a new
 
 /particles
 
 datum, and then you can set the datum's vars. The vars can
be set to constant values, or generator functions that will allow the client
to choose from a range of values when spawning those particles. (The easiest
way to handle this is to create your own type that inherits from
 
 /particles
 
 , and set up the parameters you'll want at compile-time.)
 



 After the datum is created, it can be assigned to an obj or mob using their
 
 particles
 
 var. The particles will appear on the map wherever that obj
or mob appears.
 


### 
 Example:



 particles/snow
 width = 500 // 500 x 500 image to cover a moderately sized map
 height = 500
 count = 2500 // 2500 particles
 spawning = 12 // 12 new particles per 0.1s
 bound1 = list(-1000, -300, -1000) // end particles at Y=-300
 lifespan = 600 // live for 60s max
 fade = 50 // fade out over the last 5s if still on screen
 // spawn within a certain x,y,z space
 position = generator("box", list(-300,250,0), list(300,300,50))
 // control how the snow falls
 gravity = list(0, -1)
 friction = 0.3 // shed 30% of velocity and drift every 0.1s
 drift = generator("sphere", 0, 2)
obj/snow
 screen\_loc = "CENTER"
 particles = new/particles/snow

mob
 proc/CreateSnow()
 client?.screen += new/obj/snow
 

 These are the vars that can be used in a particle set. "Tick" refers to a
BYOND standard tick of 0.1s.


| 
 Particle vars that affect the entire set (generators are not allowed for these)
  |
| --- |
| 
 Var
  | 
 Type
  | 
 Description
  |
| 
 width
  | 
 num
  | 
 Size of particle image in pixels
  |
| 
 height
  |
| 
 count
  | 
 num
  | 
 Maximum particle count
  |
| 
 spawning
  | 
 num
  | 
 Number of particles to spawn per tick (can be fractional)
  |
| 
 bound1
  | 
 vector
  | 
 Minimum particle position in x,y,z space; defaults to list(-1000,-1000,-1000)
  |
| 
 bound2
  | 
 vector
  | 
 Maximum particle position in x,y,z space; defaults to list(1000,1000,1000)
  |
| 
 gravity
  | 
 vector
  | 
 Constant acceleration applied to all particles in this set (pixels per squared tick)
  |
| 
 gradient
  | [color gradient](#/{notes}/color-gradient)  | 
 Color gradient used, if any
  |
| 
 transform
  | [matrix](#/{notes}/projection-matrix)  | 
 Transform done to all particles, if any (can be higher than 2D)
  |
| 
 Vars that apply when a particle spawns
  |
| 
 lifespan
  | 
 num
  | 
 Maximum life of the particle, in ticks
  |
| 
 fade
  | 
 num
  | 
 Fade-out time at end of lifespan, in ticks
  |
| 
 fadein
  | 
 num
  | 
 Fade-in time, in ticks
  |
| 
 icon
  | 
 icon
  | 
 Icon to use, if any; no icon means this particle will be a dot
 
 Can be assigned a weighted list of icon files, to choose an icon at random
  |
| 
 icon\_state
  | 
 text
  | 
 Icon state to use, if any
 
 Can be assigned a weighted list of strings, to choose an icon at random
  |
| 
 color
  | 
 num or color
  | 
 Particle color (not a color matrix); can be a number if a gradient is used
  |
| 
 color\_change
  | 
 num
  | 
 Color change per tick; only applies if gradient is used
  |
| 
 position
  | 
 num
  | 
 x,y,z position, from center in pixels
  |
| 
 velocity
  | 
 num
  | 
 x,y,z velocity, in pixels
  |
| 
 scale
  | 
 vector (2D)
  | 
 Scale applied to icon, if used; defaults to list(1,1)
  |
| 
 grow
  | 
 num
  | 
 Change in scale per tick; defaults to list(0,0)
  |
| 
 rotation
  | 
 num
  | 
 Angle of rotation (clockwise); applies only if using an icon
  |
| 
 spin
  | 
 num
  | 
 Change in rotation per tick
  |
| 
 friction
  | 
 num
  | 
 Amount of velocity to shed (0 to 1) per tick, also applied to acceleration from drift
  |
| 
 Vars that are evalulated every tick
  |
| 
 drift
  | 
 vector
  | 
 Added acceleration every tick; e.g. a circle or sphere generator can be applied to produce snow or ember effects
  |



 The
 
 icon
 
 and
 
 icon\_state
 
 values are special in that they can't be assigned a generator, but they can be assigned a constant icon or string, respectively, or a list of possible values to choose from like so:
 



 icon = list('confetti.dmi'=5, 'coin.dmi'=1)
 

 The list used can either be a simple list, or it can contain weights as shown above.
 



 Changing a var on a particle datum will make changes to future particles.
For instance, you can set the datum's
 
 spawning
 
 var to 0 to make it
stop creating new particles. (Note: If you are changing a vector or color
matrix, such as
 
 gravity
 
 , you need to assign a new value. You can't
for instance set
 
 particles.gravity[2] = 0
 
 because it won't do
anything to update the particle stream.)
 



 The same particle datum can be assigned to more than one movable atom.
However the particles displayed by each atom will be different.
 




---


Pixel movement
----------------




**See also:** 


*Bounding boxes* 

[bound\_x var (movable atom)](#/atom/movable/var/bound_x) 

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

*Speed and position* 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[contents list var (atom)](#/atom/var/contents) 

[fps var (world)](#/world/var/fps) 

*Movement* 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

*Other topics* 

[bounds proc](#/proc/bounds) 

[bounds\_dist proc](#/proc/bounds_dist) 

[Gliding](#/{notes}/gliding) 


























 Pixel movement is a concept that allows atoms to escape the constraints of
BYOND's historically tile-based movement, and move in smaller steps. In the
past this had to be done with soft code, but that was sometimes inconvenient
and it did not perform as well in projects with many objects moving.
 



 The key to understanding pixel movement is to use the bound and step vars.
You use the bound family of vars to define a bounding box for a movable atom,
instead of just making it one full tile in size. The step vars can give it a
movement speed and offset it from the corner of the tile it's standing on.
 


* bound\_x: The left edge of the bounding box
* bound\_y: The bottom edge of the bounding box
* bound\_width: Width of the bounding box
* bound\_height: Height of the bounding box
* step\_size: default movement speed
* step\_x: x offset from the corner of loc
* step\_y: y offset from the corner of loc



 Those are for movable atoms only; they do not apply to turfs.
 



 If
 [world.movement\_mode](#/world/var/movement_mode) 
 is set to
 
 TILED\_MOVEMENT\_MODE
 
 , all movable atoms must be aligned
to the tile grid: their step\_x/y/size values must be multiples of the icon
size, and their bounds must also land on tile boundaries although the atom
can be bigger than one tile. In other movement modes you can specify that
only specific atoms use this behavior, by giving them the
 [TILE\_MOVER](#/atom/var/appearance_flags) 
 appearance
flag.
 


### 
 Bounding boxes



![](data:image/png;charset=utf-8;base64,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)

**Left:** 
 The bounding box (blue) is the only part of the mob that actually collides with anything. By default, it would cover the whole turf (brown). Any turfs covered by the bounding box are in the mob's locs var.
 **Right:** 
 The atom's true position (shaded) is offset from the turf by step\_x and step\_y.
 




 As an example, if your players' mobs have icons that only cover the center
24×24 pixels of a regular 32×32 icon, then you would set the
mobs' bound\_x and bound\_y to 4--because there are 4 pixels unused to the left
and bottom--and bound\_width and bound\_height to 24.
 



 The mob's physical location on the map depends on four things: Its loc,
its step\_x/y values, its bound\_x/y values, and its bound\_width/height. The
lower left corner of the bounding box, relative to the turf the mob is
actually standing on, begins at step\_x+bound\_x on the left and step\_y+bound\_y
on the bottom.
 



 The physical position of the bounding box is
 **not affected** 
 by the
pixel\_x/y/z vars. Those are still strictly visual offsets.
 



 The turfs the mob is covering can be read from the read-only locs var. The
mob will also appear in the contents of those turfs.
 



 Note: This means if an atom is in a turf's contents, its loc is
 *not
necessarily* 
 that turf. The contents list is made to include "overhangers"
from another tile for ease of use.
 


### 
 Movement



 All of the step and walk procs have been upgraded to take an additional
argument, which is the speed at which the atom should move. If that argument
is left out, the atom's own step\_size is used by default. The step\_size
determines how fast the step\_x and step\_y values will change when moving.
 



 Move() has two new arguments that handle the position change gracefully.
These are the step\_x and step\_y values for the target location.
 



 Pixel movement changes the behavior of the Move() proc, because a lot of
things are possible that were not possible when BYOND only supported moving
one tile at a time. For starters, a Move() is either a "slide" or a "jump"
depending on the distance. A slide is when the move can be stopped partway;
a jump is strictly pass/fail. Anything greater than one tile
 *and* 
 the
mover's regular step\_size is considered a jump. Changing z levels is also a
jump, as is moving to/from a non-turf.
 



 If step\_x and step\_y aren't within a good range, the new loc and the
step\_x/y values may be changed so that the southwest corner of the mover's
bounding box is standing on its actual loc, or as close to it as possible.
 



 Enter() and Exit() can be called for several turfs and/or areas, not
just one at a time. It is also possible for them not to be called at all,
if the moving atom moves within a turf but doesn't cross a new turf
boundary. Enter() and Exit() are only called when first attempting to enter
or fully exit. The behavior of these procs depends on
 [world.movement\_mode](#/world/var/movement_mode) 
 ; in
legacy mode, they look at some of the contents of the turfs as well as the
turfs themselves, to preserve behavior found in older BYOND versions.
 



 Cross() and Uncross() are the equivalent of Enter() and Exit() but apply
to objects the mover will either overlap or stop overlapping. (For turfs,
Enter() and Exit() call these procs by default, since the mover is both
stepping
 *into* 
 and
 *onto* 
 a turf.) Likewise Crossed() and
Uncrossed() are the equivalents of Entered() and Exited().
 



 If an atom is sliding, its movement can be halted if it encounters an
obstacle partway along its route. Bump() will still be called for any
obstacles the atom runs into, but Move() will return the number of pixels
moved (the most in any direction). When sliding at a speed so fast that the
distance is bigger than the atom itself, the move will be split up into
several smaller slides to avoid skipping over any obstacles.
 



 Gliding, which is used to show smooth movement between atoms in tile
movement, is mostly not used in pixel movement. It only applies when the
client uses a higher
 [fps](#/client/var/fps) 
 than the
server.
 


### 
 Pixel procs



 The bounds() and obounds() procs have been added to grab a list of atoms
within a given bounding box. That box can be relative to an atom, or in
absolute coordinates.
 



 bounds\_dist() tells the distance between two atoms, in pixels. If it is
positive, that is the minimum distance the atoms would have to traverse to be
touching. At 0, they are touching but not in collision. A negative value
means the two atoms are in collision.
 




---
Projection matrix
-------------------




**See also:** 


[Particle effects](#/{notes}/particles) 

[transform var (atom)](#/atom/var/transform) 

[matrix](#/matrix) 

[Color matrix](#/{notes}/color-matrix) 






 Note: Currently this feature applies only to particle effects, using the
 
 transform
 
 var.
 



 Normally icons in BYOND can only be transformed in 2D, using a simple 3x3
matrix. This is represented by the
 
 /matrix
 
 object, which cuts off the
last column because it isn't used. However particles can have coordinates in x,
y, and z, and the whole particle set can be given a transformation matrix that
handles all three dimensions.
 


### 
 Simple 2D transforms



 The easiest transformation for particles is a simple 2D one, which you can
do by setting the particle datum's
 
 transform
 
 var to a
 
 /matrix
 
 object.
 



```
          a d 0
x y 1  *  b e 0  =  x' y' 1
          c f 1
```


 When an x,y point is multiplied by the matrix, it becomes the new point
x',y'. This is equivalent to:
 



```
x' = a*x + b*y + c
y' = d*x + e*y + f
```


 This is called an
 **affine transform** 
 because all the operations are
"linear" in math terms. (That is, every term in the formula above has a single
variable, not raised to a higher power than 1.)
 


### 
 3x4 matrix (x,y,z with translation)



 3D affine transforms of this type are also affine transformations. There is
no special object for this so a list is used (see below).
 



```
            xx xy xz 0
x y z 1  *  yx yy yz 0  =  x' y' z' 1
            zx zy zz 0
            cx cy cz 1
```


 The way to read the vars above is that the first letter says what input
component is being transformed (x,y,z, or c for "constant"), and the second
letter is the output component.
 



```
x' = xx*x + yx*y + zx*z + cx
y' = xy*x + yy*y + zy*z + cy
z' = xz*x + yz*y + zz*z + cz
```


 To use this kind of matrix, you can cut off the 4th column and provide the
values in a list form, in row-major order:
 



 list(xx,xy,xz, yx,yy,yz, zx,zy,zz, cx,cy,cz)
 

 Note the 4th row is also optional.
 


### 
 4x4 matrix (x,y,z,w with projection)



 This is the most interesting matrix, since if you use all 4 columns you're
actually altering an "axis" called w. This isn't a real axis, but is just a
number that the resulting vector will be divided by.
 



```
            xx xy xz xw
x y z 1  *  yx yy yz yw  =  x'w' y'w' z'w' w'
            zx zy zz zw
            wx wy wz ww

w' = xw*x + yw*y + zw*z + ww
x' = (xx*x + yx*y + zx*z + wx) / w'
y' = (xy*x + yy*y + zy*z + wy) / w'
z' = (xz*x + yz*y + zz*z + wz) / w'
```


 In a regular affine transform, w always stays at 1. In projection you can
think of w as a distance from the "camera". 1 is where objects are their
"normal" size. If you make the z value affect w' by setting zw, you basically
make an object look smaller at higher z values.
 



 This is a simple projection matrix where x,y,z are left untouched, but
there's a projection effect. The "D" value is how far away the "camera" is
from z=0, so a point at z=D looks like it's twice as far away.
 



```
1  0  0  0
0  1  0  0
0  0  1  1/D
0  0  0  1

```


 This 4x4 matrix is handled as a list just like the 3x4 affine matrix:
 



 list(xx,xy,xz,xw, yx,yy,yz,yw, zx,zy,zz,zw, wx,wy,wz,ww)
 


---
Regular expressions
---------------------




**See also:** 


[regex datum](#/regex) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 








 Regular expressions are patterns that can be searched for within a text
string, instead of searching for an exact match to a known piece of text.
They are much more versatile for find and replace operations, and therefore
useful for parsing, filtering, etc.
 



 Some example regular expressions are:


| 
 Pattern
  | 
 Code
  | 
 Meaning
  |
| --- | --- | --- |
| 
 B.\*D
  | 
 regex("B.\*D")
  | 
 Find
 
 B
 
 , followed by any number of characters (including none), followed by a
 
 D
 
 .
  |
| 
 [0-3]
  | 
 regex(@"[0-3]")
  | 
 Find any digit from 0 to 3
  |
| 
 foo|bar
  | 
 regex("foo|bar","i")
  | 
 Find
 
 foo
 
 or
 
 bar
 
 , case-insensitive
  |
| 
 \d+
  | 
 regex(@"\d+","g")
  | 
 Find all sequences of digits
  |



 These are some of the patterns you can use. If you want to use any of the
operators as an actual character, it must be escaped with a backslash.
 



 It is highly recommended that you use
 [raw strings](#/DM/text) 
 like
 `@"..."` 
 for your regular expression patterns, because with a
regular DM string you have to escape all backslash
 `\` 
 and open
bracket
 `[` 
 characters, which will make your regular expression
much harder for you to read. It's easier to write
 `@"[\d]\n"` 
 than
 `"\[\\d]\\n"` 
 .
 




| 
 Pattern
  | 
 Matches
  |
| --- | --- |
| *a* 
 |
 *b*  | *a* 
 or
 *b*  |
| 
 .
  | 
 Any character (except a line break)
  |
| 
 ^
  | 
 Beginning of text; or line if
 
 m
 
 flag is used
  |
| 
 $
  | 
 End of text; or line if
 
 m
 
 flag is used
  |
| 
 \A
  | 
 Beginning of text
  |
| 
 \Z
  | 
 End of text
  |
| 
 [
 *chars* 
 ]
  | 
 Any character between the brackets. Ranges can be specified with a hyphen, like 0-9. Character classes like
 
 \d
 
 and
 
 \s
 
 can also be used (see below).
  |
| 
 [^
 *chars* 
 ]
  | 
 Any character NOT matching the ones between the brackets.
  |
| 
 \b
  | 
 Word break
  |
| 
 \B
  | 
 Word non-break
  |
| 
 (
 *pattern* 
 )
  | 
 Capturing group: the pattern must match, and its contents will be captured in the group list.
  |
| 
 (?:
 *pattern* 
 )
  | 
 Non-capturing group: Match the pattern, but do not capture its contents.
  |
| 
 \1
 *through* 
 \9
  | 
 Backreference;
 
 \
 *N* 

 is whatever was captured in the
 *N* 
 th capturing group.
  |
| 
 Modifiers
  |
| 
 Modifiers are "greedy" by default, looking for the longest match possible. When following a word, they only apply to the last character.
  |
| *a* 
 \*
  | 
 Match
 *a* 
 zero or more times
  |
| *a* 
 +
  | 
 Match
 *a* 
 one or more times
  |
| *a* 
 ?
  | 
 Match
 *a* 
 zero or one time
  |
| *a* 
 {
 *n* 
 }
  | 
 Match
 *a* 
 , exactly
 *n* 
 times
  |
| *a* 
 {
 *n* 
 ,}
  | 
 Match
 *a* 
 ,
 *n* 
 or more times
  |
| *a* 
 {
 *n* 
 ,
 *m* 
 }
  | 
 Match
 *a* 
 ,
 *n* 
 to
 *m* 
 times
  |
| *modifier* 
 ?
  | 
 Make the previous modifier non-greedy (match as little as possible)
  |
| 
 Escape codes and character classes
  |
| 
 \x
 *NN*  | 
 Escape code for a single character, where
 *NN* 
 is its hexadecimal ASCII value
  |
| 
 \u
 *NNNN*  | 
 Escape code for a single 16-bit Unicode character, where
 *NNNN* 
 is its hexadecimal value
  |
| 
 \U
 *NNNNNN*  | 
 Escape code for a single 21-bit Unicode character, where
 *NNNNNN* 
 is its hexadecimal value
  |
| 
 \d
  | 
 Any digit 0 through 9
  |
| 
 \D
  | 
 Any character except a digit or line break
  |
| 
 \l
  | 
 Any letter A through Z, case-insensitive
  |
| 
 \L
  | 
 Any character except a letter or line break
  |
| 
 \w
  | 
 Any identifier character: digits, letters, or underscore
  |
| 
 \W
  | 
 Any character except an identifier character or line break
  |
| 
 \s
  | 
 Any space character
  |
| 
 \S
  | 
 Any character except a space or line break
  |
| 
 Assertions
  |
| 
 (?=
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern to come next, but don't include it in the match
  |
| 
 (?!
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern NOT to come next
  |
| 
 (?<=
 *pattern* 
 )
  | 
 Look-behind: Require this pattern to come before, but don't include it in the match (must be a fixed byte length)
  |
| 
 (?<!
 *pattern* 
 )
  | 
 Look-behind: Require this pattern NOT to come before (must be a fixed byte length)
  |



 The optional flags can be any combination of these:
 




| 
 Flag
  | 
 Meaning
  |
| --- | --- |
| 
 i
  | 
 Case-insensitive matching
  |
| 
 g
  | 
 Global: In Find() subsequent calls will start where this left off, and in Replace() all matches are replaced.
  |
| 
 m
  | 
 Multi-line: ^ and $ refer to the beginning and end of a line, respectively.
  |



 After calling
 
 Find()
 
 on a
 
 /regex
 
 datum, the datum's
 
 group
 
 var will contain a list—if applicable—of any
sub-patterns found with the
 
 ()
 
 parentheses operator. For instance,
searching the string
 
 "123"
 
 for
 
 1(\d)(\d)
 
 will match
 
 "123"
 
 , and the
 
 group
 
 var will be
 
 list("2","3")
 
 .
Groups can also be used in replacement expressions; see the
 [Replace() proc](#/regex/proc/Replace) 
 for more details.
 




---


Understanding the renderer
----------------------------



 .renderlist {position: relative; display: inline-block; margin-left: 3em; text-align: center;}
 .renderlist-label, .renderlist-caption, .renderlist-note {display: block; margin: 3px 0; width: 100%;}
 .renderlist-caption {font-size: 1.1em; font-weight: bold;}
 .renderlist-note {font-size: 0.9em;}
 .renderlist-box {background: #eee; border: 1px solid #333; padding: 3px 10px; margin: 3px 0; border-radius: 10px;}
 body.dark .renderlist-box {color: white; background: #333; border-color: #aaa;}
 .renderlist-box .renderlist-box {background: #ddd; width: 100%;}
 body.dark .renderlist-box .renderlist-box {background: #444; width: 100%;}
 .renderlist-box .renderlist-box .renderlist-box {background: #ccc;}
 body.dark .renderlist-box .renderlist-box .renderlist-box {background: #555;}
 

 To get the most out of BYOND's visual effects, it helps to understand how
the map is displayed.
 



 Every atom has an
 [appearance](#/atom/var/appearance) 
 that holds
all of its visual info (and sometimes a little non-visual info). This
appearance has to be turned into sprites in order to be rendered.
 



 Although many atoms need little more than a simple
 [icon](#/atom/var/icon) 
 and
 [icon\_state](#/atom/var/icon_state) 
 and produce only a
single sprite, some are more complex with overlays, underlays, maptext, etc.
Also there may be
 [image objects](#/image) 
 and
 [visual contents](#/atom/var/vis_contents) 
 involved, although
they're not part of the atom's appearance.
 



 For a simple
 
 icon
 
 and
 
 icon\_state
 
 , just one sprite is
generated. The client looks up the icon it's given. Then it looks up an icon
state, which may be influenced by whether the atom is moving or not since you
can have moving and non-moving icon states. Then it determines which
 [direction](#/atom/var/dir) 
 to draw and which frame of the icon's
animation (if any) to use.
 



 So with several simple icons, and not worrying about layers for now, a list
of sprites lays out like this:
 




 Atom #1
 

 Atom #2
 

 &vellip;
 

 Atom #N
 

### 
 Overlays and underlays



 Now let's consider what happens when an appearance has overlays.
 




 Underlay #1
 

 &vellip;
 

 Underlay #N
 

 Main icon
 

 Overlay #1
 

 &vellip;
 

 Overlay #N
 


 The
 [underlays](#/atom/var/underlays) 
 list is processed
first, then
 [overlays](#/atom/var/overlays) 
 . These lists
contain appearances themselves, rather than actual atoms. This means that
overlays are recursive: an overlay can have overlays itself. To picture how
that works, just replace
one of the overlays above with another list.
 




 Underlay #1
 

 Underlay #2
 

 Main icon
 

 Underlays of overlay #1
 

 Overlay #1 icon
 

 Overlays of overlay #1
 

 Overlay #2
 

### 
 Image objects and visual contents



 Any atom can have an
 [image object](#/image) 
 attached, which can
be shown to only specific players. Most atoms, and image objects, can have
 [visual contents](#/atom/var/vis_contents) 
 that display other atoms
as if they're overlays.
 




 Underlays
 

 Main icon
 

 Overlays
 

 Image objects
 

 Visual contents
 


 As you see this is very similar to overlays. Just like overlays, image
objects and visual contents have appearances of their own (and may also have
their own images or visual contents), so this may be recursive as they add
new overlays, etc.
 



 A couple of things to keep in mind:
 


* If an image object uses the
 [override](#/atom/var/override) 
 var, it will replace the main appearance's icon and overlays, although it
 won't replace other images or visual contents.
* An object in visual contents can use
 [vis\_flags](#/atom/var/vis_flags) 
 to set
 
 VIS\_UNDERLAY
 
 and move itself before the parent's underlays.


### 
 Maptext and particles



 Any appearance may have
 [maptext](#/atom/var/maptext) 
 attached. That maptext draws above the icon but is grouped with it. That
grouping will be discussed further below.
 



 Particle effects also get grouped with the main icon in a similar way to
maptext.
 



 For simplicity, from this point forward the diagram will just treat underlays,
overlays, image objects, and visual contents as overlays.
 





 Main icon
 

 Maptext
 

 Particles
 


 Overlays
 

### 
 Color, transform, and filters



 An appearance's
 [color](#/atom/var/color) 
 and
 [alpha](#/atom/var/alpha) 
 vars (from here forwarded
they'll just be referred to by
 
 color
 
 ) and
 [transform](#/atom/var/transform) 
 are inherited by any
overlays, which also includes images and visual contents. You can avoid that
inheritance by giving those overlays special
 [appearance\_flags](#/var/appearance_flags) 
 :
 
 RESET\_COLOR
 
 ,
 
 RESET\_ALPHA
 
 , and
 
 RESET\_TRANSFORM
 
 .
 



 The appearance's filters are only applied to the main icon.
 





 Main icon
 

 Maptext
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 



 Overlays
 


 color
 
 and
 
 transform
 
 are inherited from Main
   


 filters
 
 are not inherited from Main
 



 When
 
 color
 
 and
 
 transform
 
 are inherited, they "stack". The
inherited color and transform values are applied after those of the overlays.
 


### 

 KEEP\_TOGETHER
 
 and
 
 KEEP\_APART



 There are times it's desirable for an appearance and all its overlays to be
treated as a single unit so any colors or filters can be applied all at once.
One simple example is if the appearance has an
 
 alpha
 
 of 128 to make it
translucent, you probably want to draw the whole atom faded instead of drawing
each sprite faded, one on top of the other.
 



 By using the
 
 KEEP\_TOGETHER
 
 value in
 [appearance\_flags](#/var/appearance_flags) 
 (called KT for
short), an appearance will group all of its underlays and overlays together.
If this is an atom with image objects and visual contents, those will be
grouped with it as well.
 





 KT group
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 


 Main icon
 

 Maptext
 


 Overlays
 



 With
 
 KEEP\_TOGETHER
 
 all of these sprites are rendered to a
temporary drawing surface, and then the main appearance's
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 are all applied to the combined
drawing. This comes with a trade-off, since you can no longer use flags
such as
 
 RESET\_COLOR
 
 to opt out of inheritance.
 



 If an overlay doesn't want to be part of a KT group, it can use the
 
 KEEP\_APART
 
 flag (KA for short). If there are multiple nested
KT groups, KA will only escape the innermost group.
 



 If an overlay inside a KT group has a different
 [plane](#/atom/var/plane) 
 than the group's owner, it
will be separated as if it defined
 
 KEEP\_APART
 
 , except it can
escape multiple nested groups.
 


### 
 Layers and planes



 Any appearance can have a
 [layer](#/atom/var/layer) 
 or
 [plane](#/atom/var/layer) 
 , and these influence how
it gets sorted. (There's also a concept called a "sub-plane" that's
influenced by whether an atom is a
 [HUD/screen object](#/{notes}/HUD) 
 or special layers like
 [BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 
 .)
 



 If a sprite is created with
 
 FLOAT\_LAYER
 
 (any negative value
counts as a floating layer) its layer has to be resolved, or "unfloated".
The main sprite for an atom can never float; it has to have a real layer.
Its overlays and underlays with floating layers will reorder themselves in
numerical order, then look for the next closest sprites in the rendering
list that has a non-negative layer.
 



 A similar process happens with
 
 FLOAT\_PLANE
 
 . Planes can have
negative values but
 
 FLOAT\_PLANE
 
 and the values close to it are
special. Sprites with floating planes have to resolve those as well.
 



 Once all atoms that will appear on the map are assembled into a rendering
list of sprites, the order in which they're rendered on the map is determined
in this order:
 


1. The
 
 plane
 
 var matters most.
2. Subplane is counted next. E.g., HUD objects render above non-HUD objects.
3. Depending on
 [world.map\_format](#/world/var/map_format) 
 ,
 
 layer
 
 or physical position determine the drawing order from here.
4. After everything else has been checked, the order the sprites were generated in is the final tie-breaker.



 In a typical topdown map,
 
 layer
 
 is basically all that matters
after the plane and subplane are taken into account. There is a legacy
concept called micro-layers that helps break ties between sprites with the
same layer; for instance if an atom is moving it's usually desirable to
draw it above other atoms with the same layer; this applies only to topdown
maps.
 


### 
 Plane masters



 Sometimes it's helpful to group multiple sprites on one plane as if the
plane itself were a KT group. For this,
 [appearance\_flags](#/var/appearance_flags) 
 has a value
called
 
 PLANE\_MASTER
 
 . An object with this flag will act as a "parent"
for everything else on the plane. All other sprites on the plane will be
grouped together and rendered on a temporary drawing surface, and then the
plane master's
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 will
be applied.
 



 A plane master does not, however, get an icon or maptext of its own;
they're simply ignored. It can have overlays added to the group.
 


### 
 Advanced topics



 There are other topics not covered in this article, such as
 [render targets](#/atom/var/render_target) 
 and special map formats.
Any details on how those features impact rendering are discussed in their
own articles.
 




---
Side-view maps
----------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[pixel\_w var (atom)](#/atom/var/pixel_w) 

[pixel\_z var (atom)](#/atom/var/pixel_z) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[Isometric maps](#/{notes}/isometric) 

[Topdown maps](#/{notes}/topdown) 

[HUD](#/{notes}/HUD) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/topdown_layer) 















 The side-view map format is used for 3/4 perspective, where the map is
basically similar to a top-down view but is usually foreshortened. Just like
with isometric projection, tiles that are closer to the bottom of the screen
are considered to be closer to the viewer. This is a form of pseudo-3D in
which the 2D icons used by BYOND can be arranged in a way to give the
appearance of three dimensions.
 



 It is important to remember that this is an illusion of 3D, not real 3D.
 



 The
 
 layer
 
 var behaves much the same way it does in
 
 ISOMETRIC\_MAP
 
 mode.See
 [isometric maps](#/{notes}/isometric) 
 for more information.
 



 When using this mode you may want to use a foreshortened
 
 world.icon\_size
 
 , like a 32x24 format instead of 32x32 for example,
and use taller icons for any vertical structures like walls or buildings. If
you set
 
 world.icon\_size
 
 to use foreshortening, then
 
 pixel\_y
 
 (or
 
 pixel\_x
 
 , depending on the orientation of client.dir) will be
adjusted for you; the same applies to
 
 step\_x
 
 and
 
 step\_y
 
 .
For example, with
 
 world.icon\_size
 
 set to
 
 "64x32"
 
 , the
 *physical* 
 tile—what you would see if you were to look at it
straight down from above— is considered to be 64x64, so you would need
 
 pixel\_y=64
 
 or
 
 step\_y=64
 
 to offset by a whole tile. This
adjustment does not apply to screen objects,
 
 pixel\_w
 
 , or
 
 pixel\_z
 
 .
 




---
Tiled icons
-------------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 







 In BYOND 3.0, any file like a large .bmp would be treated like a regular
icon that had been broken up into several tile-sized icon states. All tiles
then were 32x32 pixels. An image that was 100x100 would therefore take at
least 4x4 tiles to display. The icon was padded to the right and the top with
blank space to become an even multiple of 32x32, and then broken up into
sections. The lower left section was given an icon\_state of
 
 "0,0"
 
 ,
the next to the right was
 
 "1,0"
 
 , and so on, up to the upper right
which was
 
 "3,3"
 
 . Another icon state, a 32x32 thumbnail of the big
image, was also included.
 



 BYOND 4.0 expanded on this concept by allowing icons to be defined that had
individual graphics bigger than 32x32, and it would break each one up into
tiles just like 3.0 did. If an icon had a state called
 
 "open"
 
 then it
might break down into
 
 "open 0,0"
 
 ,
 
 "open 1,0"
 
 , and so on,
while the actual
 
 "open"
 
 state would be a thumbnail image. To show the
whole image, you would have to have a separate atom or overlay for each
individual tile.
 



 In newer versions, breaking big icons into tiles is no longer done by
default. Instead, icons are shown and manipulated in their
 [native size](#/{notes}/big-icons) 
 . To use the old method of breaking
icons into tiles, set
 
 world.map\_format
 
 to
 
 TILED\_ICON\_MAP
 
 .
This is the default for all projects compiled before version 455.
 



 When using tiled icons, there are some important things to note:
 


* You need to use extra atoms or overlays to show any icon bigger than a
 single tile, where each atom/overlay shows an individual tile-sized piece
 of the big icon.
* The icon\_state names of each tile are always the original name followed
 by a space, followed by x,y tile coordinates such as 0,0 or 2,1, so the
 northeast corner of
 
 "flag"
 
 might for instance be
 
 "flag 3,2"
 
 . If the original icon\_state had no name, the space is
 left out and only the x,y coordinates are used.
* Every icon's size is a multiple of world.icon\_size. If an icon of an
 incompatible size is used, it will be padded to the nearest full tile
 size.
* Crop()
 
 and
 
 Scale()
 
 always pad their results to the
 nearest full tile size.
* icon.Insert()
 
 can insert a single-tile icon into a multi-tiled
 big icon using the appropriate icon\_state; e.g., inserting into
 
 "door 0,0"
 
 will replace the southwest corner of the
 
 "door"
 
 state.
* Using the
 
 icon()
 
 proc, you can extract a single tile from a
 multi-tiled big icon.



 This example shows a big icon being applied to an atom in tiled mode, as
overlays:
 


### 
 Example:



 // icon is 3 tiles wide by 2 high
icon\_state = "0,0"

// A temporary object used for the overlays
var/obj/O = new
O.icon = icon
O.layer = FLOAT\_LAYER

for(var/tile\_y=0, tile\_y<2, ++tile\_y)
 for(var/tile\_x=0, tile\_x<3, ++tile\_x)
 if(tile\_x && tile\_y)
 O.pixel\_x = tile\_x \* 32
 O.pixel\_y = tile\_y \* 32
 O.icon\_state = "[tile\_x],[tile\_y]"
 overlays += O
 


---
Topdown maps
--------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 













 By default, BYOND displays all maps in top-down format, so
 
 world.map\_format
 
 is set to
 
 TOPDOWN\_MAP
 
 unless you say
otherwise. This view means players are looking down on the map, and
"north" corresponds to the top of their screen. (This can be changed by
setting
 
 client.dir
 
 .)
 



 A related map\_format, used by older games, is
 
 TILED\_ICON\_MAP
 
 . This
is also topdown but it handles icons differently.
 



 In this form, the
 
 layer
 
 var behaves exactly as you would expect:
Icons with a lower layer are drawn beneath icons with a higher layer. The only
exception is when you use
 [big icons](#/{notes}/big-icons) 
 , which will
be drawn above any other icons on the same layer. Also an atom's underlays will
be drawn behind it unless their layer is changed, and its overlays will draw in
front of it unless otherwise stated.
 



 Topdown mode also guarantees that
 
 world.view
 
 or
 
 client.view
 
 will set the exact screen size used by the HUD, except for HUD objects that
appear outside of the normal bounds.
 



 Screen objects (also called the HUD) cannot be intermixed with topdown
icons. They will appear on top of other icons, unless using a lower plane or a
special layer like
 
 BACKGROUND\_LAYER
 
 .
 




---
TOPDOWN\_LAYER
----------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







 TOPDOWN\_LAYER is a special high value that can be added to the regular layer
of any atom. This is only available when using a non-topdown world.map\_format,
such as isometric mapping.
 



 The purpose of this value is to make an atom appear as if it belongs in a
top-down map, when using a map\_format other than TOPDOWN\_MAP or TILED\_ICON\_MAP.
This can be handy for title screens, or for special battle maps or the inside
of a building in an RPG.
 



 When using this special layer, it should be added to the layer an atom
normally uses. For instance a turf should have a layer of TOPDOWN\_LAYER +
TURF\_LAYER. Usually you will want one part of the map to have TOPDOWN\_LAYER,
and for players to be unable to walk to there from the regular map. Mixing
topdown icons and icons in the normal map\_format in view of each other could
look very strange. For safety's sake, the easiest thing to do is to keep them
on separate z layers.
 



 This can be mixed with EFFECTS\_LAYER. Anything in TOPDOWN\_LAYER will
display on top of EFFECTS\_LAYER, and TOPDOWN\_LAYER + EFFECTS\_LAYER will be
above both.
 



 This can also be mixed with BACKGROUND\_LAYER, which takes priority over
everything else.
 



 Images or overlays with FLOAT\_LAYER can be left alone. They will
automatically have the same layer as whatever atom they are attached to.
 




---
Unicode
---------




**See also:** 


[text](#/DM/text) 



 BYOND was originally written to handle 8-bit ("ANSI") characters only.
However as time has marched on, Unicode has become ubiquitous for supporting
multiple languages, special characters, and emojis. To adapt to this, BYOND
now supports Unicode.
 



 When ANSI was king, every character was exactly one byte in width, because
the only valid characters were between 1 and 255. (And technically, BYOND
reserved 255 for its own use.) Now, BYOND uses an encoding called UTF-8 to
store characters that can't fit in one byte.
 



 UTF-8 breaks up characters with codes of 128 or higher into multiple
bytes, like so:


| 
 Character code
  | 
 Size in bytes
  |
| --- | --- |
| 
 0 - 0x7F
  | 
 1
  |
| 
 0x80 - 0x7FF
  | 
 2
  |
| 
 0x800 - 0xFFFF
  | 
 3
  |
| 
 0x10000 - 0x10FFFF
  | 
 4
  |


### 
 Text handling



 Importantly, BYOND's text procs are based on the byte position, not the
character position which may be lower. In other words,
 
 length("abcdéfg")
 
 is greater than 7; it's 8, because
 
 é
 
 takes up 2 bytes in UTF-8. That also means
 
 f
 
 is at
position 7, not position 6.
 



 Why do the text procs work with byte position instead of character
position? Because ultimately, it's faster. Going by character position would
require counting every byte in a string (at least when it uses UTF-8) until
the right character position was found. This would be detrimental to
performance in most cases.
 



 For the most part, this distinction should be fairly invisible to you.
Most code isn't going to encounter problems, but if you do a lot of text
processing you should be aware of it.
 



 In particular,
 [text2ascii()](#/proc/text2ascii) 
 returns the Unicode value at a specific position, which may cover several
bytes. If you loop through a string calling this proc for each character,
you'll have to make adjustments for cases when multiple bytes have been
read.
 



 The read-only
 
 []
 
 index operator also uses byte positions.
 



 If you read a byte or cut text at an inappropriate point, any broken
characters resulting from the cut will be turned into the Unicode
replacement character � which is 0xFFFD.
 


### 

 \_char
 
 procs



 Most of the text handling procs have slower
 
 \_char
 
 versions (e.g.,
 
 copytext\_char
 
 ) that use character positions instead of byte
positions.
 



 These should be used sparingly if at all; whenever it's possible to use
byte positions, you should. When you do use a
 
 \_char
 
 version of a
proc, prefer using
 
 -offset
 
 instead of
 
 length\_char(text)-offset
 
 for positions near the end of the string.
Most text procs allow negative position values that count backwards from the
end, and counting a small number of characters backward is faster than
counting a lot of characters going forward.
 


### 
 Old code



 Code written in ANSI will be up-converted to UTF-8 by Dream Maker, based on
your current locale when the code is loaded.
 




---


User interface skins
----------------------




**See also:** 


[winset proc](#/proc/winset) 

[winget proc](#/proc/winget) 

[output proc](#/proc/output) 

[winclone proc](#/proc/winclone) 

[winexists proc](#/proc/winexists) 

[winshow proc](#/proc/winshow) 

[controls](#/{skin}/control) 

[parameters](#/{skin}/param) 

[macros (skin)](#/{skin}/macros) 

[commands](#/{skin}/commands) 












 BYOND games used to have very limited interface options, all effectively
sharing the same layout. In BYOND 4.0, skins were introduced, allowing
developers more control over the layout.
 



 A skin consists of
 [macro sets](#/{skin}/macros) 
 for
keyboard/gamepad input, menus, and windows and/or panes. All of these are
considered
 [controls](#/{skin}/control) 
 that a game can interact with
via
 [winset()](#/proc/winset) 
 ,
 [winget()](#/proc/winget) 
 ,
 [output()](#/proc/output) 
 , and a few other procs.
 



 About the simplest possible skin is a single window with a single
 [map control](#/{skin}/control/map) 
 , and a single macro set.
 




---
client commands
-----------------



 Several commands can be executed on the client that are not verbs, but raw instructions for Dream Seeker.
 




 .winset "
 *[control.param=value;...]* 
 "
 

 Sets parameters in response to a menu or button command (or a manually typed command). You can set more than one by separating them with semicolons. This command has a more complex format for conditional instructions (see below).
 

 .output
 *control* 
*text* 


 Sends output to a control. The text does not need quotes, but backslashes, newlines, and tabs should be escaped with a backslash. This works similarly to the
 [output()](#/proc/output) 
 proc.
 

 .options
 

 Shows the Options & Messages box.
 

 .reboot
 

 Reboots the world, when Dream Seeker is also acting as a server.
 

 .reconnect
 

 Reconnects to the same world.
 

 .host
 

 Opens hosting options box, when Dream Seeker is also acting as a server.
 

 .profile
 

 Opens the profiler. On a remote connection you may not have access to profile server procs, but you can look at the client and network profilers.
 

 .screenshot
 

 Saves a screenshot of the map. If there's more than one map control, the default map is used.
 

 .screenshot auto
 

 Saves a screenshot of the map, but does not prompt for a filename. The file will be saved in the client's user directory in BYOND/screenshots.
 

 .gamepad-mapping
 

 Opens the gamepad mapping dialog. Helpful if the user's gamepad is not supported or not configured to their liking.
 

 .command
 

 Prompts the user to enter a command, which can be one of these commands as well.
 

 .configure
 *option* 
*value* 


 Toggle certain Dream Seeker config options, such as
 
 .configure graphics-hwmode on
 
 . The only supported options you can use are
 
 graphics-hwmode
 
 ,
 
 sound
 
 , and
 
 delay
 
 which is an old mechanism for dynamically adapting to network delay. (Usually the
 
 delay
 
 is reset to 0.)
 

 .quit
 

 Closes Dream Seeker.
 

### 
 Conditional Winset



 The
 
 .winset
 
 command allows you to use conditional expressions,
like so:
 



```
condition ? choice1 : choice2
```


 The condition is the same as any other parameter you might use in
 
 .winset
 
 , but instead of setting the parameter, it checks to see if
it's true. If so, then the parameters in
 
 choice1
 
 will be set.
Otherwise, the parameters in
 
 choice2
 
 are set. This example makes the
window background red if bigbutton is checked.
 



```
.winset "bigbutton.is-checked=true ? window.background-color=#ff0000 : window.background-color=none"
```


 If you want to look for values that don't match instead of values that do,
use
 
 !=
 
 instead of
 
 =
 
 in the condition.
 



```
.winset "bigbutton.is-checked!=false ? window.background-color=#f00 : window.background-color=none"
```


 The
 
 choice2
 
 item is optional.
 



```
.winset "bigbutton.is-checked=true ? window.background-color=#f00"
```


 Because it's often useful to do more than one thing at a time,
 
 choice1
 
 and
 
 choice2
 
 don't have to be just one parameter. You
can use multiple parameters, but they are separated with a space instead of a
semicolon. (A semicolon indicates the conditional expression is over.)
 



```
.winset "bigbutton.is-checked=true ? window.text-color=#fff window.background-color=#f00 : window.text-color=none window.background-color=none"
```

### 
 Embedded Winget



 Commands that are initiated by the skin (like button.command, map.on-show,
etc.) have a special syntax that allows you to include information that would
normally require a winget call. By including
 
 [[
 *something* 
 ]]
 
 in
the command, the double-bracketed text will be replaced by the result of
running a winget on that parameter.
 



 A value of
 
 [[id.parameter]]
 
 will run a winget on the control with
the given ID. Just using
 
 [[parameter]]
 
 will run a winget for the
control that initiated this command. You can also use
 
 parent
 
 in place
of the ID to do something with the parent of the control, or
 
 parent.id
 
 for access to a sibling control. Position and size parameters can be further
broken down by appending
 
 .x
 
 or
 
 .y
 
 to get at the numbers
directly.
 



 Several commands already support some special cases like
 
 [[\*]]
 
 or
 
 [[width]]
 
 or such, where the special-case values are relevant to the
command. An example is that in
 
 on-size
 
 the value of
 
 [[\*]]
 
 is
a size value. The Any macro, gamepad macros, and mouse macros, also support this
syntax; see
 [macros](#/{skin}/macros) 
 for more info.
 



 You can choose how embedded wingets get formatted by following the value with
 
 as
 
 and a type, such as
 
 [[window.size as string]]
 
 . There are
several types you can use, and different types of parameters get formatted differently:
 




 arg
 

 Value is formatted as if it's an argument on a command line. Numbers are left alone; booleans are 0 or 1; size and position have their X and Y values separated by a space; pretty much everything else is DM-escaped and enclosed in quotes.
 

 escaped
 

 DM-escape the value as if it's in a quoted string but do not include the quotes. Size and position values both use
 
 ,
 
 to separate their X and Y values.
 

 string
 

 Value is formatted as a DM-escaped string with surrounding quotes.
 

 params
 

 Format value for a URL-encoded parameter list (see
 [list2params](#/proc/list2params) 
 ), escaping characters as needed.
 

 json
 

 JSON formatting. Numbers are left unchanged; size or position values are turned into objects with x and y items; boolean values are
 
 true
 
 or
 
 false
 
 .
 

 json-dm
 

 JSON formatting, but DM-escaped so it can be included in a quoted string. Quotes are not included.
 


 The
 
 arg
 
 type is the default, unless the
 
 [[
 
*...* 

 ]]
 
 expression has double quotes on both sides, in which case
 
 escaped
 
 is the
default.
 




---
controls (skin)
-----------------




**Control types:** 


[Bar](#/{skin}/control/bar) 
 : A progress bar or slider
 
[Browser](#/{skin}/control/browser) 
 : A browser
 
[Button](#/{skin}/control/button) 
 : A pushbutton or toggle button
 
[Child](#/{skin}/control/child) 
 : A container holding one or two panes, with a movable splitter
 
[Grid](#/{skin}/control/grid) 
 : For table-like or list-like output
 
[Info](#/{skin}/control/info) 
 : Classic BYOND statpanel
 
[Input](#/{skin}/control/input) 
 : Command input or other user-entered text
 
[Label](#/{skin}/control/label) 
 : Non-interactive text label
 
[Main](#/{skin}/control/main) 
 : A window or pane that holds other controls
 
[Macro](#/{skin}/control/macro) 
 : A
 [keyboard/gamepad/mouse macro](#/{skin}/macros) 

[Map](#/{skin}/control/map) 
 : The game map display
 
[Menu](#/{skin}/control/menu) 
 : An item in a drop-down menu
 
[Output](#/{skin}/control/output) 
 : Text output
 
[Tab](#/{skin}/control/tab) 
 : A tab control holding multiple panes, showing one at a time
 
















**Parameters common to all controls:** 


[id](#/{skin}/param/id) 

[is-disabled](#/{skin}/param/is-disabled) 

[parent](#/{skin}/param/parent) 

[saved-params](#/{skin}/param/saved-params) 

[type](#/{skin}/param/type) 






**Positionable controls only (not Macro or Menu):** 


[anchor1, anchor2](#/{skin}/param/anchor) 

[background-color](#/{skin}/param/background-color) 

[border](#/{skin}/param/border) 

[drop-zone](#/{skin}/param/drop-zone) 

[flash](#/{skin}/param/flash) 

[focus](#/{skin}/param/focus) 

[font-family](#/{skin}/param/font-family) 

[font-size](#/{skin}/param/font-size) 

[font-style](#/{skin}/param/font-style) 

[is-visible](#/{skin}/param/is-visible) 

[is-transparent](#/{skin}/param/is-transparent) 

[on-size](#/{skin}/param/on-size) 

[pos](#/{skin}/param/pos) 

[right-click](#/{skin}/param/right-click) 

[size](#/{skin}/param/size) 

[text-color](#/{skin}/param/text-color) 

















### 
 Creating/Destroying at runtime



 Controls can be created or deleted at runtime. (Only controls you created
during runtime may be deleted.) To create a control, call
 [winset()](#/proc/winset) 
 using the
 [id](#/{skin}/param/id) 
 of the new control, and the
parameter list should include
 [type](#/{skin}/param/type) 
 ,
 [parent](#/{skin}/param/parent) 
 , and probably also
 [pos](#/{skin}/param/pos) 
 ,
 [size](#/{skin}/param/size) 
 , and any
 [anchors](#/{skin}/param/anchor) 
 .
 



 To delete the control again, set its
 
 parent
 
 to a blank value.
 



 Menu items and macros work similarly, except they have no positional info.
For those, the
 [name](#/{skin}/param/name) 
 parameter is
important when you create them, and you will either need
 [command](#/{skin}/param/command) 
 or (for macros)
 [map-to](#/{skin}/param/map-to) 
 to do anything with them.
 




---
bar control (skin)
--------------------



 A progress bar or interactive slider. This can be made to use several different orientations. Its
 
 value
 
 can be read or set as a percentage from 0 to 100.
 




**Bar-specific parameters:** 


[angle1, angle2](#/{skin}/param/angle) 

[bar-color](#/{skin}/param/bar-color) 

[dir](#/{skin}/param/dir) 

[is-slider](#/{skin}/param/is-slider) 

[on-change](#/{skin}/param/bar-color) 

[value](#/{skin}/param/value) 

[width](#/{skin}/param/width) 










---
browser control (skin)
------------------------



 A browser panel integrated into the skin.
 




**Browser-specific parameters:** 


[auto-format](#/{skin}/param/auto-format) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 








 Browsers are capable of displaying HTML documents, and can also interact with the skin.
 


### 
 Browsers and popups



 A longstanding behavior of BYOND is the ability to create a new browser window by sending an extra argument to the
 [browse()](#/proc/browse) 
 proc. Since the advent of skins in BYOND 4.0, this behavior was kept. When you create a new browser popup, the window name you specify for the popup is used for the name of a new
 [window control](#/{skin}/control/main) 
 , and within that window there will be a new browser control simply called
 
 browser
 
 .
 



 If you want to interact with the new browser, its full "decorated"
 [id](#/{skin}/param/id) 
 is
 
*windowname* 
 .browser
 
 .
 


### 
 Running JavaScript from DM



 Sending
 [output()](#/proc/output) 
 to a browser will send a document to display there, but if you follow the browser's control name with a colon and a function name, you can call a JavaScript function in the document displayed within that browser.
 


### 
 Example:



 var/list/info = list("name"="fridge", "power"=12)
// send {"name":"fridge","power":12} to a JavaScript function
usr << output(url\_encode(json\_encode(info)), "mybrowser:myJSfunction")
 

 The text that you send as output will be parsed like URL parameters, where mutliple arguments to the function are separated by
 
 &
 
 or
 
 ;
 
 , which is why
 [url\_encode()](#/proc/url_encode) 
 is wrapped around the
 [json\_encode()](#/proc/json_encode) 
 call in this example.
 


### 
 Winset and Winget via JavaScript



 To allow better access to the skin via JavaScript, two new URL formats have been added. If
 
 window.location
 
 is set to these from JavaScript in a browser control, they can be used to interact directly.
 



**Winset URL:** 

 byond://winset?id=
 *[control ID]* 
 &
 *[property]* 
 =
 *[value]* 
 &...
 




 This works like an ordinary
 [winset()](#/proc/winset) 
 call from the server. If
 
 id
 
 is omitted, it's the same as a winset with a null ID. You can also leave the
 
 id
 
 blank if you use "fully decorated" property names such as
 
 mybutton.is-checked
 
 instead of just
 
 is-checked
 
 .
 



 Any text you use other than letters, numbers, hyphens, commas, and periods should be encoded via the
 
 encodeURIComponent()
 
 function in JavaScript.
 



**Winget URL:** 

 byond://winget?callback=
 *[callback function]* 
 &id=
 *[control ID/list]* 
 &property=
 *[property/list]* 





 In this winget, the IDs and properties you want can be separated by commas if you want to retrieve more than one. The winget operation works via a callback function you must define in JavaScript. The callback is given just one argument, a JavaScript object with all of the properties you requested. For example, this URL:
 



```
byond://winget?callback=wgcb&id=button1&property=is-checked,size,background-color
```


 ...might send this to the callback function wgcb:
 



```
{
    "is-checked": true,
    "size": {
        "x": 60,
        "y": 20
    },
    "background-color": {
        "value": "none",
        "isDefault": true,
        "red": 236,
        "green": 233,
        "blue": 216,
        "alpha": 255,
        "css": "#ece9d8"
    }
}

```


 The property names will be in the same format you would expect from
 [winget()](#/proc/winget) 
 , so when you're looking at multiple elements' properties, you'll get the full names in
 
 id.property
 
 format. The values are always sent back in a convenient form for JavaScript to work with; in the case of size, position, and color these will always be objects.
 



 An optional
 
 control
 
 parameter for the winget call can be used if you want to send data to a callback in a different browser control.
 




---
button control (skin)
-----------------------



 A button that can be pressed to run a
 [command](#/{skin}/commands) 
 , or possibly toggled.
 




**Button-specific parameters:** 


[button-type](#/{skin}/param/button-type) 

[command](#/{skin}/param/command) 

[group](#/{skin}/param/group) 

[image](#/{skin}/param/image) 

[is-checked](#/{skin}/param/is-checked) 

[is-flat](#/{skin}/param/is-flat) 

[text](#/{skin}/param/text) 










---
child control (skin)
----------------------



 A container that can hold one or two
 [panes](#/{skin}/control/main) 
 . If it holds two panes, a splitter may appear between them. This control can therefore be used to subdivide a window or pane into smaller units.
 




**Child-specific parameters:** 


[is-vert](#/{skin}/param/is-vert) 

[left, top](#/{skin}/param/left) 

[lock](#/{skin}/param/lock) 

[right, bottom](#/{skin}/param/right) 

[show-splitter](#/{skin}/param/show-splitter) 

[splitter](#/{skin}/param/splitter) 









---
grid control (skin)
---------------------



 A grid that contains multiple cells that can show various kinds of output data.
 




**Grid-specific parameters:** 


[cell-span](#/{skin}/param/cell-span) 

[cells](#/{skin}/param/cells) 

[current-cell](#/{skin}/param/current-cell) 

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 















 Sending output to a grid looks like this:
 


### 
 Example:



 // output to column 3, row 2
winset(usr, "thegrid", "current-cell=3,2")
usr << output("Text", "thegrid")

// or even easier:
usr << output("Text", "thegrid:3,2")

// when is-list is true:
usr << output("5th item", "thegrid:5")
 

 You can output an atom to the grid, which can be clicked, dragged, etc.
However, you should make sure that atom is
 *not* 
 temporary and will
persist until you no longer need it, or else the server may recycle it and
the object in the cell will either disappear or be impossible to interact
with anymore.
 



 There are some limitations to output in grid controls:
 


* Only one character style (font, color, bold, etc.) may appear within a single cell.
* A cell is either a link, or not.
* One image is allowed per cell.
* A cell can hold an object (atom), sent to it via the
 [output()
 
 proc](#/proc/output) 
 , which can be clicked, dragged, etc.; it will not act as a link.
* The same margin is used all around the cell, not different margins for left, right, top, bottom.
* There will always be a 1-pixel space for grid lines, whether they're shown or not.




---
info control (skin)
---------------------



 The classic BYOND statpanel, which contains both stat and verb tabs. This
is technically a 3-column grid with a variable number of rows.
 




**Info-specific parameters:** 


[allow-html](#/{skin}/param/allow-html) 

[highlight-color](#/{skin}/param/highlight-color) 

[multi-line](#/{skin}/param/multi-line) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[on-tab](#/{skin}/param/on-tab) 

[prefix-color](#/{skin}/param/prefix-color) 

[suffix-color](#/{skin}/param/suffix-color) 

[tab-background-color](#/{skin}/param/tab-background-color) 

[tab-font-family, tab-font-size, tab-font-style](#/{skin}/param/tab-font) 

[tab-text-color](#/{skin}/param/tab-text-color) 













 Output to a statpanel is done via the
 [stat()](#/proc/stat) 
 and
 [statpanel()](#/proc/statpanel) 
 procs, during
 [mob/Stat()](#/atom/proc/stat) 
 .
 



 The same limitations that apply to
 [grid](#/{skin}/control/grid) 
 output apply here.
 




---
input control (skin)
----------------------



 A text box into which the user can type. By default this is used for sending
 [commands](#/{skin}/commands) 
 , but it can be used for other purposes as well.
 




**Input-specific parameters:** 


[command](#/{skin}/param/command) 

[is-password](#/{skin}/param/is-password) 

[multi-line](#/{skin}/param/multi-line) 

[no-command](#/{skin}/param/no-command) 

[on-blur](#/{skin}/param/on-blur) 

[on-focus](#/{skin}/param/on-focus) 

[text](#/{skin}/param/text) 









 Note that when in "standard" mode of accepting user commands, built-in verbs like
 
 .click
 
 , or local commands like
 
 .winset
 
 , are not accepted when typed in. This kind of command can still be entered manually through the Client menu of the Options & Messages window.
 




---
label control (skin)
----------------------



 A text label that appears on the skin.
 




**Label-specific parameters:** 


[align](#/{skin}/param/align) 

[allow-html](#/{skin}/param/allow-html) 

[image](#/{skin}/param/image) 

[image-mode](#/{skin}/param/image-mode) 

[keep-aspect](#/{skin}/param/keep-aspect) 

[text](#/{skin}/param/text) 

[text-wrap](#/{skin}/param/text-wrap) 










---
macro control (skin)
----------------------



 A
 [keyboard/gamepad/mouse macro](#/{skin}/macros) 
 , usually designed to run a
 [command](#/{skin}/commands) 
 . The control is a means of interacting with the macro as an object, allowing some of its properties to be changed at runtime.
 




**Macro-specific parameters:** 


[command](#/{skin}/param/command) 

[map-to](#/{skin}/param/map-to) 

[name](#/{skin}/param/name) 






---
main control (skin)
---------------------



 A container for other controls. The Main control takes two forms: a window or a pane.
 



 A window exists independently and can be moved around on the screen. A pane has to be used within another container control such as a
 [Child](#/{skin}/control/child) 
 or
 [Tab control](#/{skin}/control/tab) 
 .
 




**Main-specific parameters:** 


[icon](#/{skin}/param/icon) 

[image](#/{skin}/param/image) 

[image-mode](#/{skin}/param/image-mode) 

[inner-size](#/{skin}/param/inner-size) 

[is-pane](#/{skin}/param/is-pane) 

[keep-aspect](#/{skin}/param/keep-aspect) 

[outer-size](#/{skin}/param/outer-size) 

[title](#/{skin}/param/title) 

[on-status](#/{skin}/param/on-status) 










**Windows only:** 


[alpha](#/{skin}/param/alpha) 

[can-close](#/{skin}/param/can-close) 

[can-minimize](#/{skin}/param/can-minimize) 

[can-resize](#/{skin}/param/can-resize) 

[is-maximized](#/{skin}/param/is-maximized) 

[is-minimized](#/{skin}/param/is-minimized) 

[macro](#/{skin}/param/macro) 

[menu](#/{skin}/param/menu) 

[on-close](#/{skin}/param/on-close) 

[statusbar](#/{skin}/param/statusbar) 

[titlebar](#/{skin}/param/titlebar) 

[transparent-color](#/{skin}/param/transparent-color) 













**Panes only:** 


[can-scroll](#/{skin}/param/can-scroll) 



 The font parameters have no impact on a window's statusbar or titlebar; those are drawn by the operating system.
 




---
map control (skin)
--------------------



 A map that will display icons from the game.
 




**Map-specific parameters:** 


[icon-size](#/{skin}/param/icon-size) 

[letterbox](#/{skin}/param/letterbox) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[style](#/{skin}/param/style) 

[text-mode](#/{skin}/param/text-mode) 

[view-size](#/{skin}/param/view-size) 

[zoom](#/{skin}/param/zoom) 

[zoom-mode](#/{skin}/param/zoom-mode) 












---
menu control (skin)
---------------------



 A menu item, that when activate will run a
 [command](#/{skin}/commands) 
 .
 




**Menu-specific parameters:** 


[can-check](#/{skin}/param/can-check) 

[command](#/{skin}/param/command) 

[group](#/{skin}/param/group) 

[index](#/{skin}/param/index) 

[is-checked](#/{skin}/param/is-checked) 

[name](#/{skin}/param/name) 









---
output control (skin)
-----------------------



 Displays text output.
 




**Output-specific parameters:** 


[enable-http-images](#/{skin}/param/enable-http-images) 

[image](#/{skin}/param/image) 

[legacy-size](#/{skin}/param/legacy-size) 

[link-color](#/{skin}/param/link-color) 

[max-lines](#/{skin}/param/max-lines) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 










---
tab control (skin)
--------------------



 A tab control, where each tab holds a different
 [pane](#/{skin}/control/main) 
 .
 




**Tab-specific parameters:** 


[current-tab](#/{skin}/param/current-tab) 

[multi-line](#/{skin}/param/multi-line) 

[on-tab](#/{skin}/param/on-tab) 

[tabs](#/{skin}/param/tabs) 







---
macros (skin)
---------------



 Macros are used to convert keyboard and gamepad events into actions. There
are two ways this works: A macro can run a command, or in some cases (such as
gamepad controls) it can be used to remap one control to another.
 



 A collection of macros is called a macro set, and the window currently in
use defines which macro set will be used via its
 [macro](#/{skin}/param/macro) 
 parameter.
 



 Macros can be changed at runtime. If a macro does not have an
 [id](#/{skin}/param/id) 
 , you can refer to it by its key
combination (
 [name](#/{skin}/param/name) 
 ). If you have a
macro set named
 
 macro1
 
 and have a
 
 Ctrl+E
 
 macro for instance,
you could use
 [winset()](#/proc/winset) 
 with
 
 "macro1.Ctrl+E"
 
 . See the
 [Macro
control](#/{skin}/control/macro) 
 for information on which parameters you can change with
 
 winset()
 
 .
 



 The
 
 name
 
 of the macro is actually the full key combination as it
would appear in the macro editor, like
 
 CTRL+E
 
 ,
 
 Space+REP
 
 , or
 
 Alt+Shift+F1
 
 . This is not case-specific and it doesn't matter where
you put modifiers like
 
 CTRL+
 
 ,
 
 SHIFT+
 
 , etc.
 


### 
 The Any macro



 Oftentimes it's desirable to keep track of key presses yourself rather than
have a hundred different macros defined. BYOND makes this possible via the
 
 Any
 
 and
 
 Any+UP
 
 macros, which respond to any key or gamepad
button.
 
 UP
 
 is the only allowed modifier for this macro, since other
modifier keys are handled by this same macro.
 



 Typically, you will want to use
 [set
instant=1](#/verb/set/instant) 
 on the verbs that will be tied to the Any macro, so that
keyboard input doesn't queue up and lag behind.
 



 In the
 [command](#/{skin}/param/command) 
 that goes with
this macro,
 
 [[\*]]
 
 will be replaced with the name of the key or gamepad
button that was pressed/released. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 


### 
 Mapping



 The
 [map-to](#/{skin}/param/map-to) 
 parameter is used
by
 **mappings** 
 , which are like macros but are used to convert gamepad
inputs easily and quickly to keyboard inputs. E.g.,
 
 GamepadLeft
 
 can
map to
 
 West
 
 which is the left arrow key. A set of default mappings
will be added automatically at runtime if you don't include any gamepad
mapping in your project.
 


### 
 Gamepads



 BYOND will support up to four gamepads, and breaks up their input into the
following categories:
 


* **Buttons:** 
 Buttons on the controller that are either pressed or not pressed.
* **Directions:** 
 Directions pressed on the D-pad, which act like buttons. Diagonals are also included.
* **D-pad:** 
 The D-pad itself, which can be used to read a
 [dir](#/atom/var/dir) 
 number.
* **Analog:** 
 The analog sticks (BYOND supports left and right).



 See the list of available macros below for information on how to harness
these inputs.
 



 To let a user configure their gamepad, you need to call the client-side
 
 .gamepad-mapping
 
[command](#/{skin}/commands) 
 . Or, if they
have access to the Options & Messages window and Dream Seeker's default
menus, they can reach it from there. However it's a good idea to make this
easy for them to find. Several common gamepads are already known by BYOND.
 



 There is also the
 
 GamepadRaw
 
 macro, which is similar
to
 
 Any
 
 in some ways and will avoid doing any processing (e.g.
checking for dead zones on the analog sticks) so you can handle all input
yourself.
 
 GamepadRaw
 
 does not rely on BYOND's controller
configuration, so it will not, for instance, know that button 0 should be
 
 GamepadFace1
 
 . See below for more information on how to use this
macro.
 


### 
 Mouse macros



 You can add macros (not local player-defined ones) for any of the mouse
input commands, thereby bypassing the normal mouse verbs. This can be helpful
for designing custom setups where you don't want to have to parse the normal
parameter string that provides most of the info, and instead want to provide
data directly to the verb. You will want
 
 set instant=1
 
 on any such
verb.
 



 Mouse macro commands use the
 
 [[...]]
 
 syntax to embed values, just
like
 [embedded wingets](#/{skin}/commands) 
 . These are the values you
can include in a mouse macro:


| 
 Embedded keyword
  | 
 Meaning
  |
| --- | --- |
| 
 action
  | 
 Name of the mouse action (e.g. MouseDown, MouseMove, etc.).
  |
| 
 src
  | 
 Object the mouse is touching, or dragging/dropping.
  |
| 
 loc
  | 
 Turf or statpanel that
 
 src
 
 is over; in a drag-drop you should split this into
 
 src.loc
 
 and
 
 over.loc
 
 .
  |
| 
 button
  | 
 Mouse button used for this action, if any:
 
 left
 
 ,
 
 middle
 
 , or
 
 right
 
 .
  |
| 
 drag
  | 
 Mouse button currently used for dragging.
  |
| 
 buttons
  | 
 Mouse buttons currently down or involved in this action, separated by commas.
  |
| 
 keys
  | 
 Modifier keys currently held (
 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
 
 ), separated by commas.
  |
| 
 over
  | 
 Object the mouse is over in a drag/drop operation.
  |
| 
 id
  | 
 Control ID; in a drag-drop you should split this into
 
 src.id
 
 and
 
 over.id
 
 .
  |
| 
 icon
  | 
 The icon offset (starting from 1,1 at the lower left) where the mouse action occurred.
 \*  |
| 
 tile
  | 
 The tile where the mouse action occurred, if relevant.
 \*  |
| 
 vis
  | 
 Pixel coordinates relative to the icon's position on screen (same as
 
 icon
 
 but without taking transform into account).
 \*  |
| 
 screen\_loc
  | 
 The regular
 
 screen\_loc
 
 cordinate string.
 \*  |
| 
 screen
  | 
 screen\_loc
 
 coordinates but entirely in pixels starting at 0,0 from lower left.
 \*  |
| 
 screen\_tile
  | 
 screen\_loc
 
 coordinates but only the tile number starting at 1,1.
 \*  |
| 
 screen\_offset
  | 
 screen\_loc
 
 coordinates but only the pixel offset from the tile, starting at 0,0.
 \*  |
| 
 delta
  | 
 Wheel changes in a mouse wheel command.
 \*  |
| 
 left
 
 ,
 
 right
 
 ,
 
 middle
  | 
 1 if this button is down or involved in this action, 0 otherwise
  |
| 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
  | 
 1 if this modifier key is held, 0 otherwise
  |
| 
 link
  | 
 1 if the mouse is over a maptext link, 0 otherwise
  |
| \* 
 Coordinate values are comma-separated, but you can follow them with
 
 .x
 
 or
 
 .y
 
 to get the individual X and Y numbers.
  |



 An example mouse macro command might look like this:
 



> 
> 
> ```
> my-mousedown-verb [[src]] [[button]] "keys=[[keys as params]];drag=[[drag as params]]"
> ```
> 
> 



 In the example, the
 
 src
 
 value is a reference such as you would get
with the
 [ref()
 
 proc](#/proc/ref) 
 . It can be used as a verb
argument directly and won't be enclosed by quotes by default. The
 
 button
 
 value is a string and the default formatting will put quotes around it. The
 
 keys
 
 and
 
 drag
 
 values were given the
 
 as params
 
 format
specifier so they would behave as part of a
 [parameter
list](#/proc/list2params) 
 .
 



 In drag/drop actions, you can precede any value with
 
 src
 
 or
 
 over
 
 if there may be different information for the dragged object and
the mouseover object/location. This also applies to things like
 
 keys
 
 ,
which by default will be the currently held keys but you can use
 
 src.keys
 
 to refer to the values from when the drag began.
 


### 
 Available macros



 This is a list of all keys and gamepad events that can be used in macros.
 




| **Macro modifiers** 
 are part of the macro name, and control the conditions in which the macro will fire.
  |
| 
 Modifier
  | 
 Meaning
  |
| 
 SHIFT+
  | 
 This macro only counts if either Shift key is pressed.
  |
| 
 CTRL+
  | 
 This macro only counts if either Ctrl key is pressed.
  |
| 
 ALT+
  | 
 This macro only counts if either Alt key is pressed.
  |
| 
 +REP
  | 
 If a key/button is held down, this macro repeats.
  |
| 
 +UP
  | 
 This macro fires when the key/button is released.
  |
| **Keyboard keys** 
 are the garden-variety macros. (This list is abridged to exclude keys probably no one has.)
  |
| 
 Key
  | 
 Description
  |
| 
 A
 
 -
 
 Z
  | 
 Letter key
  |
| 
 0
 
 -
 
 9
  | 
 Number key
  |
| 
 Numpad0
 
 -
 
 Numpad9
  | 
 Numpad numbers
  |
| 
 North
  | 
 Up arrow
  |
| 
 South
  | 
 Down arrow
  |
| 
 East
  | 
 Right arrow
  |
| 
 West
  | 
 Left arrow
  |
| 
 Northwest
  | 
 Home key
  |
| 
 Southwest
  | 
 End key
  |
| 
 Northeast
  | 
 Page Up key
  |
| 
 Southeast
  | 
 Page Down key
  |
| 
 Center
  | 
 Center key (numpad)
  |
| 
 Return
  | 
 Enter / Return key
  |
| 
 Escape
  | 
 Esc key
  |
| 
 Tab
  | 
 Tab key
  |
| 
 Space
  | 
 Space bar
  |
| 
 Back
  | 
 Backspace key
  |
| 
 Insert
  | 
 Ins key
  |
| 
 Delete
  | 
 Del key
  |
| 
 Pause
  | 
 Pause key
  |
| 
 Snapshot
  | 
 Snapshot / Print Screen key
  |
| 
 LWin
  | 
 Left Windows key
  |
| 
 RWin
  | 
 Right Windows key
  |
| 
 Apps
  | 
 Apps key
  |
| 
 Multiply
  | 
 Multiply key
  |
| 
 Add
  | 
 Add key
  |
| 
 Subtract
  | 
 Subtract key
  |
| 
 Divide
  | 
 Divide / Slash key
  |
| 
 Separator
  | 
 Separator / Backslash key
  |
| 
 Shift
  | 
 Shift key (when not used as a modifier)
  |
| 
 Ctrl
  | 
 Ctrl key (when not used as a modifier)
  |
| 
 Alt
  | 
 Alt key (when not used as a modifier)
  |
| 
 VolumeMute
  | 
 Mute key
  |
| 
 VolumeUp
  | 
 Volume up key
  |
| 
 VolumeDown
  | 
 Volume down key
  |
| 
 MediaPlayPause
  | 
 Play/pause media key
  |
| 
 MediaStop
  | 
 Stop media key
  |
| 
 MediaNext
  | 
 Next track key
  |
| 
 MediaPrev
  | 
 Previous track key
  |
| **Special macros**  |
| 
**Any** 
 | 
 A special macro that can run a command on press/release of any key or gamepad button.
 
 UP
 
 is the only modifier allowed. In the command,
 
 [[\*]]
 
 is replaced with the key/button name.
 \*  |
| 
**GamepadRaw** 

\*  | 
 Captures raw input from a gamepad, without regard to the adjustments done by the Gamepad Setup dialog. In the command,
 
 [[id]]
 
 is replaced by the name of the button or axis changed ("Button0" through "Button15" and "Axis0" through "Axis11"),
 
 [[value]]
 
 is replaced with the value of the button or axis, and
 
 [[\*]]
 
 is equivalent to
 
 [[id]] [[value]]
 
 .
  |
| 
\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.
  |
| **Gamepad buttons** 
† 
 can use another gamepad button as a modifier (but not CTRL, SHIFT, ALT), and can be mapped to one or two keyboard keys or mouse buttons.
  |
| 
 Button
  | 
 Description
  |
| 
 GamepadFace1
  | 
 A (Xbox), X (PS), bottom of diamond
  |
| 
 GamepadFace2
  | 
 B (Xbox), Circle (PS), right of diamond
  |
| 
 GamepadFace3
  | 
 X (Xbox), Square (PS), left of diamond
  |
| 
 GamepadFace4
  | 
 Y (Xbox), Triangle (PS), top of diamond
  |
| 
 GamepadL1
  | 
 Left top shoulder
  |
| 
 GamepadR1
  | 
 Right top shoulder
  |
| 
 GamepadL2
  | 
 Left bottom shoulder
  |
| 
 GamepadR2
  | 
 Right bottom shoulder
  |
| 
 GamepadSelect
  | 
 Select / Back
  |
| 
 GamepadStart
  | 
 Start / Forward
  |
| 
 GamepadL3
  | 
 Left analog click
  |
| 
 GamepadR3
  | 
 Right analog click
  |
| 
 Directional buttons: only one can pressed at a time, and the diagonal buttons are virtual.
  |
| 
 GamepadUp
  | 
 Up button
  |
| 
 GamepadDown
  | 
 Down button
  |
| 
 GamepadLeft
  | 
 Left button
  |
| 
 GamepadRight
  | 
 Right button
  |
| 
 GamepadUpLeft
  | 
 Up+left virtual button
  |
| 
 GamepadUpRight
  | 
 Up+right virtual button
  |
| 
 GamepadDownLeft
  | 
 Down+left virtual button
  |
| 
 GamepadDownRight
  | 
 Down+right virtual button
  |
| **Gamepad analog sticks** 
† 
 can have commands and/or map to
 
 GamepadDir
 
 ,
 
 GamepadDir4
 
 , or
 
 Mouse
 
 . They can use a gamepad button as a modifier. In a command,
 
 [[x]]
 
 and
 
 [[y]]
 
 are replaced by coordinates, and
 
 [[\*]]
 
 is replaced by both with a comma for separation.
  |
| 
 GamepadLeftAnalog
  | 
 Left analog stick
  |
| 
 GamepadRightAnalog
  | 
 Left analog stick
  |
| **Gamepad Dpads** 
†‡ 
 can have commands or are used as mapping targets for analog sticks. A gamepad button can be used as a modifier. In a command,
 
 [[\*]]
 
 is replaced by a direction number, which can be 0.
  |
| 
 GamepadDir
  | 
 Dpad, converted to one of the eight standard directions.
  |
| 
 GamepadDir4
  | 
 Dpad, converted to a cardinal direction.
  |
| 
† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).
 

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.
  |
| **Mouse macros** 
 can have commands but not be used as mapping targets.
  |
| 
 MouseDown
  | 
 Mouse button pressed (replaces MouseDown verb)
  |
| 
 MouseUp
  | 
 Mouse button released (replaces MouseUp verb)
  |
| 
 MouseOver
  | 
 Mouse has moved over a new icon or entered/exited a control (replaces MouseEntered and MouseExited verbs)
  |
| 
 MouseMove
  | 
 Mouse has moved to a new pixel of the same icon (replaces MouseMove verb)
  |
| 
 MouseDrag
  | 
 Mouse has begin dragging or is over a new drop target (replaces MouseDrag verb)
  |
| 
 MouseDragMove
  | 
 Mouse is dragging and is over a new pixel of the same drop target (replaces MouseDrag verb in situations where MouseMove would apply)
  |
| 
 MouseDrop
  | 
 Mouse drag has been released over a target (replaces MouseDrop verb)
  |
| **Mouse targets** 
 can only be used as mapping targets for another macro.
  |
| 
 Mouse
  | 
 The mouse cursor, mappable by a gamepad analog stick.
  |
| 
 MouseLeftButton
  | 
 Left button, mappable by a gamepad button.
  |
| 
 MouseRightButton
  | 
 Right button, mappable by a gamepad button.
  |
| 
 MouseMiddleButton
  | 
 Middle button, mappable by a gamepad button.
  |




---


parameters (skin)
-------------------



 Controls can be interacted with via
 [winset()](#/proc/winset) 
 and
 [winget()](#/proc/winset) 
 to change or read various
parameters.
 



 Parameters come in a few different formats:
 


* Boolean:
 
 true
 
 or
 
 false
* Numeric: any number, sometimes allowing decimal or negative numbers
* String: text
* Position:
 *x* 

 ,
 
*y*
* Size:
 *width* 

 x
 
*height*
* Enumerated: one of several text choices, sometimes accepting numbers or true/false values as shortcuts



 The list of
 [all controls](#/{skin}/control) 
 which shows which
parameters are universal, and each individual control type lists additional
parameters that apply to that type specifically.
 



 Note: In any parameter's "Applies to" section, "all" refers to positionable
controls only, not Macro or Menu controls. Macro and Menu will be listed
separately if supported.
 




---
align parameter (skin)
------------------------




**See also:** 


[allow-html parameter](#/{skin}/param/allow-html) 




**Applies to:** 


[Label](#/{skin}/control/label) 




**Possible values:** 


 center
 
 left
 
 right
 
 top
 
 bottom
 
 top-left
 
 top-right
 
 bottom-left
 
 bottom-right
 











**Default value:** 


 center
 


 Default alignment of text/image, both horizontal and vertical.
 



 A BYOND direction flag like
 
 WEST
 
 may be assigned to this parameter, or 0 for center alignment.
 




---
allow-html parameter (skin)
-----------------------------




**Applies to:** 


[Label](#/{skin}/control/label) 

[Info](#/{skin}/control/info) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 Info control: Allow HTML tags to be used in
 [stat()](#/proc/stat) 
 info. The same limitations apply as to the
 [Grid control](#/{skin}/control/grid) 
 .
 



 Label control: Currently, the label control will not actually use the HTML; it will simply strip it out. Full support may appear in a later version.
 




---
alpha parameter (skin)
------------------------




**See also:** 


[transparent-color parameter](#/{skin}/param/transparent-color) 




**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 number
 



**Default value:** 


 255
 


 Opacity of the window, from 0 (invisible) to 255 (opaque).
 




---
anchor1, anchor2 parameters (skin)
------------------------------------




**See also:** 


[pos parameter](#/{skin}/param/pos) 

[size parameter](#/{skin}/param/size) 





**Applies to:** 


[All](#/{skin}/control) 
 (except
 [Main](#/{skin}/control/main) 
 )
 



**Format:** 


 none
 
*x* 
 ,
 *y* 





**Default value:** 


 none
 


 Anchors the control within the window or pane. If the anchor is not
 
 none
 
 , it is expressed as pecentages of the container's width and height. For example, an anchor of 100,100 means that the X and Y position are tied to the lower right of the container, and 50,0 is tied to the top center.
 



 Setting only
 
 anchor1
 
 will control the position of the control but won't affect its size.
 



 Setting
 
 anchor2
 
 as well will allow you to stretch the control as the container's size changes. You can think of this
 
 anchor1
 
 controlling the top left corner, and
 
 anchor2
 
 the bottom right corner.
 




---
angle1, angle2 parameters (skin)
----------------------------------




**See also:** 


[dir parameter](#/{skin}/param/dir) 

[width parameter](#/{skin}/param/width) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 number
 



**Default value:** 



 angle1
 
 : 0
 

 angle2
 
 : 180
 



 The angle of the bar control's arc when its
 [dir](#/{skin}/param/dir) 
 is
 
 clockwise
 
 or
 
 counterclockwise
 
 . Angles are measured clockwise from due north, so 0 is north, 90 is east, and so on.
 
 angle1
 
 is the beginning of the arc, and
 
 angle2
 
 is the end.
 




---
auto-format parameter (skin)
------------------------------




**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false (was once true in old versions)
 


 When true, the browser control will inject conditional scripting into HTML documents to make them behave nicer in very old browsers. However, it is unlikely there are any systems left that need this.
 




---
background-color parameter (skin)
-----------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[tab-background-color parameter](#/{skin}/param/tab-background-color) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 



 The control's background color. The exact way this applies depends on the control.
 




---
bar-color parameter (skin)
----------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[is-transparent parameter](#/{skin}/param/is-transparent) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 



 The color of the bar or slider.
 




---
border parameter (skin)
-------------------------




**Applies to:** 


[All](#/{skin}/control) 




**Possible values:** 


 none
 
 line
 
 sunken
 





**Default value:** 


 none
 


 Border type around the control or window. May not work the same in all controls.
 




---
button-type parameter (skin)
------------------------------




**See also:** 


[group parameter](#/{skin}/param/group) 

[is-checked parameter](#/{skin}/param/is-checked) 





**Applies to:** 


[Button](#/{skin}/control/button) 




**Possible values:** 


 pushbutton: press once
 
 pushbox: press to toggle
 
 checkbox: press to toggle, and displays a checkmark if checked
 
 radio: press to check, and other buttons with the same
 
 group
 
 will be unchecked
 






**Default value:** 


 pushbutton
 


 Changes the type of button.
 




---
can-check parameter (skin)
----------------------------




**See also:** 


[group parameter](#/{skin}/param/group) 

[is-checked parameter](#/{skin}/param/is-checked) 





**Applies to:** 


[Menu](#/{skin}/control/menu) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 If true, this menu item is toggled like a checkbox or radio button when clicked.
 




---
can-close parameter (skin)
----------------------------




**See also:** 


[on-close parameter](#/{skin}/param/on-close) 

[can-resize parameter](#/{skin}/param/can-resize) 

[titlebar parameter](#/{skin}/param/titlebar) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Allow the window to be closed, and also shows a system menu for the window.
 




---
can-minimize parameter (skin)
-------------------------------




**See also:** 


[can-resize parameter](#/{skin}/param/can-resize) 

[titlebar parameter](#/{skin}/param/titlebar) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Allow the window to be minimized.
 




---
can-resize parameter (skin)
-----------------------------




**See also:** 


[on-size parameter](#/{skin}/param/on-size) 

[can-minimize parameter](#/{skin}/param/can-minimize) 

[titlebar parameter](#/{skin}/param/titlebar) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Allow the window to be resized or maximized.
 




---
can-scroll parameter (skin)
-----------------------------




**See also:** 


[on-size parameter](#/{skin}/param/on-size) 

[size parameter](#/{skin}/param/size) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (pane only)
 



**Possible values:** 


 none
 
 horizontal
 
 vertical
 
 both
 






**Default value:** 


 none
 


 Allow this pane to retain its horizontal and/or vertical size and show scrollbars if necessary, instead of shrinking to fit the container.
 




---
command parameter (skin)
--------------------------




**See also:** 


[Commands](#/{skin}/commands) 




**Applies to:** 


[Button](#/{skin}/control/button) 

[Input](#/{skin}/control/input) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 







**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is activated.
 



 For the Input control, whatever the user types in follows this command. If your command starts with an exclamation point
 
 !
 
 , everything after the
 
 !
 
 is shown as a default prompt that may be cleared by the user.
 




---
cell-span parameter (skin)
----------------------------




**See also:** 


[cells parameter](#/{skin}/param/cells) 




**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


*columns* 
 ,
 *rows* 




**Default value:** 


 1x1
 


 The span of the current grid cell; it can be merged with cells to the right and down. If
 
 is-list
 
 is true, this setting is ignored. This setting is only available at runtime.
 




---
cells parameter (skin)
------------------------




**See also:** 


[cell-span parameter](#/{skin}/param/cell-span) 

[current-cell parameter](#/{skin}/param/current-cell) 

[is-list parameter](#/{skin}/param/is-list) 






**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


*columns* 
 ,
 *rows* 

*items* 





**Default value:** 


 0x0
 


 The number of columns and rows in the grid. Using -1 for either columns or rows will leave that value unchanged.
 



 If
 [is-list](#/{skin}/param/is-list) 
 is true, this value can be set to a single number.
 




---
current-cell parameter (skin)
-------------------------------




**See also:** 


[cell-span parameter](#/{skin}/param/cell-span) 

[cells parameter](#/{skin}/param/cells) 

[is-list parameter](#/{skin}/param/is-list) 






**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


*columns* 
 ,
 *rows* 

*items* 





**Default value:** 


 0x0
 


 The active cell. Any output sent to the grid, that is not sent to a specific cell, will go into this cell.
 



 If
 [is-list](#/{skin}/param/is-list) 
 is true, this value can be set to a single number.
 




---
current-tab parameter (skin)
------------------------------




**See also:** 


[on-tab parameter](#/{skin}/param/on-tab) 

[tabs parameter](#/{skin}/param/tabs) 





**Applies to:** 


[Tab](#/{skin}/control/tab) 




**Format:** 


 string
 


 The name of the
 [pane](#/{skin}/control/main) 
 in the active/default tab. If set to a pane that is not currently in this tab control, the pane by that name will be added as another tab.
 




---
dir parameter (skin)
----------------------




**See also:** 


[value parameter](#/{skin}/param/angle) 

[angle1, angle2 parameters](#/{skin}/param/angle) 

[width parameter](#/{skin}/param/width) 






**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Possible values:** 


 north
 
 south
 
 east
 
 west
 
 clockwise
 
 counterclockwise
 








**Default value:** 


 east
 


 The direction/orientation of the bar. As the
 [value](#/{skin}/param/value) 
 increases the bar will move further in this direction.
 



 Shorthand values like
 
 cw
 
 and
 
 ccw
 
 can be used, or also numerical BYOND directions.
 




---
drop-zone parameter (skin)
----------------------------




**See also:** 


[mouse handling](#/DM/mouse) 




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 



 true
 
 for
 [Grid](#/{skin}/control/grid) 
 ,
 [Info](#/{skin}/control/info) 
 ,
 [Map](#/{skin}/control/map) 


 false
 
 for everything else
 



 True if dragged objects may be dropped here. Default is true for Map, Info, and Grid controls, false for others. When in use, this will be the value of the
 
 over\_control
 
 argument in
 [MouseDrop()](#/client/proc/MouseDrop) 
 if you drop an atom here.
 



 Grids can also add
 
 drag-cell
 
 and
 
 drop-cell
 
 to mouse proc parameters. The mouse procs'
 
 src\_location
 
 and
 
 over\_location
 
 arguments are in the form
 
 "[column],[row]"
 
 (or
 
 "[item"]
 
 if
 [is-list](#/{skin}/param/is-list) 
 is true) when dragging to/from a grid cell.
 



 In Info controls,
 
 src\_location
 
 and
 
 over\_location
 
 in mouse procs will be the name of the statpanel tab.
 




---
enable-http-images parameter (skin)
-------------------------------------




**See also:** 


[small-icons parameter](#/{skin}/param/small-icons) 

[style parameter](#/{skin}/param/style) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Output](#/{skin}/control/output) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 Allows images to be pulled from the Web when using the
 
 <img>
 
 tag; otherwise only locally stored images can be shown.
 




---
flash parameter (skin)
------------------------




**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 number
 



**Default value:** 


 0
 


 Set to a positive number to make the window flash that many times, -1 to flash forever, and 0 to stop flashing.
 




---
focus parameter (skin)
------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[winget proc](#/proc/winget) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 This parameter is true if this control currently has focus.
 



 This is also a special read-only global parameter. Calling
 [winget()](#/proc/winget) 
 with no
 
 id
 
 and
 
 focus
 
 as the parameter will return the
 [id](#/{skin}/param/id) 
 of the currently focused control, if any.
 




---
font-family parameter (skin)
------------------------------




**See also:** 


[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 


 Leave blank to use the default font. This can be used for CSS-style fallback fonts, e.g. "Arial,Helvetica".
 



 You can include fonts in your resource file, making them available to the client, like so:
 



 var/list/extra\_resources = list(\
 'myfont.ttf',
 'myfont\_bold.ttf')
 


---
font-size parameter (skin)
----------------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-style parameter](#/{skin}/param/font-style) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 number
 



**Default value:** 


 0
 


 Point size of the font, or leave at 0 for the default size.
 



 The
 [Output control](#/{skin}/control/output) 
 behaves differently for legacy reasons, unless
 [legacy-size](#/{skin}/param/legacy-size) 
 is false.
 




---
font-style parameter (skin)
-----------------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[All](#/{skin}/control) 




**Possible values:** 


 bold
 
 italic
 
 underline
 
 strike
 






**Default value:** 


*empty* 



 Sets the font style. Any combination of the above values may be used, or none of them. Multiple values may be separated by spaces or commas.
 




---
group parameter (skin)
------------------------




**See also:** 


[button-type parameter](#/{skin}/param/button-type) 

[can-check parameter](#/{skin}/param/can-check) 

[is-checked parameter](#/{skin}/param/is-checked) 






**Applies to:** 


[Button](#/{skin}/control/button) 

[Menu](#/{skin}/control/menu) 





**Format:** 


 string
 


 Used for "radio" buttons and menu items, where only one of them in the same group may be checked at a time. This value is a text string, or may be left empty.
 



 Buttons in different windows/panes, or menu items in another menu/submenu, are always treated as a different group.
 




---
highlight-color parameter (skin)
----------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[background-color parameter](#/{skin}/param/background-color) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Info](#/{skin}/control/info) 





**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #00ff00
 


 The color used to highlight moused-over statpanel items or verbs. In grids, this color is used when hovering over objects or links.
 




---
icon parameter (skin)
-----------------------




**See also:** 


[title parameter](#/{skin}/param/title) 

[titlebar parameter](#/{skin}/param/titlebar) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 '
 *file* 
 '
 



**Default value:** 


*empty* 



 Custom icon used for the window. If no icon is specified, the Dream Seeker icon is used by windows by default.
 



 If this control is a pane, its icon will appear on the tab if the pane is inside a tab control. Lack of an icon will mean no icon appears in the tab.
 



 Note: The Windows
 
 .ico
 
 format is not used. Only image formats BYOND can already use are supported.
 




---
icon-size parameter (skin)
----------------------------




**See also:** 


[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 





**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 number
 



**Default value:** 


 0
 


 Size, in pixels, of icons on the map. A size of 0 stretches to fit available space.
 



 This parameter has been deprecated. Use
 [zoom](#/{skin}/param/zoom) 
 instead.
 




---
id parameter (skin)
---------------------




**See also:** 


[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 


 The name of this control. Read-only.
 



 If this is a
 [Main control](#/{skin}/control/main) 
 , the name should always be unique. For others, it is usually still a good idea to use a unique name, but they can be referenced by
 *window* 
 .
 *id* 
 at runtime.
 



 You can use a colon in front of the
 [type](#/{skin}/param/type) 
 to refer to the default control of a certain type, if one exists, e.g.
 
 :map
 
 is the default map.
 




---
image parameter (skin)
------------------------




**See also:** 


[image-mode parameter](#/{skin}/param/image-mode) 

[keep-aspect parameter](#/{skin}/param/keep-aspect) 





**Applies to:** 


[Button](#/{skin}/control/button) 

[Label](#/{skin}/control/label) 

[Main](#/{skin}/control/main) 

[Output](#/{skin}/control/output) 







**Format:** 


 '
 *file* 
 '
 


 A background image to show in this control.
 



 In the Output control this image is always tiled.
 



 Note: Icons displayed in the output control will not show the background image underneath their transparent parts, but will instead show the background color.
 



 For Label and Main, use
 [image-mode](#/{skin}/param/image-mode) 
 to control how the image is displayed.
 




---
image-mode parameter (skin)
-----------------------------




**See also:** 


[image parameter](#/{skin}/param/image) 

[keep-aspect parameter](#/{skin}/param/keep-aspect) 





**Applies to:** 


[Label](#/{skin}/control/label) 

[Main](#/{skin}/control/main) 





**Possible values:** 


 center
 
 stretch
 
 tile
 





**Default value:** 


 center
 


 Determines how the background image is displayed.
 




---
index parameter (skin)
------------------------




**Applies to:** 


[Menu](#/{skin}/control/menu) 




**Format:** 


 number
 



**Default value:** 


 1000
 


 Moves the menu item to the
 *N* 
 th position among its siblings. 0 or less is no change. Write-only.
 




---
inner-size parameter (skin)
-----------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 

[outer-size parameter](#/{skin}/param/outer-size) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


*width* 
 x
 *height* 



 Read-only.
 



 If the control is a window, this refers to its current interior size: i.e., not counting titlebar, statusbar, borders, etc. If it's maximized, this will be the true size of the window interior, as opposed to
 
 size
 
 which is the interior size once this window is no longer maximized.
 



 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true, this is the size of the display area not including the scrollbars.
 




---
is-checked parameter (skin)
-----------------------------




**See also:** 


[button-type parameter](#/{skin}/param/button-type) 

[can-check parameter](#/{skin}/param/can-check) 

[group parameter](#/{skin}/param/group) 






**Applies to:** 


[Button](#/{skin}/control/button) 

[Menu](#/{skin}/control/menu) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if the button or menu item is checked. Menu items can set this even if
 [can-check](#/{skin}/param/can-check) 
 is false.
 




---
is-default parameter (skin)
-----------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Specifies that this is a default control. This should be true for your main window, and for your primary map, info, output, input, and browser controls.
 



 The default control of a given type can be referenced in
 [winset()](#/proc/winset) 
 and other skin-related procs by the name
 
 ":
 *type* 
 "
 
 , e.g.
 
 ":map"
 
 .
 



 Changing this value at runtime should be avoided, especially for windows. Results may be unpredictable.
 




---
is-disabled parameter (skin)
------------------------------




**See also:** 


[is-checked parameter](#/{skin}/param/is-checked) 

[is-visible parameter](#/{skin}/param/is-visible) 





**Applies to:** 


[All](#/{skin}/control) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 






**Format:** 


 true/false
 



**Default value:** 


 false
 


 Disables the control, menu item, or macro.
 




---
is-flat parameter (skin)
--------------------------




**See also:** 


[button-type parameter](#/{skin}/param/button-type) 




**Applies to:** 


[Button](#/{skin}/control/button) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Gives this button a flat appearance instead of pseudo-3D highlights.
 




---
is-list parameter (skin)
--------------------------




**See also:** 


[cells parameter](#/{skin}/param/cells) 

[current-cell parameter](#/{skin}/param/current-cell) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if the grid is used for a flexible list of items; the number of columns and rows may change to fit them.
 




---
is-maximized parameter (skin)
-------------------------------




**See also:** 


[can-resize parameter](#/{skin}/param/can-resize) 

[is-minimized parameter](#/{skin}/param/is-minimized) 

[size parameter](#/{skin}/param/size) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 false
 


 Maximize the window.
 




---
is-minimized parameter (skin)
-------------------------------




**See also:** 


[can-resize parameter](#/{skin}/param/can-resize) 

[is-maximized parameter](#/{skin}/param/is-maximized) 

[size parameter](#/{skin}/param/size) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 false
 


 Minimize the window.
 




---
is-pane parameter (skin)
--------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[Child control](#/{skin}/control/child) 

[Tab control](#/{skin}/control/tab) 






**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if this is a pane that will be used in other container controls, instead of an independent window. Read-only.
 




---
is-password parameter (skin)
------------------------------




**See also:** 


[command parameter](#/{skin}/param/command) 

[multi-line parameter](#/{skin}/param/multi-line) 

[no-command parameter](#/{skin}/param/no-command) 






**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Hide text with asterisks. Copy to clipboard is not available in this mode, but the
 [text](#/{skin}/param/text) 
 parameter can still read the control's contents.
 



 Note: For obvious reasons, you should never use the same password in a game that you would use anywhere else.
 




---
is-slider parameter (skin)
----------------------------




**See also:** 


[value parameter](#/{skin}/param/value) 




**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Make this an adjustable slider capable of being changed by the user, instead of a progress bar.
 




---
is-transparent parameter (skin)
---------------------------------




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Make this control transparent.
 



 Transparency support is extremely limited. Only some controls can actually use it, and only when on top of certain other controls.
 



 Bars and labels handle transparency reasonably well, when not on top of other controls (or only on top of other conrols of these types).
 




---
is-vert parameter (skin)
--------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 The splitter between the two panes in this control is vertical.
 




---
is-visible parameter (skin)
-----------------------------




**See also:** 


[is-disabled parameter](#/{skin}/param/is-disabled) 




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 True if this control can be seen. The main window should usually be made visible.
 




---
keep-aspect parameter (skin)
------------------------------




**See also:** 


[image parameter](#/{skin}/param/image) 

[image-mode parameter](#/{skin}/param/image-mode) 





**Applies to:** 


[Label](#/{skin}/control/label) 

[Main](#/{skin}/control/main) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 If stretching a background image, preserve its aspect ratio.
 




---
left, top parameters (skin)
-----------------------------




**See also:** 


[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 string
 
 none
 




**Default value:** 


 none
 


 The
 [id](#/{skin}/param/id) 
 of the left/top pane in this control. The parameter names
 
 left
 
 and
 
 top
 
 can be used interchangeably.
 




---
legacy-size parameter (skin)
------------------------------




**See also:** 


[font-size parameter](#/{skin}/param/font-size) 




**Applies to:** 


[Output](#/{skin}/control/output) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 When true, font sizes are scaled slightly larger for readability, which is legacy (and default) BYOND behavior. Set to false for exact font sizing.
 




---
letterbox parameter (skin)
----------------------------




**See also:** 


[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 






**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 If map auto-scales its icons (
 [zoom](#/{skin}/param/zoom) 
 is 0), make sure the entire map fits, and fill excess space with the background color.
 



 If
 
 letterbox
 
 is not enabled, auto-zoom will fill all available space, and any excess will be cut off.
 




---
line-color parameter (skin)
-----------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[show-lines parameter](#/{skin}/param/show-lines) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #c0c0c0
 


 The color of grid lines.
 




---
link-color parameter (skin)
-----------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[visited-color parameter](#/{skin}/param/visited-color) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Output](#/{skin}/control/output) 





**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #0000ff
 


 The color used for links. In some controls
 [visited links](#/{skin}/param/visited-color) 
 may have a different color.
 




---
lock parameter (skin)
-----------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 








**Applies to:** 


[Child](#/{skin}/control/child) 




**Possible values:** 


 left
 
 right
 
 none
 





**Default value:** 


 none
 


 Allows one pane to "lock" the splitter so if this Child control is resized, the splitter will stay put on that side.
 




---
macro parameter (skin)
------------------------




**See also:** 


[Keyboard/gamepad macros](#/{skin}/menu) 

[menu parameter](#/{skin}/param/menu) 

[id parameter](#/{skin}/param/id) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 string
 


 The
 [id](#/{skin}/param/id) 
 of the macro set this window will use, if any, when it's active.
 




---
map-to parameter (skin)
-------------------------




**See also:** 


[macros (skin)](#/{skin}/macros) 

[command parameter](#/{skin}/param/command) 

[id parameter](#/{skin}/param/id) 

[name parameter](#/{skin}/param/name) 







**Applies to:** 


[Macro](#/{skin}/control/macro) 




**Format:** 


 string
 


 The
 [macro name](#/{skin}/macros) 
 (e.g., "SOUTH") of a key combo, Dpad, mouse button, etc. that this macro maps to.
 




---
max-lines parameter (skin)
----------------------------




**Applies to:** 


[Output](#/{skin}/control/output) 




**Format:** 


 number
 



**Default value:** 


 1000
 


 Maximum number of lines before the control drops old text to make room for more. 0 is no limit.
 



 An overflow of 5% is allowed, to reduce flicker.
 




---
menu parameter (skin)
-----------------------




**See also:** 


[macro parameter](#/{skin}/param/macro) 

[id parameter](#/{skin}/param/id) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 string
 


 The
 [id](#/{skin}/param/id) 
 of the menu this window will use, if any, when it's active.
 




---
multi-line parameter (skin)
-----------------------------




**Applies to:** 


[Info](#/{skin}/control/info) 

[Input](#/{skin}/control/input) 

[Tab](#/{skin}/control/tab) 






**Format:** 


 true/false
 



**Default value:** 



 false
 
 : Input control
 

 true
 
 : Info and Tab controls
 



 Input control: Create a multi-line input control. Read-only for this control.
 



 Info and Tab controls: Show tabs in multiple rows if there are too many to fit in a single row.
 




---
name parameter (skin)
-----------------------




**See also:** 


[macros (skin)](#/{skin}/macros) 

[id parameter](#/{skin}/param/id) 





**Applies to:** 


[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 





**Format:** 


 string
 


 Macro control: The key/gamepad combination such as
 
 R+REP
 
 ,
 
 CTRL+Northwest
 
 ,
 
 GamepadLeft
 
 .
 



 Menu control: This is the menu item label. A tab character can be used between the name and a keyboard shortcut, like "Help\tF1". (Keyboard shortcuts must be implemented as macros in order to work. This is just a label.) A blank name shows just a separator.
 




---
no-command parameter (skin)
-----------------------------




**See also:** 


[command parameter](#/{skin}/param/command) 

[is-password parameter](#/{skin}/param/is-password) 

[multi-line parameter](#/{skin}/param/multi-line) 






**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if this input control is for typing only; hitting Enter will not run a command.
 




---
on-blur parameter (skin)
--------------------------




**See also:** 


[focus parameter](#/{skin}/param/focus) 

[on-focus parameter](#/{skin}/param/on-focus) 





**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the control loses focus.
 




---
on-close parameter (skin)
---------------------------




**See also:** 


[can-close parameter](#/{skin}/param/can-close) 

[on-size parameter](#/{skin}/param/on-size) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the window is closed.
 




---
on-change parameter (skin)
----------------------------




**See also:** 


[value parameter](#/{skin}/param/value) 




**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the
 [value](#/{skin}/param/value) 
 of the bar/slider is changed. If you drag the slider around, the command will not run until you let go.
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the control's new
 
 value
 
 . (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




---
on-focus parameter (skin)
---------------------------




**See also:** 


[focus parameter](#/{skin}/param/focus) 

[on-blur parameter](#/{skin}/param/on-blur) 





**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the control gains focus.
 




---
on-hide parameter (skin)
--------------------------




**See also:** 


[on-show parameter](#/{skin}/param/on-show) 




**Applies to:** 


[Browser](#/{skin}/control/browser) 

[Info](#/{skin}/control/info) 

[Map](#/{skin}/control/map) 






**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is hidden by the game. Must be the default control for the game to show/hide it.
 



 Currently not editable in Dream Maker.
 




---
on-show parameter (skin)
--------------------------




**See also:** 


[on-hide parameter](#/{skin}/param/on-hide) 




**Applies to:** 


[Browser](#/{skin}/control/browser) 

[Info](#/{skin}/control/info) 

[Map](#/{skin}/control/map) 






**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is shown by the game. Must be the default control for the game to show/hide it.
 



 Currently not editable in Dream Maker.
 




---
on-size parameter (skin)
--------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is resized. If you are dragging a window edge or splitter, the command won't run until you finish.
 



 No command will be sent in response to size or splitter changes made by
 [winset()](#/proc/winset) 
 .
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the control's new size. Likewise,
 
 [[width]]
 
 will be replaced with the width and
 
 [[height]]
 
 with the height. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




---
on-status parameter (skin)
----------------------------




**See also:** 


[statusbar parameter](#/{skin}/param/statusbar) 




**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the text that would go in the statusbar is changed. This applies even if this control is a pane and not a window, or is a window without a statusbar. It applies to all panes and windows that directly or indirectly contain whatever control generated the statusbar text (e.g., a map).
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the new text. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




 [[from]]
 
 can be used to reference the control (if any) that generated the next text. You can also use expressions like
 
 [[from.type]]
 
 ,
 
 [[from.parent.pos.x]]
 
 , etc.
 




---
on-tab parameter (skin)
-------------------------




**See also:** 


[current-tab parameter](#/{skin}/param/current-tab) 

[tabs parameter](#/{skin}/param/tabs) 





**Applies to:** 


[Info](#/{skin}/control/info) 

[Tab](#/{skin}/control/tab) 





**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the current tab is changed.
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the new tab's
 [id](#/{skin}/param/id) 
 . (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




---
outer-size parameter (skin)
-----------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 

[inner-size parameter](#/{skin}/param/inner-size) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


*width* 
 x
 *height* 



 Read-only.
 



 If the control is a window, this refers to its current exterior size
 *including* 
 titlebar, statusbar, borders, etc.
 



 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true, this is the size of the display area including the scrollbars.
 




---
parent parameter (skin)
-------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[type parameter](#/{skin}/param/type) 

[name parameter](#/{skin}/param/name) 






**Applies to:** 


[All](#/{skin}/control) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 






**Format:** 


 string
 


 The
 [id](#/{skin}/param/id) 
 of this control's parent. Write-only, used when creating a new control at runtime or deleting a control that was created this way.
 




---
pos parameter (skin)
----------------------




**See also:** 


[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[size parameter](#/{skin}/param/size) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


*x* 
 ,
 *y* 

 none
 




**Default value:** 


*x* 
 ,
 *y* 

 none
 



 Position of this control's upper left corner, relative to its container. (Not applicable to panes.)
 




---
prefix-color parameter (skin)
-------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[suffix-color parameter](#/{skin}/param/suffix-color) 





**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 The color used for the prefix/header column of statpanel displays. No color means the default
 [text-color](#/{skin}/param/text-color) 
 will be used.
 



 In BYOND 3.0, this color was red.
 




---
right, bottom parameters (skin)
---------------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 string
 
 none
 




**Default value:** 


 none
 


 The
 [id](#/{skin}/param/id) 
 of the right/bottom pane in this control. The parameter names
 
 top
 
 and
 
 bottom
 
 can be used interchangeably.
 




---
right-click parameter (skin)
------------------------------




**See also:** 


[mouse handling](#/DM/mose) 

[popup\_menu setting (verb)](#/set/popup_menu) 

[drop-zone parameter](#/{skin}/param/drop-zone) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if this control should allow right-clicks to behave like any other click instead of opening up popup menus or similar special behavior.
 




---
saved-params parameter (skin)
-------------------------------




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 



**Default value:** 


*varies* 



 A semicolon-separated list of parameters that get saved with this control. This is often used for things a user might set, like zoom level for a map.
 



 Currently not editable in Dream Maker.
 




---
size parameter (skin)
-----------------------




**See also:** 


[pos parameter](#/{skin}/param/pos) 

[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[on-size parameter](#/{skin}/param/on-size) 

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 








**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


*width* 
 x
 *height* 



 The size of this control.
 



 Setting 0 for width or height uses up any available space right/downward.
 



 If the control is a window, this refers to its
 *interior size when not maximized or minimized* 
 . That is, it does not count borders, titlebar, menu, or statusbar, and if the window is minimized/maximized, this refers to the window's normal size when it is restored. See the
 [inner-size](#/{skin}/param/inner-size) 
 and
 [outer-size](#/{skin}/param/outer-size) 
 params for comparison.
 



 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true,
 
 size
 
 refers to the total scrollable size of the pane, NOT the smaller size displayed. In this case,
 
 outer-size
 
 and
 
 inner-size
 
 refer to the display area with and without scrollbars, respectively.
 




---
show-history parameter (skin)
-------------------------------




**See also:** 


[show-url parameter](#/{skin}/param/show-url) 

[use-title parameter](#/{skin}/param/use-title) 





**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Show forward/back navigation buttons.
 




---
show-lines parameter (skin)
-----------------------------




**See also:** 


[line-color parameter](#/{skin}/param/line-color) 




**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Possible values:** 


 none
 
 horizontal
 
 vertical
 
 both
 






**Default value:** 


 both
 


 Determines which grid lines to display.
 




---
show-names parameter (skin)
-----------------------------




**See also:** 


[name var (atom)](#/atom/var/name) 

[small-icons parameter](#/{skin}/param/small-icons) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 When atoms are output to the grid, show the atom's name next to its icon.
 



 If the atom has no icon and
 
 show-names
 
 is false, the grid cell will be blank.
 




---
show-splitter parameter (skin)
--------------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 Show a splitter if both the left and right (or top and bottom) panes are in use. The splitter can be dragged to resize the panes.
 




---
show-url parameter (skin)
---------------------------




**See also:** 


[show-history parameter](#/{skin}/param/show-history) 

[use-title parameter](#/{skin}/param/use-title) 





**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Shows an address bar for this browser control.
 




---
small-icons parameter (skin)
------------------------------




**See also:** 


[show-names parameter](#/{skin}/param/show-names) 




**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 When output(object,grid) is sent, show smaller icons in this control instead of larger ones.
 




---
splitter parameter (skin)
---------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 number (0 to 100)
 



**Default value:** 


 50
 


 Position of the splitter when two panes are in use, whether
 [show-splitter](#/{skin}/param/show-splitter) 
 is true or not. This value is a percentage. Specifically, it is the percentage of the available width/height that is given to the left/top pane.
 




---
suffix-color parameter (skin)
-------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[prefix-color parameter](#/{skin}/param/prefix-color) 





**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 The color used for the suffix column of statpanel displays. No color means the default
 [text-color](#/{skin}/param/text-color) 
 will be used.
 



 In BYOND 3.0, this color was blue.
 




---
statusbar parameter (skin)
----------------------------




**See also:** 


[titlebar parameter](#/{skin}/param/titlebar) 

[on-status parameter](#/{skin}/param/on-status) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Shows a status bar at the bottom of the window. This will show the name of an atom when you hover over it with the mouse.
 




---
stretch parameter (skin)
--------------------------




**See also:** 


[image parameter](#/{skin}/param/image) 

[image-mode parameter](#/{skin}/param/image-mode) 





**Applies to:** 


[Label](#/{skin}/control/label) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Stretch the background image. Deprecated; use
 [image-mode](#/{skin}/param/image-mode) 
 instead.
 




---
style parameter (skin)
------------------------




**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Map](#/{skin}/control/map) 

[Output](#/{skin}/control/output) 






**Format:** 


 string
 


 Custom stylesheet used for the control. Changes made at runtime will usually not impact any existing text.
 



 For Map controls, this affects any
 [maptext](#/atom/var/maptext) 
 drawn, and changes to the style should appear on the next refresh.
 




---
tab-background-color parameter (skin)
---------------------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[tab-text-color parameter](#/{skin}/param/tab-text-color) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 Affects the background color for tabs. The regular
 [background-color](#/{skin}/param/background-color) 
 is used for the content area.
 




---
tab-font-family, tab-font-size, tab-font-style parameters (skin)
------------------------------------------------------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 

[tab-text-color parameter](#/{skin}/param/tab-text-color) 

[tab-background-color parameter](#/{skin}/param/tab-background-color) 








**Applies to:** 


[Info](#/{skin}/control/info) 



 Affects the font for tabs. The regular versions of these without the
 
 tab-
 
 prefix are used for the content area.
 




---
tab-text-color parameter (skin)
---------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[tab-background-color parameter](#/{skin}/param/tab-background-color) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 Affects the text color for tabs. The regular
 [text-color](#/{skin}/param/text-color) 
 is used for the content area.
 




---
tabs parameter (skin)
-----------------------




**See also:** 


[current-tab parameter](#/{skin}/param/current-tab) 

[id parameter](#/{skin}/param/id) 

[multi-line parameter](#/{skin}/param/multi-line) 






**Applies to:** 


[Tab](#/{skin}/control/tab) 




**Format:** 


 string
 


 A comma-separated list of
 [id](#/{skin}/param/id) 
 values for the panes included as tabs in this control.
 



 When setting this value, you can put
 
 +
 
 in front of the list to add tabs to the existing control, without affecting current tabs. You can likewise use
 
 -
 
 in front of the list to remove tabs.
 



 Note: When using this with
 [winset()](#/proc/winset) 
 , remember you will need to escape
 
 +
 
 as
 
 %2B
 
 via
 [url\_encode()](#/proc/url_encode) 
 or
 [list2params()](#/proc/list2params) 
 .
 




---
text parameter (skin)
-----------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 

[text-wrap parameter](#/{skin}/param/text-wrap) 







**Applies to:** 


[Button](#/{skin}/control/button) 

[Input](#/{skin}/control/input) 

[Label](#/{skin}/control/label) 






**Format:** 


 string
 


 Text shown in this control. For Input controls this setting is only available at runtime.
 




---
text-color parameter (skin)
-----------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 







**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 



 The control's foreground text color.
 




---
text-mode parameter (skin)
----------------------------




**See also:** 


[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 





**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Show text mode even if icons are available. Text mode will be used if no icons are present, regardless of this setting.
 




---
text-wrap parameter (skin)
----------------------------




**See also:** 


[text parameter](#/{skin}/param/text) 




**Applies to:** 


[Label](#/{skin}/control/label) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Wrap text that is too long for the width of the label.
 




---
title parameter (skin)
------------------------




**See also:** 


[name var (world)](#/world/var/name) 

[icon parameter](#/{skin}/param/icon) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 string
 


 The title of this window or pane. For a window, the title will appear in the titlebar if present. For a pane, this will be displayed on the tab if this pane is in a
 [Tab control](#/{skin}/control/tab) 
 .
 



 If this is the default window,
 [world.name](#/world/var/name) 
 takes precedence over the window title.
 




---
titlebar parameter (skin)
---------------------------




**See also:** 


[can-close parameter](#/{skin}/param/can-close) 

[can-minimize parameter](#/{skin}/param/can-minimize) 

[can-resize parameter](#/{skin}/param/can-resize) 

[icon parameter](#/{skin}/param/icon) 

[title parameter](#/{skin}/param/title) 

[use-title parameter](#/{skin}/param/use-title) 

[statusbar parameter](#/{skin}/param/statusbar) 

[name var (world)](#/world/var/name) 











**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Show a titlebar for this window. This is also required for the close, minimize, and maximize buttons to appear.
 




---
transparent-color parameter (skin)
------------------------------------




**See also:** 


[alpha parameter](#/{skin}/param/alpha) 




**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 A color that will be turned into transparency wherever it appears in this window. Overall, this method of transparency comes with many limitations, so it is considered deprecated.
 




---
type parameter (skin)
-----------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[parent parameter](#/{skin}/param/parent) 





**Applies to:** 


[All](#/{skin}/control) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 






**Format:** 


 string
 


 The type of this control. Read-only.
 




---
use-title parameter (skin)
----------------------------




**See also:** 


[show-history parameter](#/{skin}/param/show-history) 

[show-url parameter](#/{skin}/param/show-url) 

[title parameter](#/{skin}/param/title) 

[titlebar parameter](#/{skin}/param/titlebar) 







**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Use the browser's document title to override the title of the window or pane it appears in.
 




---
value parameter (skin)
------------------------




**See also:** 


[is-slider parameter](#/{skin}/param/is-slider) 

[dir parameter](#/{skin}/param/dir) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 number
 



**Default value:** 


 0
 


 The "fullness" of this bar/slider, as a percentage.
 




---
view-size parameter (skin)
----------------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 










**Applies to:** 


[Map](#/{skin}/control/map) 
 (window only)
 



**Format:** 


*width* 
 x
 *height* 



 The size, in pixels, of the map after
 
 zoom
 
 has been applied.
 



 For instance, if the client view has 10×10 tiles (this includes any extended tiles caused by HUD objects) and
 
 world.icon\_size
 
 is 32x32, the map has a native size of 320×320 pixels. If the map has a zoom level of 2, then
 
 view-size
 
 will be 640x640.
 



 With a
 
 zoom
 
 value of 0, which is the default for most projects, the actual zoom level is automatically determined by the size of the map control, the map's native pixel size as explained above, and the value of the
 [letterbox](#/{skin}/param/letterbox) 
 parameter.
 




---
visited-color parameter (skin)
--------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[link-color parameter](#/{skin}/param/link-color) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Output](#/{skin}/control/output) 





**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #0000ff
 


 The color used for visited links.
 




---
width parameter (skin)
------------------------




**See also:** 


[dir parameter](#/{skin}/param/dir) 

[is-slider parameter](#/{skin}/param/is-slider) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 number
 



**Default value:** 


 10
 


 Width, in pixels, of the bar or slider. A value of 0 uses all available width.
 




---
zoom parameter (skin)
-----------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[view-size parameter](#/{skin}/param/view-size) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 






**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 number
 



**Default value:** 


 0
 


 Zoom factor for icons on the map. 1 means to show the icons at their original size, 2 is 200%, 0.5 is 50%, and so on. A value of 0 stretches to fit available space.
 




---
zoom-mode parameter (skin)
----------------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 






**Applies to:** 


[Map](#/{skin}/control/map) 




**Posisble values:** 


 normal
 
 distort
 
 blur
 





**Default value:** 


 normal
 


 Controls the way the map is upscaled.
 




 normal
 


 Preserves a pixelated look, but does some blending between adjacent pixels when the zoom factor is not an integer. This is equivalent to upscaling by the next highest integer, then downscaling.
 

 distort
 

 Uses nearest-neighbor sampling to upscale. This may look odd if the zoom factor is not an integer, since for instance some pixels might scale up to be 2 pixels wide, others 3 pixels wide. Some users prefer it anyway.
 

 blur
 

 Uses bilinear sampling to upscale. This will cause a blurry appearance if the zoom factor is high, but it may be desired in some cases.
 


---
Appendix
----------



 This section contains miscellaneous information that may apply to multiple
vars or procs.
 




[CSS attributes](#/{{appendix}}/css) 

[HTML colors](#/{{appendix}}/html-colors) 

[Color space](#/{{appendix}}/color-space) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







---
CSS attributes
----------------



 DM-CSS is a subset of CSS, and only supports some kinds of selectors and
attributes.
 



 The following table lists all supported attributes, and whether they are
supported in text output, maptext, and in other controls (labels/etc.) Other
controls will often allow only one style for an entire unit of text. A
checkbox in "Other" only indicates that
 *some* 
 support exists in other
controls, but it may vary by the type of control.






| 
 Attribute
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |
| 
 color
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Alpha colors may not be supported in some controls.
  |
| 
 background
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 In most cases, only applies to the entire text body.
  |
| 
 background-color
  | 
 ✔️
  | 
 ✔️
  |  |  |
| 
 background-image
  | 
 ✔️
  |  |  |  |
| 
 font
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-family
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-style
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-weight
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-size
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 text-decoration
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 underline
 
 ,
 
 overline
 
 ,
 
 line-through
 
 ,
 
 blink
 
 , and
 
 none
 
 . Support for each of these may vary depending on where they are used.
  |
| 
 text-align
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 justify
 
 is supported in output and maptext.
  |
| 
 vertical-align
  |  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 top
 
 ,
 
 middle
 
 , and
 
 bottom
 
 .
  |
| 
 text-indent
  | 
 ✔️
  | 
 ✔️
  |  |  |
| 
 margin-left
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 margin-right
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 margin-top
  |  |  | 
 ✔️
  |  |
| 
 margin-bottom
  |  |  | 
 ✔️
  |  |
| 
 margin
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 width
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |
| 
 height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |
| 
 line-height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Support in output control is limited; line heights less than 1 are not respected.
 
 Only unitless numbers, percentages, or em units are allowed.
  |
| 
 white-space
  | 
 ✔️
  | 
 ✔️
  |  | 
 normal
 
 ,
 
 nowrap
 
 ,
 
 pre
 
 ,
 
 pre-wrap
 
 ,
 
 pre-line
  |
| 
 text-shadow
  |  | 
 ✔️
  |  |  |
| 
 -dm-text-outline
  |  | 
 ✔️
  |  | 
 Custom attribute: Adds an outline to text. Values are in the form:
 
*width color style* 

 .
 
 The style is either blank, or any combination of the
 
 sharp
 
 and
 
 square
 
 keywords (see
 [Outline filter](#/{notes}/filters/outline) 
 ).
  |



 These pseudo-classes are allowed in some contexts, but they can only change
the text color.
 








| 
 Psuedo-class
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |
| 
 :link
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 :visited
  | 
 ✔️
  |  |  |  |
| 
 :active
  |  |  |  | 
 Currently not used, but future support is planned.
  |
| 
 :hover
  |  | 
 ✔️
  |  |  |




---


HTML colors
-------------




**See also:** 


[rgb proc](#/proc/rgb) 



 Text colors may be specified by name or RGB value. The RGB color format
uses hexadecimal numbers, with 2 hex digits each for red, green, and blue.
These range from 0 (00 in hex) to 255 (FF in hex). In certain situations
BYOND will also honor a fourth pair of digits for alpha.
 



```
#rrggbb
#rrggbbaa

```


 It is also possible to use 4 bit values by using only one hex digit per
color. The full 8 bit color is produced by repeating each digit. For example,
 `#F00` 
 (red) is the same as
 `#FF0000` 
 .
 



 The named colors supported by BYOND, and their corresponding RGB values,
are listed in the following table:






| 
 black
  | 
 #000000
  |  |
| 
 silver
  | 
 #C0C0C0
  |  |
| 
 gray
 *or* 
 grey
  | 
 #808080
  |  |
| 
 white
  | 
 #FFFFFF
  |  |
| 
 maroon
  | 
 #800000
  |  |
| 
 red
  | 
 #FF0000
  |  |
| 
 purple
  | 
 #800080
  |  |
| 
 fuchsia
 *or* 
 magenta
  | 
 #FF00FF
  |  |
| 
 green
  | 
 #00C000
  |  |
| 
 lime
  | 
 #00FF00
  |  |
| 
 olive
 *or* 
 gold
  | 
 #808000
  |  |
| 
 yellow
  | 
 #FFFF00
  |  |
| 
 navy
  | 
 #000080
  |  |
| 
 blue
  | 
 #0000FF
  |  |
| 
 teal
  | 
 #008080
  |  |
| 
 aqua
 *or* 
 cyan
  | 
 #00FFFF
  |  |




---


Color space
-------------




**See also:** 


[rgb proc](#/proc/rgb) 

[rgb2num proc](#/proc/rgb2num) 

[gradient proc](#/proc/gradient) 

[animate proc](#/proc/animate) 

[Color gradient](#/{notes}/color-gradient) 

[Color matrix filter](#/{notes}/filters/color) 








 There are different ways of interpreting color besides RGB. Several parts of
BYOND are capable of using other color spaces.
 


### 
 COLORSPACE\_RGB



 The default color space is RGB, where each color is split into red, green,
and blue components, as well as an optional alpha. All of these components range
from 0 to 255.
 



 The color yellow for instance is
 
 rgb(255,255,0)
 
 which is red and
green mixed together at their maximum brightness, but no blue component.
 


### 
 COLORSPACE\_HSV



![](data:image/png;charset=utf-8;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAACWCAYAAAA8AXHiAAAgQklEQVR4Xu2dDbAW1XnHz+677718XLkXAlEJUFCJWoGEWAtJDNUq0WrSRJNiVWq0EjRCk4ramphpTJ2mSRW1qZgPNMZINNRomvhVqxhQ0qEEO1WjQEDUCKiBGECC3Pved7f/uf5nntfnuc+cC5MZnZ1d5jfPOWfv7uXd/d/nefbsOedNiqII1Vbx+yalraiohFVRCauiElZFxe+PrLWSJAlLFYoZ4AwwGDwEfgAKUG1EPwRWHivObLAcXAjOAbeDL4Jqq0LhfpOBhSCh15pOT3UxvVe1VcLaL6aAd4KN4GdgDcvDwdRKPpWw9pcxtC8G2bbSHkxbUQlrnzmAtjvI1pAwWW2VsPaPX9MOD7KNoN1CW1EJa5/Z0JJrdVJgR9FrPeMcU1G58yjPs99qJljGtnZwM3gVVFvlsfab2eAucDg4BHwT/M3v48SVx6ryrE+G0myVx6qohFVRUQmrohJWRSWs8nMlKe9WCauiElZFJayKikpYFVXPexFWwjRJTktCrymLbbCs6eH+HtYbYonXxnZtR4Ep4CjUD8G5x6N8EOxIMALUQ8g7+vx7LVwCGiELr8Juh30Z9nnYTaEenoZ9EmxDOfSR0WqyAbTVQBtta1umqCmb0tZISsu2ZHo5hAVqtAno1bJrLZOUttbSlrOet7RntE0ek4BUkRgLDgMngQ+iAsI4wC3l+RICQ8umDjYOR/lQEEjrKX6FOkacgjQ8iPJG/nqfmion0kYrbQJF5NWdnw/lEhbJKIQg4pGyEpoWVBCPxzZeSSW4Zn/iOgJ2NuwZ4DCqwWCFnti/gcSpUzx9Qk1AGs5k20aIYCnKS1BeB1pE45Qz62msF7KCtG3alinHsp+Y1BxSY3mltZ+P3KFkBOrzwSqwFvUr3hBVsF5M1CGIglxxAXtYasqHgStQXgu7CsxHeQQ9kxaBkEX3wXpezIRH7i+Jx7L6TXRZUbhleimSSl28GG16OM69APYcMMgPjcEVk/VaNOZjGTGxLigBTSNXg+9h37Ww6ykKP4xlghWMxQ+1JfJY9mplOpGIXSHnKpsr926wBOVnsH/uG6KSu8qyIGITXPF7niqGm1MNgp0L+wz4Psrvln02FHrh01pFpnOvUgkrca5IJtYJb84+fY6RYBF4GpyNfamKH76YiGxWYD5+BLW/1o3YKTgLPA0WgZHAj+6ZLltLrEdLSiesLCKYNCI2tz3BceejvgFchHoGjKB0G4kLzBcT0VfRRlwS9zJZyGAvAhvAHLQntjtBl3VbhKx0oTCNXRXbHmc8jnkE3IRyV//h0oqMVvDzrn30WCrSiqYdz+Um3F2oL4Z9BHa8mx3EHTzPWf4cy/Eg0T9FscJstD0BjuvnSTHmKtzcygqsGGDoc9rTAYjJj/DHgSfAbOA78nqsK0JfzrdOWBM5POS74HowI9jtdHAT+BY4Ue0bCi4Dt4KvggkmxxLcsEe0aNrBYrTdhrZh/STysbgQCYXRkBgXWmqRMCQ43koLZxj23Qa7GLTHuxbsJbAh2P0Ufw6+wfv2aaWRc8At4AYwfX+F9RnwD+AT4HNgBTgzyHYVuIu/bC6nR81qmRr1KPgXHvP3YHUSJhzkeKOIwFJQD6zjHNljsHPQ5h4L7JW0sUnwXc++iSlR1ATdRvxuAyuyOeAxcHDsdQ6Iey+rgR+AH4MLed/PD7ItptjOBvPAY2DGPguLv2QEp5dfw7azaN8FLge76dlms/3ztOeC94FloAPcCUaCuf36/YF32EwC/4PyMao98jxuMl8To2wSFFxL4/9IKrAt6kF8UUidf0fHgFVonyT7JRRaXHHpbS6YRcGM5n07g/umgr8GW8FB4O9ARrvPwloNdrC8Wy2KMYMnXg5eoOdqgPdSjCfwuDtAD1jK+p9Ge9v98DUd+x4F4/TP2Le3vuiIERkwapDNvuax+lM6DfE+Jisghf80OA72UdjpVkBeSIyGwgtbbIMO5YXA+0Z7L3iVToft+yosOdETDIk/AV9yVl/ZC37D8sH0aNyvVmbx44C98iKUGbAPoW0420226ovJv+IWEZhVTyHlwguBfsSF9ckEu89lOHgIl2GGPc7J6TJiQ+EQMBl0Mx/eRqfyT+p+b6Z9iVdhMBi+P8IaD97J/RPBEWwfRtsTZOulrYNOlrv1yixRf22v8DSc8j60dYBAtKfSQtXC06HSy7+0+1GYl8/+U2DNtXHtE/vRzMfqAPeiPC0iToqNWGENZ2s72AMuZpT6AjgaDFP3swlylrP9EdYkeqBzwZHg+2r1lS65rFCuqPoVtTrLO2i3+IEf1l7FybAPou6IKhOk7uwzV1lZIzAS2bz8KnE/HqwRif0bqXvezIjuANgHYSe7OVx82Mx2kJNzwfVMbwKFpe9nF8/SzWMHLizl4tbQjqACNrD+AapgKrsXtjAkcn/4EO2xtE+a8OO/lxgNez9spxKTf9XtHfAFJXUlJLZFuxpsCBT8m+lHZ3cgn/3YdXNsJ+z9YIz/9ssXFgWyka2jlTN4GWxQ9/GDtE+BYl+F9TgfPb8DHmTb3VT1I+BZMJH7/h0EKr3gMTmYx8R9AdV948CS9XobLH5XNkbaoh5L4+VikcFLCTH5luOlIiKzIoo72rrg/7wR0BjwQ9DmXF43FJLraR/kU/xHeY8fBj8C2ymse8C3eMx1+5O8r2An2NlMzv8ZfKYltzoV/JTqHcLO1IUtT5Rn8ani42AT+FgR9jxjQw+wIlsEpgH/qtt9GraL9UWX+q997OYPm0kdMsEXmKn7//3MZRrOf6N7iVknevsm7+FQMBPcBz4M9jCRPwWsZlsP+Cy4fX/GY51H67E+8ri5lJhRo8x6Sa7Dzmz8zBzJEbnxOP8dXmHg+CxFrwiPZT+ZF7jZp0Lb1QC8Tk/fUwmeF3MEasc/ng+Wo32JfuCVMrGf6ssExvBzMO3tOmwmMno0G4+2Rf1muWIdTOzwQmOkazohLGuR+T3ufoSN/7dt2dZ9z2fztkWw4/3Xo6Uc3ZDg36DrkjB4fhKGZiKuLIH9jnr3F3seJ20xIam2WNe0DYXSQUqTOk+Cok+dlFutt0WidUxc/giHYbC3gIQiCslgXOBBYX7SFq4rp7AA4/mfgV8kYcgpvBrnwx7vDFLyMtkIbUp4hO061yKRUQ+RvqvMWt8jiTW0EdcZRwb8peE4MAd1iKovZflfcBq4Be0hT0okrBwUIQX5enAqqvPBNaPDhOVNWPfxyb9DniuI3y0h7rVg7RYZFpMpHL0T7ot3z/mh0JKHcPXYQ8N/8CnuqqIIJ+RFeDKn0y2NsNhdC5JQ9FE8jOp7loY7anhK7vRHkYolnmhIRmuIhMpabKyWJfFe3ajTa723s12LjPuk7oqL+H29aT10fveWvn6pyRDUnTLdBLY8M6HpsdTtgrgmwEyn5OSqoGyfHPPIZIeCSJ3nFWSWNWlQVD3Ouw9nM09bNp/yQ54rKlrPaXvj1/3BsSecGKY2izAOQvolYIpYMmE1QaLEhfKXUM4SaREBGZogeHVVLgS5nKQJ2iisOsWl3UKP47nEALcrzjpS0i4WKC/m5VSR5wwr8tZPn+Vv9E+dlYuoyuexkpYypHQ4+MuC7Sn2JiIMWk1qBCXYjcKyopJ+LdKjXILgnjsVbMIeCYOsi8ikbvMposKeN02S4mm1Z8D+I+w61kGJhNVQ1wLSuQSkSkoUmCMoCig+e9nK2nqtXoqsQUtxEd1Z6udWRESlRKPLqi5CE2reu3Nih5GJkKxNwQKU55ZMWPbWQhIjwWyWKbQ3WcqrJrJz863UWWgkifbGS57VY2KQHwpVs+rLJSYECmqf7Y7zR2jbaZLyyRxhsTwb9guw2xkGy+mxIItzYAd7czoJ6yms7kDK/VF2FgmLxms1SDvF1a3vpucFrah8L2UZRHTinilS/2G1AEZIfnkw7KfAQraVK3kvRBKfFpHBEu1jUrEgNd6K4XHgC3qwLA/d8nRIJUTFZecGmnwKaCE5XktyKzmPP4SfgoqIyN83B3Zh6UJhr9yPo2GPgBUPZt6KUD4si/gSUHNyr9TxeWbop+p+IPRYKtlRAvUmSKjwNigKxeW8cTIrzMQF1Yx7riPA0Sg/DsrTQdqQWzgLiK8QdBuzIGtzZ0imSloicWgwMXebxxuv5U7qFg9kBcRf4f8alq24RNt5YnvhGrT7Ugaz2FYaYbUK5nRJmSkoKyorulaxkcLGIj9zppgsQ5w7L+KiqFQotLmVaJV2qLTJPqVx74U0KBIrEisWQa6rPY6cTlsujwUOBYc54qHQnAvmXrSEAlOeizjeSjGEUBU81nY70IieVfhTp5O67xzbrbgKnLup/5B8zx4XHeG1P7SnbB4LnGyFFKfHvWitNwAC06FRBOUIaSitYB/ZakSEJaFKRCXa1KfXkdfpv6pRUMlArgcwbRZ7nXkPypS88yXJsbIaqZ9upxHkVjOxF8ulplDy6LfromhJ4PeSPXLnjceS931Gqx1kKBmixWS7ywognSBCLrCuyzaBD7rd7jsW9UWl6seCED6oOgm0mPxBmbqdVgQl9aYIzJzFn43Tq8QlYVGOU2GQzpDeiaKSMsUmpzHPBf4C5az7glLtRaRPK0j92FINm+kOYRRu2VjPbXcLuk38iGrrdugR+AQp+ZbNrjs4o3wYQTl0KEVkcpkSVtvlFDgEyOE8hZxGh0GcMq+9OVR1a6vK7mc357A0uI92DNpGlSl5n6JFpesiItbtRZU2A9sdoTUZu1oU4QirU8rYL49uKaCp8xQd6jBCYTEUUlQiKBGL4nW2w8rnUaKyImPdCtNea8lR31smYR3VHfVSxAiIdV9IvDG0xHq5JBSh3uqxyAFUxHDQRUuBQRkSDmna2CyHyaHDSMebRZVDjI1EC8YXF8v+zzt/hKpMTNuRZUreD7Fr7NNG1tZwE/vIRH0ZJKAnfaVobwtJv8MHAmhSirvBq2Bwq7DorSikES10UWxDpBuhyEx3gGBeiducirY1f2KdODlWYDmoNh5zSJmENcF9mwfSiOCcyfBEC4ttKle2E2BqYLBaQRbwdsl8zVd4BA8eSg81Eozi0invoKcSUUmoV6+8tbBylpWQWCexpJxYgVmRhTIJC254tPJWIhxbjq8S5DwluqtCkLZ+RwbX+wiEZ6YkdoGXqBZG0S5wIBhNRrGN+X5DhSLT76a8VC6WOIKyQmLZEmi192L94DJ5rJEiKOu5Ck9YntC8BYnduQ3xgQiDUGrjHnoosIceayOgtzoIjCOj6b0gqp6U+ZAIy3bwWlEBG/KskGgdQkRYqm1UmTxWl7MQI4XliwrY0GnFJz1Vbpj0h1BJl1QK7XRgXzv3BobDdYDhbyI4EkwAEFUDJ/pdy0NDN7GCovWE5Ic3trMeL4uXUvCYzjJ1kNaUeLjZeqLrjrjcsOlOUvbXj203XVP10IV4V0cNG9gAHnlj+bn3g6MgHCTwO1F8DVBYVlAkd3ImzyuFmDeyYqHnt/uCHX+blcljHcAP7i2OJ3UKQAtR6oITXmWf49kSR2itnREHgJHwXmPCNPquG/vWie6ZFsJmLga2k4LqIcojgXiiHVxLtGAcUZnj/GM6ypNj+R+WWAEVTpvzVYEWfQ4jQv8c9v8wDeUiJNMS+38hqt0KwV9t0j2n/3N2s+3+7y6Tx3qtoNeKiatwLmJBlDCAP5vQQq9hPIuEr26m7LvolTYDeKkQVoEwPdRRGMt0i91W9t0yqJFAmygi4Z1bNH3w23yx7i6Tx2r6bloE4O+Ll/28RWgqGoS5UXid+dJrDHPIo5BPgb8K3GbjmCJsCk+HF3F/OuXlj7y5IWZaoCIRq1Azlhxx8WdsThoXW2+ZhLUDIugy3sXzTFY0LFtyW5Zk2fdMsPZF7x4Kq1FnN8IEJut8CYICG3B8eC5sD7+FABsUFnBHyID4d5BJ2WL7+4h5gtbWtu0sUyjcDhGMj3gdWoUWl37NERFTL8veiNVu8jpopIxtI9iNeASYyLgn/Q1gB6WwBef4LWp78C+XSTl2pIw/X4IoYVkbFxw3v43t28okrK0sWu+jQpdtB5H3Y01fVPRSYnvtC1q0UxFDQSd70/+AnaAHst30kO4BBSWzA+faA/aGbmetDyCdtLHvBY+Li3VfXKmfy71UplD4HIvRd1xBys5MX4u8cxPbJGZCgqKo08UMBcNavNVoaqiL+wPVFzqptl0yhFEkA3F1o7UBG1mgz+ny8L9KypZDRGyOyJ4rk7A2uTlTXEgsi+2l9b2UNyFBbFGTrncOg4GIwDvJKOZZHaAulwsN8hYaXkpy4Rp5PRRhL4TVgz1NWK4S0SKwlNb/EgniCKwWGxVCQv9tz5ap5/2ZwvdW/nRx0nQTc2Lrdm4iyVPqQ0Qlg/beAUaQTrbLqBkWBlOFw5nq96iVncUP5aEHQF4o6VdKFJr9Cs/IQuHRhF8LznYYry3T0OQngHkSAzJYjVbKTKpp1QA4Qe0jZn8PBJUz7PU7MrlLj/Pjz7RpYbUpNfIgWDOElM+JeahDYgloHdRnR43S2gGM7oja+LDubjuS9MkyjSDdBjbrMdhSR1kLTaEvrtRFTFas9FwyI4yzapSwOgWOXcd+GVslVymVOV+iSmJOYOYrNkMWGhSYfF5jiW3zr5P9o2z0374ZXvuV0giLAlrZLWXrnXSb4I9pVyLV589rdi4FhQXsPArrbECmhcWTarfHk/EEZtC7UIfAUhGBY6OTRlxBsa3/LpaVpZqwSq+00kyoMJ7LislOvvBF2SBNZsd6CrxM17JTtsTJkHbJsM36RXZihqgS8GREpunoxbHykOrefyEiIuBfB6nra/OznrKtj5WH8J9uT7nFDs9162KLRH+VNK2ZAaYcS4eavdyu5qsaj2VnrIoEevXgYOcZr7fPFvgUTZCjxM8icyZJ7sy1bHo9+H5i/0BawtVmnm0AEBzP5ZZZ9xcLSdh9oNZT95ZtoICIaCO+LkhhF28QN0grZbsiiL9GZIFzNkMiXSP+Z7fXjUSWKHiWlMtj0UvdnYdwmTMdPOK1VLcDsWuBkrr1VrJQR2RNkDphfmW7Gv0xqHaqhP+NmeK5EpL3ebBeWP6U9VoEdeOpmsZbCTB3cV9phNUaHJbCXuZ2fqpZKr7o7Ne30RIjKqCdiLd+Fcmcbmwq2RdXQwkLyEAgRWoXkqPN+U/LMCeJ03FqwqDU72S9dKEQNjwOuw4EwYY3O1ZcyJPIIv0UEq0w2AmLZk1Qp2fSLJkMKC6e2K5wYy0xyym7L33ykNg5iA4NostgPVhTxoXXWrnJfHDTS27LuSwh5Ia8+NJYtIT7nJX1SOJ9iY5N6vwl/dp9QRErrJoWmC8q/erKlhdLWzlDIQi3onwV7OAm2/yw6HyNYI2Y8KeFZkOc1AW7Goz7dTpmegYPUk8MPbQSEtVwRmduUkOFyKbUUS5CTtCqrl1KWG5tfx32VtlXFo9lvc92lJdQbPqvTkicGaittGkhWVH5S2GTurcOqJeQ2K9TtTGY2DVQzX/EUldkxlUXIZWX7p4VloDtoHweq2n7r64F56Oc2pfQ8cUaJFR53koEZD2Tn97IOU0G7E060/kWadd/Jt7qC8540Ib97iA7rwmlAuQys8lOAM4hwOvUvhKFQtspuo5PiGdKW2QVEPX63ybwTp5l6lZQQvS7A1xB2YSvoYRmQ6I/aspcDAlkFBnbKLUiNEFq5bcUrBUJl+5LmqxXAleCv0A9s7NM457Kdi2oMq3NlQU5zlu0n9jswf8GTIoKVgX4NjXwJ0SmmGqaRPbrToic56MEe7H3y0DyrVJ1N7gTG5Ln8mTlKgpHUHURT/wbtmwy7llzTtp44k5r3aeNy0bd/pcU2n1C5lBzvxulgHzyZeH/oKwXKGOhTMLKTYdnciLME6GY1Qy15i4b8sw1BN63vXuJvCsyS03hDce0K3y1kDkCyxwhRRTPstjod81JPU93FeeGLag81Uz6okIQyvnVvYdDVPeheAO4NNS3HhfS2qX+l2cLVlBKSMZRaGt+Lj43y9/8JNDmW7Tmu3s9XFGRyF9fEvqu6YvZx1G5AHwxT8IyCGxKKT1WkfQVLwQPgEmhrbifN/ImsNx6K3uvrLj8LgfBejYRruOphIiooosnDfDbxn18MRHr6pejfhMIoag/goajwY/AeaX7hlXxAMXFUpaUAJwHnoCIhul8WMoa7zv/NJ4wdV7lhUATCjWRPpDeFttkGdYmCMQRMjCvnHkL5VzJLpTPg5UTFfjFobiBKTx/Q1EKj2X/uBNzD54H86x3dyKCJ6C2iKic3DcuKkELSkicWF63CWI8lrvxmnjt81F/vv8LnYp9i0Lh+8CPwctgF1gW/CWc7+F0og8H2SaDFWAv2Ao+r9bw92ZrLgE3Ww9l634a4iTmRlQOKfFFZbsERJHEPC1adceVb9tsu3bpN8Pexroi1R9uBPhXutHPBW5s/yp4ErwCfgZOVfr4NHgabAcPgSMHKqxzwXTwc/A8+FPwExs2w2ngI+CQlrnCneC/wIfAvZTAV0JP8gmVhhCT68yDCFY7T+/KAXhi8u6B9zujK3ZE+plSYn6BY+vuByM23scT+DUozwNBYQWf9H4WhS0AFo3cyAywAOzlvf8AuLtFPGeCb4OR4BfgRN7n2kCEdSeYAD4K/hjsBmPBoYEbBfRv9iEjnA0Oosf7JLic7RcoUXmdnt2wn4DdrMUgYjI2Tl0LVQnJ5liRXEfXU/81T/zpznO7zvFGsJthTwPdNuxZuH7OL+k49LYRTOF9nwaWUdl/wv2Xtzif4ymuQ8DJAxHWY2APy8PBINBUc/4X0UstVcdOoV1O+9+0R9k/HuXJhc3gFLATxEVUj0Qaf1aoYD2UrdtOUkXqUBP8mO2JKSaunbCngM1eTy9Q5XAJeA94SouBQlmnHEhoWZN8Et32T2lXSvoTFRYRz5OBb4BdbJ9Lz/S3wc5Rexftq8oeGHYmifVUFrY/BXsy2G2jhy37eW4kHKYKV0wxcaWC++EyHxv7/fAp59qN8smwTwF9AX2BFcOiC6/xoIXgj8B6cD/1kDKC7eUBv6E9eEDCYmx9HBwDbgYXs/04hsAl4NZgt0Kdt077uzCyKLSnsNdO2sAqcCrFZb2UTWGEmrWCt6yLIrgey8VfcZ5ELoArMvvBd8OeivoqLVz/w0o5so1gX+MCJukngW79vXykRrsnKiy6yQdBF9eym9MyjOdTjLkfozf6DNu/By5sCZejacfQvui9E6T1rs+jKM8EOyJ/6G7K4t9f7akM/kqfwBcWsQKLeCYjMM/z7cBxM1F+VJ1XC8gXmL8NAg+DmeBmOpYXuO9lUAROolT3efNAOkivBh187FzLntvA8gq1Vu37wWTmUhu4by6YxcfZs3nsspDZyXFo8yOIeKVVsDNg7wXjuD8qMFuPrLYhGB3FRx/EBWa9VLOlnJMMFGJJy/YrnP8jb86PEvm7bx27xbJs+UBi/EVgKrsRviIhjotEIwcDk3l/f9jSzbQiJqyUYZBPAEC2qeC7JJBrKaxvgmVU/AL2e+0EGb3Y1xh2dKSwNnNzrungx+AYKyonx3K9pJdvO+Ew+mSYOlhFU1SeuETAlp+Dj6OwlT9HGo4XKpxvlA0+8vQ3Uy13dClzrispqMXgetDBlOgXMWEl4CpHzVuD3e5lAv8063vBsVT+4eBX4BthTLE1HiV8cTFivAQ7A/YG7D/f9Uqpdx6SuoLyt8QUHPV5K1XVNBSRiEpswXaWAcPSfJSZNA+I2NK3D4BtYI1qWxvstpr2bnASI9EQ8FOKLMSE1QRfk2qUR0jrtoNuNBARTeL2Y7EcTcb3ws6BXQ67CHaYk5/RxsXkf8WFioBR1aVOp2mTmFBIS4GxrgZp70J5Psq3SVsSm5jhrSqvw+EPSRAQeeLbQ+Rt8a7QzyttfmWxuewSlKeCFX7uSry2RDAdo344jK8CynbB/08RL36vQHkq7G3uwD6bN/gXUz5kaYbN+MlzJkSTbrtvE+zxsHNxzh02L1MoAam2yEr9LvH1joWBdj/sgJ0LezzsJiUWbXXZis8eWx5h2T8yx5sYgYnV15f1AnYx6hPBjSj36nNaR2HmKlrs5sTFqCfzVxO1C3P3wt4IOxEsBoUSTERUce9FsZfNY8Xe07pP5n6bHL8ddh7aJqF8O2xuk/n9WDSddeK5tIG+5vFygBz1O8AklOehbTvswFy3HwrcdlAujyVERQYiQkzd7oT14Gzwh+DbYK/rpVK/70qsgz0wkrgBG4v3wn4bHIXyWWC96dyLd4DGUOdLyhQKtZfRAtHYF9W+CN2+yPWwF8COg70UrHNfOKcRocW9leO13OHL68ClKI+DvYB17osk32yPvov0/3pLlrxnINEeOhYCiT+8yGInr2wDC6GHI2GPgb0GdqP/1LfP+VW0z4Jq3oi2a8Ax4EjUF8JuE8EkzhNfKliRedO/Yo/JZUzeB/q+MN557b/zc8ewr4G9DEwk88EdaN8senC6guLhUPdjbEH5Dtj5YCLKILkMdo3/slra46Ewi4jI1klZQ2Hc49hUwhGUfy4/1Ilj2QgWgbPQPhb2QL7GuBh8HdyDttVgUyjCb1H/XYuYUE7QFjaxR/oe1L/OY2eifCAYA5A3pYvorbTqvcfiyPTvqGh8AUp7iWbprErC23z7NXiYeNuVylbEPFZFRSWsikpYFZWwKireiuS9okraK49VUQmrohJWRUUlrIpKWG897uor5ETwKOfVrQZnDGT1lUpY1eauvsKZRvdyEu9dYCy4A5wQW32lEla1uauvcDmmdi4rMA9cARJwfGz1lUpY1eauvsLQ1wtm0HudBHKwLLb6StVBWm27g789CS7ghNF1bFtAIY2lx3/NWX2lElaFyzQm9c8xtzqNE3rXktjqK5YqFFYwh+oAc5hfncEQ+PmBr75SCavC0lQLyo2j7QXdTNYTMAt0qtVXqlBY4XI912L9DriMCXwOrgUhuvpK5bEqwAPga2r1lZVgCrgOPANuAFPBfWr1le/x+IsAwma1JUVRhGqrqDxWRSWsikpYFRWVsCre/vw/jy4G2fRxv14AAAAASUVORK5CYII=)
 Hue values on the color wheel
 

 HSV stands for hue, saturation, and value.
 


* Hue ranges from 0 to 360 on a color wheel, where 0 is red, 60 is yellow,
120 is green, and so on as seen in the image.
* Saturation is how colorful this color is; it ranges from 0 which means a
shade of gray, to 100 which is fully colored.
* Value is the brightness of the biggest red, green, or blue component, and
ranges from 0 to 100. A value of 0 is always black.



 All pure hues such as red (hue=0) have a saturation of 100 and a value of
100. As saturation decreases, the colors turns whiter. Lower values mean
darker colors and darker shades of gray.
 



 In HSV, saturation is less meaningful as value gets closer to 0. Black
of course always has a value of 0. With 10 as the value, saturation=100 gives
you a very dark color whereas saturation=0 is a 10% shade of gray.
 


### 
 COLORSPACE\_HSL



 HSL is a little more intuitive than HSV. Here, the value is replaced by
luminance, which again ranges from 0 to 100. Luminance is the average of the
minimum and maximum values of the red, green, and blue components.
 



 Black has a luminance of 0; white has a luminance of 100. Pure hues all
have a saturation of 100 and luminance of 50. As saturation decreases, the
color will approach a grayscale shade of L%.
 



 Saturation is less meaningful the closer luminance is to 0 or 100. At a
luminance of 100, the saturation is totally irrelevant. At 90, high saturation
will get you a very light shade of the hue but that isn't very far off from a
90% shade of gray.
 


### 
 COLORSPACE\_HCY



 HCY stands for
 **hue** 
 ,
 **chroma** 
 , and the Y is for grayscale
luminance. (Again chroma and Y range from 0 to 100.) This color space is
based around the apparent brightness of each color according to a rough
approximation of human vision.
 



 Chroma is similar to saturation in that it determines how far from
grayscale the color is. As chroma decreases toward 0, the color approaches
a grayscale shade of Y%. What's different about HCY color from HSV or HSL
is that at chroma=0 and chroma=100 the colors should appear equally
bright. Pure red, therefore, has a hue of 0, a chroma of 100, and a Y
luminance of only 29.9—roughly what red would look like in black &
white with all the color leached out.
 




---
stddef.dm file
----------------



 This is a special file that's included in all projects when you compile.
It contains various constants, definitions of some built-in datums, and so on.
 



 You can see the contents of this file by creating a new file in Dream
Maker called
 
 stddef.dm
 
 . It will automatically be filled with the
standard definitions.
 



 The contents of
 
 stddef.dm
 
 may change with new BYOND versions.
However an eye is always kept on backwards-compatibility.
 




---


**Top Buccaneers:**


 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---


Import proc (world)
---------------------




**See also:** 


[Export proc (world)](#/world/proc/Export) 

[Import proc (client)](#/client/proc/Import) 

[Topic proc (world)](#/world/proc/Topic) 

[fcopy proc](#/proc/fcopy) 







**Format:** 


 Import()
 



**Returns:** 


 The file sent by the remote server. The file will be downloaded to the
 local server's resource cache. Note that this will cause the caller to
 sleep while waiting for the necessary data to be transfered.
 



**When:** 


 Call this inside world.Topic() if you are expecting a file from the
 remote server.
 

### 
 Example:



 //sending the file
mob/proc/Export(Addr)
 var/savefile/F = new()
 F.Write(src)
 world.Export(Addr,F)

//receiving the file
world/Topic()
 var/savefile/F = new(world.Import())
 F.Read() //read the mob
 

 This example defines a mob proc called Export() which writes the mob to a
savefile and sends it to another server (specified by Addr). The remote
server opens it as a savefile and creates the mob (if the same mob type is
defined on both servers and mob.Read() is compatible with the sending
server's mob.Write()).
 



 Note that another method of transferring player mobs is to use the key
savefile (accessed by client.Export() and client.Import()). Direct server
to server communication on the other hand could transfer data (like
non-players) without the need for player involvement at all.
 



 Savefiles are the most common type of file to transfer, but world.Import()
simply returns a reference to an item in the world's .rsc file, which could be
any type of file. This particular example demonstrates how to open such a
file as a temporary savefile. (It gets dumped from the cache into a separate
temporary file, which is then opened as a savefile.) Other types of files
would be handled differently. For example, you could use fcopy() to dump the
cached item to its own separate file.
 




---
IsBanned proc (world)
-----------------------




**See also:** 


[GetConfig proc (world)](#/world/proc/GetConfig) 

[params2list proc](#/proc/params2list) 

[address var (client)](#/client/var/address) 

[computer\_id var (client)](#/client/var/computer_id) 

[connection var (client)](#/client/var/connection) 

[hub var (world)](#/world/var/hub) 









**Format:** 


 IsBanned(key,address,computer\_id,type)
 



**Returns:** 


 True value if user is banned from this world. This may be a list, in which case special meaning is attributed to certain list elements as described below.
 



**Args:** 


 key: BYOND key of the user.
 
 address: current IP address of the user.
 
 computer\_id: current computer\_id of the user if known.
 
 type: type of connection if known (see
 [client.connection](#/client/var/connection) 
 )
 





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
 




---
IsSubscribed proc (world)
---------------------------




**Format:** 


 IsSubscribed(player)
 
 IsSubscribed(player, "BYOND") (to check BYOND Membership)
 




**Returns:** 


 Number of days left in subscription, -1 for a lifetime subscriber,
 *or* 
 null if hub contact failed
 



**Args:** 


 player: a mob, client, key, or ckey
 


 Checks a player for their subscription status to this game. This is a
simpler alternative to
 
 client.CheckPassport()
 
 , which is deprecated,
and also allows you to check even when the player has gone offline.
 



 This proc will return null if contacting the hub was required, but there
was no way to reach the hub. Contacting the hub may take a few moments, so it
is a good idea to use
 [spawn()](#/proc/spawn) 
 to avoid
holding up the rest of the game.
 


### 
 Example:



 mob/verb/JoinClub()
 if(!world.IsSubscribed(src))
 src << "Sorry, the club is only for subscribers."
 else
 // go to the turf with the tag "clubhouse"
 loc = locate("clubhouse")
 src << "Welcome to the clubhouse!"
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---
New proc (world)
------------------




**Format:** 


 New()
 



**When:** 


 Called after the world is initially loaded. The only procs preceding
 this one would be in the initialization of global variables and objects
 on the map.
 



**Default action:** 


 None.
 



---
OpenPort proc (world)
-----------------------




**See also:** 


[port var (world)](#/world/var/port) 

[visibility var (world)](#/world/var/visibility) 





**See also:** 


 OpenPort(port=0)
 



**Args:** 


 port: the network port to open
 



**Returns:** 


 1 on success; 0 on failure
 


 This causes the world to be hosted on the specified network port. A value
of 0 or "any" requests that any available port be used. The value "none"
causes the port to be closed so that no new connections are possible.
 



 This proc may be overridden. If it is, calling ..() is necessary to open
the port. If ..() is not called, it will not open.
 


### 
 Example:



 world/OpenPort(port)
 // only allow subscribers to host
 if(host\_is\_subscribed)
 return ..()
 

 The "ports" configuration option in cfg/byond.txt can be used to control
what ports worlds may open. The -ports command-line option may also be used.
See
 [startup](#/proc/startup) 
 for the syntax.
 




---
PayCredits proc (world)
-------------------------




**See also:** 


[AddCredits proc (world)](#/world/proc/AddCredits) 

[GetCredits proc (world)](#/world/proc/GetCredits) 





**Format:** 


 PayCredits(player, credits, note)
 



**Returns:** 


 1 if the credits were spent successfully, 0 or null otherwise.
 



**Args:** 


 player: a mob, client, key, or ckey
 
 credits: A number of credits to deduct from the player's account
 
 note: An optional note (for author purposes) for the credit change
 




 Removes credits from a player's account, if they have enough. The proc
will return 1 if it is successful, or 0 if the attempt failed (usually
because the player doesn't have enough credits). This feature is intended
for games that make use of the credit system, and for security all such
games must use a hub password.
 



 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is often a good idea to use spawn() to avoid holding up the
rest of the game.
 


### 
 Example:



 mob/proc/ItemShop()
 var/items = list("Get credits!", "Magic sword"=10, "Skeleton key"=50)
 var/choices[0]
 var/item,price
 for(item in items)
 price = items[item]
 choices["[item]: [price] credit\s"] = item

 var/credits = world.GetCredits(key)
 if(isnull(credits))
 src << "Sorry, the item shop isn't available right now."
 return

 var/choice = input(src,\
 "You have [credits] credit\s. What would you like to purchase?",\
 "Item Shop")\
 as null|anything in choices
 if(!choice) return // cancel

 if(choice == "Get credits")
 src << link("http://www.byond.com/games/Author/MyGame/credits")
 return

 item = choices[choice]
 price = items[item]
 if(!price) return

 src << "Contacting item shop..."
 var/result = world.PayCredits(name, price, "Item shop: [item]")

 if(isnull(result))
 src << "Sorry, the item shop isn't available right now."
 else if(!result)
 src << "You need [price-credits] more credit\s to buy [item]."
 else
 src << "You bought \a [item]!"

 // Now give the user the item and save their character
 // These procs are for you to define
 src.AddEquipment(item)
 src.SaveCharacter()
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---
Profile proc (world)
----------------------




**Format:** 


 Profile(command, format)
 
 Profile(command, type, format)
 




**Returns:** 


 Profilng data or null
 



**Args:** 


 command: A numerical value that says whether to start, stop, refresh, etc.
 
 type: A type of profile to use, other than proc profiling.
 
 format: Optional format for output data
 




 Interacts with the built-in server profiler without requiring the host to do
so via Dream Daemon, or an authorized player via Dream Seeker.
 



 The
 
 command
 
 value is built from bitflags, so it can combine any of
these three values via the
 
 |
 
 operator:
 




 PROFILE\_STOP
 

 Stop profiling. Not using this flag will start/continue profiling.
 

 PROFILE\_CLEAR
 

 Clear all profile data. This will also cause the proc to return null.
 

 PROFILE\_AVERAGE
 

 Any output data should use average times instead of total times.
 


 These additional values are also defined for convenience:
 




 PROFILE\_START
 

 Start/continue profiling but don't clear any existing data.
 

 PROFILE\_REFRESH
 

 Currently this is the same as
 
 PROFILE\_START
 
 .
 

 PROFILE\_RESTART
 

 Start profiling and clear existing data.
 

### 
 Profiling procs



 By default, data will be returned as a list. The first six values are the
column names:
 
 "name"
 
 ,
 
 "self"
 
 ,
 
 "total"
 
 ,
 
 "real"
 
 ,
 
 "over"
 
 , and
 
 "calls"
 
 , corresponding to the
columns in the profiler. These are followed by the profile data for each proc,
with the data being in the same column order. E.g. the next six items
represent the first proc in the profile.
 



 The optional
 
 format
 
 argument however can be used to return the
data in other formats. Currently the only accepted value is
 
 "json"
 
 ,
which will output the same data in JSON format.
 


### 
 SendMaps profile



 Using
 
 "sendmaps"
 
 in the
 
 type
 
 argument will profile the
routines used to send map informaiton to players. Unlike the proc profiling
this only has three data columns:
 
 "name"
 
 ,
 
 "value"
 
 , and
 
 "calls"
 
 . The value column might be a time or number value, depending
on what's being measured.
 



 The JSON format will include a
 
 unit
 
 property data that is not a
raw number, such as a time value.
 




---
Reboot proc (world)
---------------------




**Format:** 


 Reboot(reason)
 



**Args:** 


 reason: the reason
 
 Reboot()
 
 was called:
 * 0 or null: Called by game code
* 1: By host (Ctrl+R in Dream Seeker)
* 2: By
 [world.Topic()](#/world/proc/Topic)
* 3: By SIGUSR1 in UNIX






**Default action:** 





 Reload the world from scratch. Any connected players will automatically
relogin. This would be useful if you needed to recompile the world after
changing some code.
 



 In a UNIX environment, you can cause a running server to reboot by
sending it the signal SIGUSR1.
 



 If you override this proc, you must call ..() if you want the reboot to
complete normally.
 



 For reboots initiated by Dream Seeker, usr will be the mob belonging to
the player who sent the command.
 




---
Repop proc (world)
--------------------




**Format:** 


 Repop()
 



**Default action:** 


 Reload the obj and mob instances defined in the world map. This
 "repopulates" a world to its initial state. Only objects that were
 destroyed will be recreated.
 



---
SetConfig proc (world)
------------------------




**See also:** 


[GetConfig proc (world)](#/world/proc/GetConfig) 




**Format:** 


 SetConfig(config\_set,param,value)
 



**Args:** 


 config\_set: name of the configuration set (see below)
 
 param: name of the configuration parameter
 
 value: data to store (or null to delete this entry)
 




 This command is for storing configuration information that is shared by
applications installed on the same system. The configuration data is
accessed by specifying the configuration "set" and the parameter within that
set.
 



 For more information, see
 [GetConfig](#/world/proc/GetConfig) 
 .
 




---
SetMedal proc (world)
-----------------------




**See also:** 


[GetMedal proc (world)](#/world/proc/GetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 

[GetScores proc (world)](#/world/proc/GetScores) 

[SetScores proc (world)](#/world/proc/SetScores) 







**Format:** 


 SetMedal(medal, player)
 



**Returns:** 


 1 if the medal was awarded successfully, 0 or null otherwise.
 



**Args:** 


 medal: name of the medal being awarded
 
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
SetScores proc (world)
------------------------




**See also:** 


[GetScores proc (world)](#/world/proc/GetScores) 

[GetMedal proc (world)](#/world/proc/GetMedal) 

[SetMedal proc (world)](#/world/proc/SetMedal) 

[ClearMedal proc (world)](#/world/proc/ClearMedal) 







**Format:** 


 SetScores(key, fields)
 



**Returns:** 


 The key, if the scores were successfully updated; null otherwise.
 



**Args:** 


 key: the name of the player, character, etc. for which scores should be set
 
 fields: The data fields to set
 



 Updates scores that are kept on the BYOND hub.
 



 The key is an arbitrary text value. Usually a player's key is a good
choice, but you can also use the name of their character, or anything else
you like, as long as it is unique. The key is case-insensitive.
 



 Scores and stats use data fields, which might be things like "Score",
"Level", "Class", etc. Use list2params() to set the fields that you want to
change. Fields that you do not include in the list will not be changed. A
field with a blank value will be deleted.
 



 Sending an empty text string for the fields will erase the scores for that
key.
 



 This proc will return null if there was no way to reach the hub. Use
isnull() to check for a null value. Contacting the hub may take a few
moments, so it is a good idea to use spawn() to avoid holding up the rest of
the game.
 


### 
 Example:



 var/params

// Change the Score and Pet fields
params = list("Score"=123, "Pet"="Dog")
world.SetScores("Tom", list2params(params))

// Delete the Pet field
params = list("Pet"="")
world.SetScores("Tom", list2params(params))

// Delete Tom's scores entirely
world.SetScores("Tom", "")
 

 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.
 




---
Tick proc (world)
-------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_usage var (world)](#/world/var/tick_usage) 






**Format:** 


 Tick()
 



**When:** 


 Called during the server tick, after sleeping procs and queued commands,
just before map information is sent to the clients.
 



**Default action:** 


 None.
 


 This proc allows you to do any updates just before map info is sent out.
One possible use for this is to run a movement loop, or sync up any user
interface input that might have arrived and deal with it all at once.
 


### 
 Example:



 world/Tick()
 for(var/client/C)
 if(C.mob?.move\_dir)
 try
 step(C.mob, move\_dir)
 catch
 // empty catch, just so a failed step won't break the loop
 

 Note: The tick will not wait if this proc sleeps. It effectively has
 [set waitfor=0](#/proc/set/waitfor) 
 already built in.
It's a good idea not to sleep in this proc or any of its callees at all,
since it will keep getting called every tick.
 




---
Topic proc (world)
--------------------




**See also:** 


[Del proc (world)](#/world/proc/Del) 

[Export proc (world)](#/world/proc/Export) 

[Import proc (client)](#/client/proc/Import) 

[Import proc (world)](#/world/proc/Import) 

[Reboot proc (world)](#/world/proc/Reboot) 








**Format:** 


 Topic(T,Addr,Master,Keys)
 



**When:** 


 Called when a message is received from another server by using
 world.Export(). If a file is expected, world.Import() may be called to
 get it. The return value of Topic() will be passed back to the remote
 server.
 



**Args:** 


 T: The topic text string specified by the remote server (everything following ? in the URL).
 
 Addr: The address of the remote server.
 
 Master: 1 if remote server is the server which started this one.
 
 Keys: List of keys belonging to users who are logged in on the remote server
 






**Default action:** 


 The topic "ping" returns a true value (number of players plus one),
 which may be useful for telling if a server is alive. The topics
 "Reboot" and "Del" will call world.Reboot() and world.Del()
 respectively if the message was sent by the master server.
 

### 
 Example:



 world/Topic(T)
 if(findtext(T,"shout:") == 1)
 world << copytext(T,7)
 

 This example allows other servers to send this server topic text of the
form "shout:msg" and will broadcast the message to all the players in this
world.
 



 The Keys argument is either null, or a list of user keys. Any keys in the
list are logged in to the remote server.
 



 Always validate the input in
 
 Topic()
 
 calls
to make sure it's correct and the query you're recieving is legitimate.
 




---
vars (world)
--------------



 Built-in world vars:
 




 world/var
 

[address](#/world/var/address) 

[area](#/world/var/area) 

[byond\_build](#/world/var/byond_build) 

[byond\_version](#/world/var/byond_version) 

[cache\_lifespan](#/world/var/cache_lifespan) 

[contents](#/world/var/contents) 

[cpu](#/world/var/cpu) 

[executor](#/world/var/executor) 

[fps](#/world/var/fps) 

[game\_state](#/world/var/game_state) 

[host](#/world/var/host) 

[hub](#/world/var/hub) 

[hub\_password](#/world/var/hub_password) 

[icon\_size](#/world/var/icon_size) 

[internet\_address](#/world/var/internet_address) 

[log](#/world/var/log) 

[loop\_checks](#/world/var/loop_checks) 

[map\_format](#/world/var/map_format) 

[map\_cpu](#/world/var/map_cpu) 

[maxx](#/world/var/maxx) 

[maxy](#/world/var/maxy) 

[maxz](#/world/var/maxz) 

[mob](#/world/var/mob) 

[movement\_mode](#/world/var/movement_mode) 

[name](#/world/var/name) 

[params](#/world/var/params) 

[port](#/world/var/port) 

[process](#/world/var/process) 

[realtime](#/world/var/realtime) 

[reachable](#/world/var/reachable) 

[sleep\_offline](#/world/var/sleep_offline) 

[status](#/world/var/status) 

[system\_type](#/world/var/system_type) 

[tick\_lag](#/world/var/tick_lag) 

[tick\_usage](#/world/var/tick_usage) 

[time](#/world/var/time) 

[timeofday](#/world/var/timeofday) 

[timezone](#/world/var/timezone) 

[turf](#/world/var/turf) 

[url](#/world/var/url) 

[vars](#/datum/var/vars) 

[version](#/world/var/version) 

[view](#/world/var/view) 

[visibility](#/world/var/visibility) 















































---
address var (world)
---------------------




**See also:** 


[port var (world)](#/world/var/port) 

[url var (world)](#/world/var/url) 

[internet\_address var (world)](#/world/var/internet_address) 





 This is the network address of the machine hosting the world. If it
cannot be determined, it will be null.
 



 The full network address of the world may be formed by concatenating the
world address and port: "byond://[address]:[port]".
 



 In CGI mode, this is the web address of the world.
 



 This is the local address only. If the world is hosted via a router, the
external IP address may be different. Use
 
 internet\_address
 
 to find
the external address, if available.
 




---
area var (world)
------------------




**Default value:** 


 /area.
 


 This is the default area type to be placed on the map wherever no area is
specified. A value of 0 turns off the default area.
 




---
byond\_build var (world)
--------------------------




**See also:** 


[DM\_VERSION macro](#/DM/preprocessor/DM_VERSION) 

[byond\_version var (world)](#/world/var/byond_version) 

[byond\_version var (client)](#/client/var/byond_version) 

[byond\_build var (savefile)](#/savefile/var/byond_build) 

[byond\_version var (savefile)](#/savefile/var/byond_version) 







 This is the build number (minor version) of BYOND being run by this server.
Typically this is not useful information, but it can come in handy when
diagnosing issues reported by players when hosting with a beta build.
 




---
byond\_version var (world)
----------------------------




**See also:** 


[DM\_VERSION macro](#/DM/preprocessor/DM_VERSION) 

[byond\_build var (world)](#/world/var/byond_build) 

[system\_type var (world)](#/world/var/system_type) 

[byond\_version var (client)](#/client/var/byond_version) 

[byond\_build var (savefile)](#/savefile/var/byond_build) 

[byond\_version var (savefile)](#/savefile/var/byond_version) 








 This is the version of BYOND at run-time. A game designed to work around
known bugs in older versions could use this to adapt its behavior accordingly.
 




---
cache\_lifespan var (world)
-----------------------------




**See also:** 


[cache](#/DM/cache) 




**Default value:** 


 30 (days)
 


 Number of days items that are not in use will be saved in the resource
cache (.rsc file). Files uploaded by players are stored in the world's .rsc
file for future use. If the file is not used for the specified amount of
time, it will be removed to save space.
 



 Setting this value to 0 causes items to be saved for the current session
only. This is used by the CGI library, because web browsers cannot make use
of server-side caches when uploading files anyway.
 



 This value must be a whole number.
 




---
contents list var (world)
---------------------------




**See also:** 


[list](#/list) 




**Default value:** 


 List of all areas, turfs, mobs, and objs initially in the world.
 


 This is a list of every object in the world. Objects in this list are in
no particular order.
 


### 
 Example:



 proc/ListAreas(mob/M)
 var/area/A
 M << "Areas:"
 for (A in world.contents)
 M << A
 

 This example displays a list of every area in existence. As a convenient
short-hand, one may simply write for(A) or for(A in world) instead of the
full for(A in world.contents).
 




---
cpu var (world)
-----------------




**See also:** 


[map\_cpu var (world)](#/world/var/map_cpu) 

[tick\_lag var (world)](#/world/var/tick_lag) 

[tick\_usage var (world)](#/world/var/tick_usage) 

[Tick proc (world)](#/world/proc/Tick) 






 This is the percentage of a server tick that the server spends processing
running procs and the work of sending map information to players. A value of 0
would indicate very little cpu usage. A value of 100 would indicate full cpu
usage, which could mean that the server cannot complete all the necessary
computations during a tick to finish in time for the next tick. In this case,
timed events (such as sleep) may take
longer than requested.
 



 When deciding on a value for tick\_lag, one could use this value to
determine if the CPU is fast enough to tick at a higher rate.
 



 The
 
 map\_cpu
 
 var is a subset of this, measuring only time used for
sending map information.
 




---
executor var (world)
----------------------




**See also:** 


[startup proc](#/proc/startup) 




**Format:** 


 executor = "/usr/local/byond/bin/DreamDaemon [params]"
 


 This option is for direct execution of
 `.dmb` 
 files in UNIX.
The most common use is for writing CGI programs that are executed by the web
server.
 



 The first parameter in the
 
 executor
 
 text string is the path to
DreamDaemon. The one listed above is the standard UNIX location.
 



 Optional parameters may follow. The most common are -CGI and -logself.
 


### 
 Example:



 world/executor = "/usr/local/byond/bin/DreamDaemon -CGI -logself"
 

 This example creates a CGI program to be executed by a web server. It
puts its error output in the file
 `projname
 
 .log` 
 .
 



 All of this is configured for you when you include
 `html/CGI.dm` 
 from the html library.
 




---
fps var (world)
-----------------




**See also:** 


[tick\_lag var (world)](#/world/var/tick_lag) 

[fps var (client)](#/client/var/fps) 

[Pixel movement](#/{notes}/pixel-movement) 






**Default value:** 


 10
 


 The value of
 
 world.fps
 
 defines the speed of the world in frames
(server ticks) per second. By default this is 10 fps, which is a good speed if
all objects move in full tiles. Higher values yield smoother results, but at a
cost to performance. Timing of many events may be limited by the system clock,
so
 
 fps
 
 values beyond 40 or 50 may cause unwanted effects like jitter
even for projects that are not very demanding in terms of performance.
 



 For projects making use of pixel movement, higher
 
 fps
 
 is usually
desired. 40 seems to be a good value for general use, but in worlds that have
a large number of players, you may wish to lower the value and give players a
higher
 
 step\_size
 
 per tick instead.
 



 This var exists for convenience; it is calculated by
 
 10 /
world.tick\_lag
 
 . The value of
 
 world.tick\_lag
 
 is actually more
accurate, but it is easier to think of world speed in terms of frames per
second. The actual tick rate has a resolution of 1 ms.
 



 When reading
 
 world.fps
 
 , the result is always given as a whole
number to gloss over rounding error.
 



 If you set
 
 client.tick\_lag
 
 or
 
 client.fps
 
 to a value other
than 0, you can make the client tick at a different (usually faster) rate.
 




---
game\_state var (world)
-------------------------




**See also:** 


[name var (world)](#/world/var/name) 

[status var (world)](#/world/var/status) 

[visibility var (world)](#/world/var/visibility) 






**Default value:** 


 0
 


 At runtime, this value may be changed to let the BYOND hub know about
certain changes in the game's status. An example for using this value is if
the number of players in the game gets too high and most new logins are
rejected, you can set game\_state to 1 to let the hub know this server is
full.
 



 The following values are accepted:
 




 0
 

 Normal status
 

 1
 

 Server is full
 


 Note that this value does not affect how your world actually reacts to new
players logging in. It is only used by the hub and website.
 




---
host var (world)
------------------




**See also:** 


[game\_state var (world)](#/world/var/game_state) 

[name var (world)](#/world/var/name) 

[status var (world)](#/world/var/status) 

[visibility var (world)](#/world/var/visibility) 







**Default value:** 


 null
 


 If the information is made available by the pager, this will provide the
key of the world's host. If the host is not known, this value will be either
null or an empty string.
 




---
hub var (world)
-----------------




**See also:** 


[hub\_password var (world)](#/world/var/hub_password) 

[name var (world)](#/world/var/name) 

[status var (world)](#/world/var/status) 

[game\_state var (world)](#/world/var/game_state) 

[version var (world)](#/world/var/version) 

[visibility var (world)](#/world/var/visibility) 









**Default value:** 


 null
 


 This is a registered
 [BYOND hub](http://www.byond.com/hub/) 
 path.
The default value of null is for unregistered games. Registered games (don't
worry, it's free!) have their own hub page showing a brief description of the
game, the author, an optional installation package, and links to online games.
The hub path is a string of the form "YourName.GameName" and can be found in your
 [hub console](https://secure.byond.com/members/?command=edit_hub) 
 .
 



 Even unregistered games show up in the hub when they are live (that is
online with people connected). It just doesn't show any of the extra info
like a description, and there is no way for people to find out about it when
nobody is logged in.
 



 If you do not want your game to show up in the hub (like while you are in
the initial stages of development), just compile with
 `visibility=0` 
 . Either that, or turn off your pager or your BYOND
locator when you are connected to it.
 



 You (or the players) might also wish to turn off the notice of a live
game in the hub when there is no longer any room for new players or if it is
too late in the game for new people to join. At such times, you can simply
set the visibility to 0.
 


### 
 Example:



 world
 hub = "Dan.PipeStock" //registered hub path

mob/verb/start\_game()
 world.visibility = 0
 //...
 

 If you configure your hub page to require a hub password, you must also
specify
 `world.hub_password` 
 .
 




---
hub\_password var (world)
---------------------------




**See also:** 


[hub var (world)](#/world/var/hub) 

[visibility var (world)](#/world/var/visibility) 





**Default value:** 


 null
 


 If
 `world.hub` 
 is set, any live session of the game will be
attached to the specified BYOND Hub page. Under the default settings,
any game can set
 `world.hub` 
 and attach itself to any BYOND
Hub page.
 



 To beef up security, you can set a hub password in your hub's
configuration page via the BYOND website. This will ensure that
only authorized copies of your game can attach themselves to your
hub page when live. Then simply copy that password into your code as
 `world.hub_password` 
 so that your game's live broadcast will
be accepted by the hub.
 


### 
 Example:



 world
 hub = "Dan.PipeStock" //registered hub path
 hub\_password = "UPAggnJaeXmSBoKK" //password for live game authentication
 

 Note that for security reasons, reading this variable at runtime will
return a hashed version of the value that was set.
 




---
icon\_size var (world)
------------------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[step\_size var (movable atoms)](#/atom/movable/var/step_size) 

[Gliding](#/{notes}/gliding) 

[Pixel movement](#/{notes}/pixel-movement) 







**Default value:** 


 32
 


 This is the tile size that will be used as a default for icons in the
world. It can be set to a single number that represents both the width and
height, or you can use a format like "[width]x[height]" (such as "16x48") to
specify width and height separately.
 



 This value affects several calculations, including icon operations and
gliding between turfs.
 



 Note: If you do not use a square icon size and you are using a topdown map
format, you may experience display issues if setting
 
 client.dir
 
 to
 
 EAST
 
 or
 
 WEST
 
 . A non-square tile with a topdown map format
will also interfere with pixel movement. For this reason, square sizes are
recommended when using any topdown-view map format.
 




---
internet\_address var (world)
-------------------------------




**See also:** 


[port var (world)](#/world/var/port) 

[url var (world)](#/world/var/url) 

[address var (world)](#/world/var/address) 





 This is the network address of the machine hosting the world, as it is
seen by the outside network (from the Internet) and the hub. If it cannot
be determined, it will be null.
 



 The full network address of the world may be formed by concatenating the
world address and port: "byond://[address]:[port]".
 



 This var exists because
 
 world.address
 
 may not be accurate if the
world is hosted on a machine behind a router using NAT. The value returned
by
 
 internet\_address
 
 can be given to other players who wish to log
in.
 




---
log var (world)
-----------------




**See also:** 


[file proc](#/proc/file) 

[startup proc](#/proc/startup) 




 Sending output to world.log may be useful for debugging purposes. The
output goes to the same place run-time proc errors are displayed.
 


### 
 Example:



 if(1+1 != 2)
 world.log << "Uh oh."
 

 You can assign world.log to a file name or file() object to redirect output
to that file. (There is also a command-line option to Dream Daemon that does
this.)
 


### 
 Example:



 world.log = file("mylog.txt")
 


---
loop\_checks var (world)
--------------------------




**Default value:** 


 1
 


 Setting this to 0 disables the very long loop protection. By default,
loops in the code which undergo a very large number of iterations or
recursions are aborted (by crashing the proc). This prevents the proc from
locking up the server for too long.
 



 You may need to disable this feature if your code has some very long loops
in it. Before doing that, make sure it's not
 *infinitely* 
 long! Your
program will utterly crash if it runs out of system stack space, which can
happen in a very deep or infinite recursion.
 



 Note: The compiler will now generate a warning when you disable
 
 loop\_checks
 
 . It is not advisable to disable the check unless you're
trying to debug something, since you can cause the server to hang. Generally
if you have a loop so long it can cause the regular loop checks to freak out,
you need to make a change to the loop behavior anyway.
 




---
map\_format var (world)
-------------------------




**See also:** 


[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Topdown maps](#/{notes}/topdown) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 

[Understanding the renderer](#/{notes}/renderer) 













**Default value:** 


 TOPDOWN\_MAP
 



**Possible values:** 


* TOPDOWN\_MAP
* ISOMETRIC\_MAP
* SIDE\_MAP
* TILED\_ICON\_MAP





 This value says how the world will display maps. In a normal overhead
tiled map the value is
 
 TOPDOWN\_MAP
 
 for the top-down format. For older
games that predate this feature, the value is
 
 TILED\_ICON\_MAP
 
 .
 



 If you use a map format other than top-down, the HUD will still use a
tile format like it would in top-down display. HUD objects are not projected
into whatever map\_format you use and they are not affected by changing
client.dir. The size of the HUD is rounded up to the nearest number of full
screen tiles; the size of each tile is defined by world.icon\_size.
 


### 
 Top-down format


 (See more at
[Topdown maps](#/{notes}/topdown) 
 .)
 
 This is the default map format. Icons are drawn in a tile form and viewed
from overhead. In this layout, the layer assigned to each atom is very
important. The number of tiles shown is set by client.view or world.view.
 



 Because this format is familiar and easy to understand, it is the default
setting. Most of the vars related to maps and atoms are designed and
documented with this format in mind.
 


### 
 Tiled icon format


 (See more at
 [Tiled icons](#/{notes}/tiled-icons) 
 .)

In BYOND 4.0 a new feature was introduced for using "big" icons, bigger than
the standard tile size, by splitting them up into states like "0,0", "1,0",
and so on. This functionality is no longer needed since BYOND now has the
ability to display icons in their natural size. Some games that were designed
before this, however, may still need to make use of this splitting feature
that breaks icons into smaller tile-sized pieces.

When an icon is broken into chunks, each state in the icon is given a
thumbail version of the full image, and then new states are added to show
each chunk. For instance if world.icon\_size is the default 32×32, and
the icon is 64×64, then the "door" state would become a thumbnail of
the full door image while "door 0,0" (the lower left corner), "door 1,0",
"door 0,1", and "door 1,1" were created to show each smaller section of the
image. If the default "" state is broken into chunks, those chunks are just
named "0,0" and so on without a space.

This format is deprecated. It exists to support older games and allow them to
be compiled without causing them to break, until they can be redesigned for
one of the newer formats.
 ### 
 Isometric format


 (See more at
 [Isometric maps](#/{notes}/isometric) 
 .)
 
 If map\_format is set to
 
 ISOMETRIC\_MAP
 
 , the map is displayed in
isometric form. Isometric tiles are displayed in a foreshortened diagonal
perspective, where the "north" direction actually displays as northeast on
the player's screen, and "east" shows up as southeast. The value of
 
 client.view
 
 or
 
 world.view
 
 is used to calculate the
 *minimum* 
 number of tiles to display, and extra tiles to each side will
be shown to fill in the corners.
 



 In an isometric map, the tile width set in world.icon\_size is the most
important factor. This should be a multiple of 4 for best results. The
minimum tile height is half that value, and any extra height is used to show
vertical structures that "stick up" off the map surface. When you draw an
isometric tile icon, start with a flattened diamond shape at the bottom that
is only half as high as it is wide.
 



 Isometric maps behave differently during drawing than top-down maps. In
isometric, tiles that are nearer to the viewer's perspective are drawn in
front of tiles farther back, regardless of layer. Layers only count within an
individual tile. This means that if you want to have a vertical structure
"stick up" to partially hide something behind it, the icon sticking up should
always be on a tile forward from the one being partly covered. E.g. if you
have a wall taking up part of your tile, it needs to be at the "back" end of
the tile to properly hide anything on the tiles behind it.
 



 The
 
 pixel\_x
 
 and
 
 pixel\_y
 
 values,
 
 step\_x
 
 and
 
 step\_y
 
 values, and the gliding that happens when moving between
tiles, are based on the width set by
 
 world.icon\_size
 
 . If you set
 
 world.icon\_size="64x128"
 
 to show tall buildings, only the 64 matters
for pixel offsets. Use
 
 pixel\_w
 
 and
 
 pixel\_z
 
 to adjust the
position of atoms (or the client) horizontally or vertically without respect
to
 
 client.dir
 
 or the map format.
 



 Note: Offsets for x and y also affect the layering order used to draw
the icons. Any object with a pixel offset onto another tile is considered
part of whichever tile is closer.
 



 If you use an icon wider than one tile, the "footprint" of the isometric
icon (the actual map tiles it takes up) will always be a square. That is, if
your normal tile size is 64 and you want to show a 128x128 icon, the icon is
two tiles wide and so it will take up a 2×2-tile area on the map. The
height of a big icon is irrelevant--any excess height beyond width/2 is used
to show vertical features. To draw this icon properly, other tiles on that
same ground will be moved behind it in the drawing order.
 



 One important warning about using big icons in isometric mode is that you
should only do this with dense atoms. If part of a big mob icon covers the
same tile as a tall building for instance, the tall building is moved back
and it could be partially covered by other turfs that are actually behind it.
A mob walking onto a very large non-dense turf icon would experience similar
irregularities.
 


### 
 Side-view format


 (See more at
 [Side-view maps](#/{notes}/side) 
 .)
 
 The
 
 SIDE\_MAP
 
 format is like a cross between
 
 TOPDOWN\_MAP
 
 and
 
 ISOMETRIC\_MAP
 
 . It looks very similar to a top-down view but it is
intended for more of a 3/4 perspective, where tiles lower on the screen are
considered closer to the viewer. Because this impacts the way layers work,
most of the layering behavior is the same as with isometric.
 



 In a 3/4 perspective the tiles are often foreshortened, so pixel offsets
are adjusted to account for this. For example, you may set
 
 world.icon\_size
 
 to
 
 "32x24"
 
 , but the tile is considered to be
a perfect square if you look at it from the top down. Because the width is 32
pixels, the virtual height is also 32, so if you use pixel\_y=32 the atom will
appear one tile further back than it normally is. (This adjustment doesn't
affect screen objects or
 
 pixel\_w
 
 /
 
 pixel\_z
 
 .)
 



 Changing
 
 client.dir
 
 preserves the same tile size regardless of
orientation.
 




---


map\_cpu var (world)
----------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[tick\_lag var (world)](#/world/var/tick_lag) 

[tick\_usage var (world)](#/world/var/tick_usage) 

[Tick proc (world)](#/world/proc/Tick) 






 This is the percentage of a server tick that the server spends processing
information about the map to send to players. A value of 0 would indicate very
little cpu usage. A value of 100 would indicate full cpu usage, which means
that the server cannot complete all the necessary computations during a tick to
finish in time for the next tick. In this case, timed events (such as sleep)
may take longer than requested.
 




---
maxx var (world)
------------------




**See also:** 


[area var (world)](#/world/var/area) 

[maxy var (world)](#/world/var/maxy) 

[maxz var (world)](#/world/var/maxz) 

[turf var (world)](#/world/var/turf) 

[Map](#/map) 








**Default value:** 


 0
 


 The world map is a three-dimensional block of turfs with coordinates
ranging from (1,1,1) to (maxx,maxy,maxz). If set at compile time, it
provides a lower bound and will be increased as needed by the map files.
 



 The default value is 0, indicating no map. If any of the map dimensions
are set to non-zero values at compile time, the others will default to 1.
 



 New territory created by increasing the map boundaries is filled in with
the default turf and area (world.turf, and world.area).
 




---
maxy var (world)
------------------




**See also:** 


[area var (world)](#/world/var/area) 

[maxx var (world)](#/world/var/maxx) 

[maxz var (world)](#/world/var/maxz) 

[turf var (world)](#/world/var/turf) 







**Default value:** 


 0
 


 The world map is a three-dimensional block of turfs with coordinates
ranging from (1,1,1) to (maxx,maxy,maxz). If set at compile time, it
provides a lower bound and will be increased as needed by the map files.
 



 The default value is 0, indicating no map. If any of the map dimensions
are set to non-zero values at compile time, the others will default to 1.
 



 New territory created by increasing the map boundaries is filled in with
the default turf and area (world.turf, and world.area).
 




---
maxz var (world)
------------------




**See also:** 


[area var (world)](#/world/var/area) 

[maxx var (world)](#/world/var/maxx) 

[maxy var (world)](#/world/var/maxy) 

[turf var (world)](#/world/var/turf) 







**Default value:** 


 0
 


 The world map is a three-dimensional block of turfs with coordinates
ranging from (1,1,1) to (maxx,maxy,maxz). If set at compile time, it
provides a lower bound and will be increased as needed by the map files.
 



 The default value is 0, indicating no map. If any of the map dimensions
are set to non-zero values at compile time, the others will default to 1.
 



 New territory created by increasing the map boundaries is filled in with
the default turf and area (world.turf, and world.area).
 




---
mob var (world)
-----------------




**See also:** 


[New proc (client)](#/client/proc/New) 




**Default value:** 


 /mob.
 


 When a player connects to the world, the world is searched for a mob with
the player's key. If one is found, the player is connected to that mob. If
none is found, a new mob of type world.mob is created and the player is
connected to this new mob.
 



 The default value is /mob. Setting world.mob to 0 prevents the creation
of default mobs.
 


### 
 Example:



 world
 mob = /mob/newbie

mob/newbie
 Login()
 src << "Welcome, [name]."
 ..()
 

 This example will connect new players to mobs of type /mob/newbie. They
are welcomed when they connect.
 




---
movement\_mode var (world)
----------------------------




**See also:** 


[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[Enter proc (atom)](#/atom/proc/Enter) 

[Exit proc (atom)](#/atom/proc/Exit) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Pixel movement](#/{notes}/pixel-movement) 

[Gliding](#/{notes}/gliding) 










**Possible values:** 



 LEGACY\_MOVEMENT\_MODE
 
 : Old BYOND behavior regarding pixel movement and turf contents (see below)
 

 TILE\_MOVEMENT\_MODE
 
 : All atoms are locked to the tile grid
 

 PIXEL\_MOVEMENT\_MODE
 
 : All movable atoms can use pixel movement unless otherwise specified (see below), but legacy behavior for turf contents is ignored
 





**Default value:** 


 LEGACY\_MOVEMENT\_MODE
 


 Controls how movement works on the map.
 




 TILE\_MOVEMENT\_MODE
 
 allows you to easily discard any and all pixel
movement, so if step\_x or step\_y coordinates or unexpected atom bounds were
loaded from a savefile, for instance, they would be eliminated. If you use any
other movement mode, you can give an atom the
 [TILE\_MOVER](#/atom/var/appearance_flags) 
 flag and it will
behave as if it were in this mode, while other atoms are free to do their own
thing.
 




 LEGACY\_MOVEMENT\_MODE
 
 exists to distinguish between old and new
movement behavior. In older versions of BYOND before pixel movement, turfs
took their contents into consideration by default in Enter() and Exit(). This
doesn't really make sense for newer games, so in any other movement mode the
turf behavior will ignore its contents. mob.Cross() is also affected, since
it would return 0 by default in legacy mode when both mobs were dense; now
by default it checks
 
 mob.group
 
 .
 




---
name var (world)
------------------




**Default value:** 


 The <world> part of the <world>.dmb file.
 


 This is the name of the world.
 


### 
 Example:



 world
 name = "The Void"
 


---
params var (world)
--------------------




**See also:** 


[list associations](#/list/associations) 

[params2list proc](#/proc/params2list) 

[startup proc](#/proc/startup) 






**Default value:** 


 null
 


 This is a list of parameters passed to the world from the command-line
-params option when the server was started. The parameter text is passed
through params2list() to generate the world.params list.
 


### 
 Example:



 world/New()
 var/p
 if(params.len) world.log << "Command-line parameters:"
 for(p in params)
 world.log << "[p] = [params[p]]"
 

 This example displays the value of each parameter.
 




---
port var (world)
------------------




**See also:** 


[OpenPort proc (world)](#/world/proc/OpenPort) 

[address var (world)](#/world/var/address) 

[reachable var (world)](#/world/var/reachable) 

[visibility var (world)](#/world/var/visibility) 






 This is the network port of the world. If the world does not have an
open network port, this is 0.
 




---
process var (world)
---------------------




**See also:** 


[byond\_version var (world)](#/world/var/byond_version) 

[system\_type var (world)](#/world/var/system_type) 

[shell proc](#/proc/shell) 





 This read-only variable indicates the ID of the server's process on the
system running it. The result is a number, unless for some unexpected
reason the number won't fit in a
 
 num
 
 type, in which case it will
be text. (In practice it should always be a number.)
 




---
realtime var (world)
----------------------




**See also:** 


[time var (world)](#/world/var/time) 

[timeofday var (world)](#/world/var/timeofday) 

[time2text proc](#/proc/time2text) 





 This is the time (in 1/10 seconds) since 00:00:00 GMT, January 1, 2000
(also known as the BYOND era).
 



 Because this is a large number, BYOND's number system isn't capable of
enough precision to deliver the exact number of 1/10 second ticks. It usually
rounds off to the nearest several seconds. For more accurate readings use
 `world.timeofday` 
 .
 




---
reachable var (world)
-----------------------




**See also:** 


[port var (world)](#/world/var/port) 

[OpenPort proc (world)](#/world/proc/OpenPort) 




 Returns 1 if the world is currently hosted and the port can be reached by
players (as determined by the BYOND hub), 0 if not.
 



 If the port is not reachable, there may be a brief period during which the
hub is still attempting to make contact; during that time the port is assumed
to be reachable. Currently, the reachability test times out and fails after
30 seconds.
 




---
sleep\_offline var (world)
----------------------------




**Default value:** 


 0
 


 Setting this to 1 causes the world to be suspended when there are no
players, even if you have sleeping procs waiting to happen. The default
value is 0, which means the server will only sleep if there are no players
and no procs waiting to happen. The main purpose of the variable is to save
the cpu from doing work when there is nobody around to appreciate it. On the
other hand, that doesn't give the poor NPC's a break from the nasty humans.
 




---
status var (world)
--------------------




**See also:** 


[hub var (world)](#/world/var/hub) 

[game\_state var (world)](#/world/var/game_state) 

[visibility var (world)](#/world/var/visibility) 





 This is a short text string used in BYOND hub to describe the state of a
game in progress. For example, you might want to indicate if new players
will be able to actively play, or whether they would have to join as
spectators.
 


### 
 Example:



 world
 status = "accepting players"
mob/verb/start\_game()
 world.status = "accepting spectators"
 //...
 


---
system\_type var (world)
--------------------------




**See also:** 


[byond\_version var (world)](#/world/var/byond_version) 

[process var (world)](#/world/var/process) 

[shell proc](#/proc/shell) 





 This variable indicates the operating system type at run-time. It will be
one of the following constants:
 


* MS\_WINDOWS
* UNIX




---
tick\_lag var (world)
-----------------------




**See also:** 


[fps var (world)](#/world/var/fps) 

[tick\_lag var (client)](#/client/var/tick_lag) 

[tick\_usage var (world)](#/world/var/tick_usage) 

[sleep proc](#/proc/sleep) 







**Default value:** 


 1
 


 This is the smallest unit of time (one server tick) measured in 1/10
seconds. The duration of events that take some finite amount of time (like
sleep) will be rounded to a whole number of ticks.
 



 Players are limited to one command (including movements) per server tick,
so this value can be used to adjust the responsiveness of the game. If the
network is too slow to keep up with players, their commands will get queued
up, which can be annoying when trying to move. In this case, tick\_lag
should be increased so that the stored up movement commands are discarded.
On the other hand, if you have a very fast network, you may wish to decrease
tick\_lag to speed up the response time to player commands.
 



 Often it is more convenient to set world.fps instead of world.tick\_lag,
since fps (frames per second) is an easier way to think of server ticks.
world.tick\_lag is 10 / world.fps and vice-versa, so a tick\_lag of 0.25 is
equal to 40 fps.
 



 If you set client.tick\_lag or client.fps to a value other than 0, you can
make the client tick at a different (usually faster) rate.
 




---
tick\_usage var (world)
-------------------------




**See also:** 


[cpu var (world)](#/world/var/cpu) 

[tick\_lag var (world)](#/world/var/tick_lag) 

[Tick proc (world)](#/world/proc/Tick) 





 This is the approximate percentage of the server tick that has been used
already. A value under 100 means there's time to do more calculations, which
can include any pending procs that are still waiting to run on this tick.
When the value is over 100, the tick is running long and your world will
experience lag.
 



 Keep in mind that sending maps to clients is the last thing that happens
during a tick, except for handling any events such as player commands that
might arrive before the next tick begins. Therefore in a verb,
 
 tick\_usage
 
 might have a higher value than you would expect to see in
a proc that loops and sleeps.
 




---
time var (world)
------------------




**See also:** 


[realtime var (world)](#/world/var/realtime) 

[tick\_lag var (world)](#/world/var/tick_lag) 




 This gives the amount of time (in 1/10 seconds) that the world has been
running. In actual fact, it is the number of server ticks that have passed
multiplied by world.tick\_lag. Therefore if the server sleeps (when no
players are connected) this time is not counted. Also, if the server runs
overtime during a tick (because procs take longer than tick\_lag to finish)
this still only counts as one tick. This value is therefore a measure of
"game time" rather than real time.
 




---
timeofday var (world)
-----------------------




**See also:** 


[realtime var (world)](#/world/var/realtime) 

[time var (world)](#/world/var/time) 

[time2text proc](#/proc/time2text) 





 This is the time (in 1/10 seconds) since 00:00:00 GMT today. It is
basically identical to
 `world.realtime` 
 but doesn't include any
information about the date. This is a much smaller number; hence it is more
accurate.
 




---
timezone var (world)
----------------------




**See also:** 


[realtime var (world)](#/world/var/realtime) 

[timeofday var (world)](#/world/var/timeofday) 

[timezone var (client)](#/client/var/timezone) 

[time2text proc](#/proc/time2text) 






 This is the time offset from UTC, in hours, for the world's time zone. It
can be used in the
 
 time2text()
 
 proc, although it is the default time
zone for that proc.
 




---
turf var (world)
------------------




**Default value:** 


 /turf.
 


 This is the default turf type to be placed on the map wherever no turf is
specified. A value of 0 turns off the default turf.
 




---
url var (world)
-----------------




**See also:** 


[address var (world)](#/world/var/address) 



 This is the full network address of the world. (For example,
byond://dan.byond.com:6005.)
 




---
version var (world)
---------------------




**See also:** 


[hub var (world)](#/world/var/hub) 




**Default value:** 


 0
 


 If you are distributing your game to players, you can use this variable
to automatically notify them of new releases. To do so, you will first need
to set
 [`world.hub`](#/world/var/hub)
 to the hub
path of your game. You can then advertise the current version by
configuring that value in your
 [hub console](https://secure.byond.com/members/?command=edit_hub) 
 .
 



 When players boot up an outdated version of your game (as indicated by
comparing
 `world.version` 
 with the version advertised by BYOND
hub), they will be notified of the new release.
 




---
view var (world)
------------------




**See also:** 


[lazy\_eye var (client)](#/client/var/lazy_eye) 

[show\_map var (client)](#/client/var/show_map) 

[view proc](#/proc/view) 

[view var (client)](#/client/var/view) 







**Default value:** 


 5
 



**Possible values:** 


 -1 to 34 or "WIDTHxHEIGHT"
 


 This is the default map viewport range. The default value of 5 produces an
11x11 viewport. A value of -1 turns off the map display altogether. The client may automatically
scale down icons in order to conveniently fit the map on the player's screen.
 



 For non-square views, you can assign this to a text string of the form
"WIDTHxHEIGHT". For example, "11x11" is equivalent to a view depth of 5, but
you could make it wider like this: "13x11".
 



 This setting also affects the default range of the
 `view()` 
 ,
 `oview()` 
 ,
 `range()` 
 , and
 `orange()` 
 procedures.
 



 If the entire map is small enough to fit on one screen 
(arbitrarily defined to be 21x21 or less),
the default
 `view` 
 is automatically adjusted to fit the map. In
this case,
 `client.lazy_eye` 
 is also automatically turned on by
default, since you probably don't want the map to scroll around.
 




---
visibility var (world)
------------------------




**See also:** 


[OpenPort proc (world)](#/world/proc/OpenPort) 

[hub var (world)](#/world/var/hub) 





**Default value:** 


 1 (visible)
 


 This controls whether the world advertises itself in the
 [BYOND Hub](http://www.byond.com/games/) 
 when it has an open network
port for accepting players. The visibility of the world still depends on
whether any of the connected players has their location reporter turned on,
and that in turn relies on the pager being turned on.
 




---
Special notes
---------------



 This section of the reference should help explain some concepts that
may be harder to understand or that can use more clarification.
 





**Language features** 



[Numbers](#/{notes}/numbers) 

[Regular expressions](#/{notes}/regex) 

[Unicode](#/{notes}/Unicode) 




**Icons** 


[Big icons](#/{notes}/big-icons) 

[Tiled icons](#/{notes}/tiled-icons) 



**Map formats** 


[Topdown maps](#/{notes}/topdown) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 





**Movement** 



[Gliding](#/{notes}/gliding) 

[Pixel movement](#/{notes}/pixel-movement) 




**Display** 



[Understanding the renderer](#/{notes}/renderer) 

[HUD / screen objects](#/{notes}/HUD) 

[Color matrix](#/{notes}/color-matrix) 

[Filter effects](#/{notes}/filters) 

[Particle effects](#/{notes}/particles) 


[Color gradient](#/{notes}/color-gradient) 

[Generators](#/{notes}/generators) 




[Projection matrix](#/{notes}/projection-matrix) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 












---
BACKGROUND\_LAYER
-------------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 









 This is mostly no longer needed. A negative value for plane is the
preferred way to do show objects in the background. It can still be used
however when you want to rearrange objects in the same plane when using
 [PLANE\_MASTER](#/atom/var/appearance_flags) 
 for visual
effects.
 




 BACKGROUND\_LAYER
 
 is a special high value that can be added to the
regular layer of any atom.
 



 The purpose of this value is to make an atom appear below any regular
atoms, even if they share the same plane. In an isometric map for instance,
HUD objects will always appear above the map, but makeing a HUD object appear
behind the map was basically impossible without this feature until
 
 plane
 
 was implemented.
 



 When using this special layer, it should be added to the layer an atom
normally uses. For instance an obj should have a layer of
 
 BACKGROUND\_LAYER
+ OBJ\_LAYER
 
 .
 



 This can be mixed with
 
 TOPDOWN\_LAYER
 
 and
 
 EFFECTS\_LAYER
 
 ,
but it will take precedence over both. Anything with
 
 BACKGROUND\_LAYER
 
 will always appear below anything without it on the same plane.
 



 Images or overlays with
 
 FLOAT\_LAYER
 
 can be left alone. They will
automatically have the same layer as whatever atom they are attached to.
 




---
Big icons
-----------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[Blend proc (icon)](#/icon/proc/Blend) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Tiled icons](#/{notes}/tiled-icons) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 










 BYOND allows you to use icons that are not the same size as the tile size
defined in world.icon\_size. These icons can be manipulated with the /icon datum
using their raw, native size, and shown on the map in full size. To use the old
behavior where an atom can display only an icon of the normal tile size, use
the TILED\_ICON\_MAP value for map\_format instead.
 



 When you use an icon of non-standard size on an atom, the icon is "anchored"
to the southwest corner of the atom. If you are using a top-down view
(world.map\_format=TOPDOWN\_MAP), the icon will appear to spread out further to
the east and north. In an isometric map (world.map\_format=ISOMETRIC\_MAP), the
icon will cover additional tiles north and east as well. The "footprint" of an
isometric icon--the actual map tiles it covers--is always square, so if your
tile size is 64x64 and you use a 128x64 icon, the 128-pixel width means the
icon will cover a 2x2 section of map tiles.
 



 It is important to remember that using a big icon is a visual effect
 *only* 
 . It will not affect how the atom bumps into other atoms or
vice-versa.
 



 Big icons will affect layering--the order in which icons are drawn. In
general, because a big icon is covering more than one tile of the map, it will
try to draw above any other tiles in that space that are on the same layer.
This way, you can set a turf to use a big icon without having to change the
turfs to the north and east. If an atom has a big icon, any overlays and
underlays attached to it will be pulled forward as well, so they will draw in
front of anything on their same layer. In isometric mode this is about the same,
except that the layer isn't that important--anything in the way will just be
moved back behind the big icon.
 



 Note: Big overlays will not "pull forward" on their own. If the main atom
uses a single-tile icon, a big overlay attached to it will not try to draw in
front of other icons on the same layer. This is so that name labels, health
bar overlays, etc. will not cause any odd behavior. To be safe, you should
always specify a layer when adding an overlay.
 



 In isometric mode, layering is affected by the "distance" between the atom
and the viewer, so putting a regular-sized icon and part of a big icon on the
same tile could cause layering oddities. Tiles that are covered by a big icon
will tend to be drawn behind the big icon as mentioned above. For this reason,
any atoms whose icons cover more than one tile (the extra height of an
isometric icon doesn't count) should always be dense, and you should block
movement onto any tile covered by them.
 



 When manipulating icons with the /icon datum, you can still use Blend() to
combine icons of different sizes. By default, the icons will be lined up at
their southwest corners. You can change the position at which the second icon
is blended.
 




---
Color gradient
----------------




**See also:** 


[gradient proc](#/proc/gradient) 

[color var (atom)](#/atom/var/color) 

[Particle effects](#/{notes}/particles) 

[Color space](#/{{appendix}}/color-space) 






 A color gradient is a special list that defines a range of colors that you
can smoothly interpolate between. A simple example is a gradient from red to
white:
 


### 
 Example:



 list("red", "white")
// OR
list(0, "red", 1, "white")
 

 Applying a number like 0.2 to this gradient would give you a color that's
20% of the way from red to white. More complex gradients however are also
possible.
 



 The format of a gradient is a list that contains a number (the position
along the gradient, from 0 to 1 unless you use values outside that range)
followed by a color. You can have as complex a gradient as you like. If you
reuse the same number twice in a row, the gradient will have a sudden color
change at that point.
 



 It is also possible to skip numbers or colors, and they will be filled in
automatically with the previous number or color. The exceptions are at the
beginning and ends of the list; at the end of the gradient, the last color is
assigned a number 1 by default, and the first is assigned 0. If you skip
colors at the beginning, they will be filled in with the first color you use.
 



 Include "loop" anywhere in the list to make this a looped gradient. If you
don't, any numbers outside the gradient's range will be clamped to that range.
E.g., in a normal gradient ranging from 0 to 1, a number of 1.2 is
interpreted as 1 without a loop and 0.2 with a loop.
 



 Here are some more examples:
 


### 
 Example:



 // color wheel; ranges 0 to 6 and loops
list(0, "#f00", 1, "#ff0", 2, "#0f0", 3, "#0ff", 4, "#00f", 5, "#f0f", 6, "#f00", "loop")

// 10% each red, yellow, green, blue, with a 20% transition zone between each
// notice no color follows 0.4 or 0.7, so the previous color is used
list(0.1, "#f00", 0.3, "#ff0", 0.4, 0.6, "#008000", 0.7, 0.9, "#00f")

// green and black stripes
list(0.5, "#008000", 0.5, "#000000", "loop")
 

 You can also include "space" in the list, and give it an associated value
that describes the color space this gradient uses to interpolate between
colors. For instance,
 
 "space"=COLORSPACE\_HSL
 
 will use HSL
interpolation instead of the default RGB. See
 [Color space](#/{{appendix}}/color-space) 
 for more information.
 


### 
 Example:



 // color wheel with a different color space
list(0, "#f00", 3, "#0ff", 6, "#f00", "loop", "space"=COLORSPACE\_HSLA)
 

 Currently, color gradients are only used by particle effects and the
 [gradient
 
 proc](#/proc/gradient) 
 . With particles, if you use
a gradient the particle's color is given as a number, and that number is used
to look up its real color from the gradient. The number can change over time,
thus changing the particle's color.
 




---
Color matrix
--------------




**See also:** 


[color var (atom)](#/atom/var/color) 

[color var (client)](#/client/var/color) 

[MapColors proc (icon)](#/icon/proc/MapColors) 





 A color matrix is used to transform colors, in the same way that a matrix
represented by the
 
 /matrix
 
 datum is used to transform 2D coordinates.
A transformation matrix is 3x3, of which only 6 values are needed because the
last column is always the same. A color matrix, because it transforms four
different numbers instead of two, is 5x5.
 



```
                |rr rg rb ra 0|
                |gr gg gb ga 0|
[r g b a 255] x |br bg bb ba 0| = [r' g' b' a' 255]
                |ar ag ab aa 0|
                |cr cg cb ca 1|

```


 In easier-to-understand terms, this is how the result is calculated:
 



 new\_red = red \* rr + green \* gr + blue \* br + alpha \* ar + 255 \* cr
new\_green = red \* rg + green \* gg + blue \* bg + alpha \* ag + 255 \* cg
new\_blue = red \* rb + green \* gb + blue \* bb + alpha \* ab + 255 \* cb
new\_alpha = red \* ra + green \* ga + blue \* ba + alpha \* aa + 255 \* ca
 

 It is helpful to think of each row in the matrix as what each component of
the original color will become. The first row of the matrix is the rgba value
you'll get for each unit of red; the second is what each green becomes, and so
on.
 



 Because the fifth column of the matrix is always the same, only 20 of the
values need to be provided. You can use a color matrix with atom.color or
client.color in any of the following ways:
 




 RGB-only (9 to 12 values)
 

 list(rr,rg,rb, gr,gg,gb, br,bg,bb, cr,cg,cb)
 

 RGBA (16 to 20 values)
 

 list(rr,rg,rb,ra, gr,gg,gb,ga, br,bg,bb,ba, ar,ag,ab,aa, cr,cg,cb,ca)
 

 Row-by-row (3 to 5
 
 rgb()
 
 values, or null to use the default row)
 

 list(red\_row, green\_row, blue\_row, alpha\_row, constant\_row)
 


 Reading a color var that has been set to a matrix will return the full
20-item list, where every 4 items represent a row in the matrix (without the
fifth column).
 



 In the
 
 MapColors()
 
 icon proc, the values are sent as arguments,
not as a list.
 




---
EFFECTS\_LAYER
----------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/TOPDOWN_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[Understanding the renderer](#/{notes}/renderer) 









 This is mostly no longer needed. A negative value for plane is the
preferred way to do show objects in the background. It can still be used
however when you want to rearrange objects in the same plane when using
 [PLANE\_MASTER](#/atom/var/appearance_flags) 
 for visual
effects.
 




 EFFECTS\_LAYER
 
 is a special high value that can be added to the
regular layer of any atom.
 



 The purpose of this value is to make an atom appear above any regular
atoms. For instance, in an isometric map if you want to display a character's
name below them, it does not make much sense to have nearer objects cover up
that name, so you can tell the name overlay to use
 
 EFFECTS\_LAYER +
MOB\_LAYER
 
 and it will show up on top of all the normal icons on the map.
This has been somewhat obviated by
 
 plane
 
 but may still be useful in
some cases.
 



 When using this special layer, it should be added to the layer an atom
normally uses. For instance an obj should have a layer of
 
 EFFECTS\_LAYER +
OBJ\_LAYER
 
 .
 



 This can be mixed with
 
 TOPDOWN\_LAYER
 
 , in non-topdown map formats.
Anything in
 
 TOPDOWN\_LAYER
 
 will display on top of
 
 EFFECTS\_LAYER
 
 , and
 
 TOPDOWN\_LAYER + EFFECTS\_LAYER
 
 will be
above both.
 



 This can also be mixed with
 
 BACKGROUND\_LAYER
 
 , which takes priority
over everything else.
 



 Images or overlays with
 
 FLOAT\_LAYER
 
 can be left alone. They will
automatically have the same layer as whatever atom they are attached to.
 




---
Filter effects
----------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[filter proc](#/proc/filter) 

[animate proc](#/proc/animate) 

[Understanding the renderer](#/{notes}/renderer) 







 Filters are a way of adding special effects to an icon, or a group of icons
(see
 
 KEEP\_TOGETHER
 
 in
 [appearance\_flags](#/atom/var/appearance_flags) 
 ), by
post-processing the image. A filter object describes a specific form of image
processing, like for instance a blur or a drop shadow. Filters can be added or
removed at will, and can even be animated.
 



 A filter is created by using the
 [filter proc](#/proc/filter) 
 like
so:
 



 // halo effect
mob.filters += filter(type="drop\_shadow", x=0, y=0,\
 size=5, offset=2, color=rgb(255,255,170))
 

 These are the filters currently supported:
 


* [Alpha mask](#/{notes}/filters/alpha)
* [Angular blur](#/{notes}/filters/angular_blur)
* [Bloom](#/{notes}/filters/bloom)
* [Color matrix](#/{notes}/filters/color)
* [Displacement map](#/{notes}/filters/displace)
* [Drop shadow](#/{notes}/filters/drop_shadow)
* [Gaussian blur](#/{notes}/filters/blur)
* [Layering (composite)](#/{notes}/filters/layer)
* [Motion blur](#/{notes}/filters/motion_blur)
* [Outline](#/{notes}/filters/outline)
* [Radial blur](#/{notes}/filters/radial_blur)
* [Rays](#/{notes}/filters/rays)
* [Ripple](#/{notes}/filters/ripple)
* [Wave](#/{notes}/filters/wave)




---
Alpha mask filter
-------------------




**See also:** 


[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 





 Format:
 

 filter(type="alpha", ...)
 



 Args:
 

 x: Horizontal offset of mask (defaults to 0)
 

 y: Vertical offset of mask (defaults to 0)
 

 icon: Icon to use as a mask
 

 render\_source:
 
 render\_target
 
 to use as a mask
 

 flags: Defaults to 0; use see below for other flags
 


 Uses an icon or render target as a mask over this image. Every pixel that
is transparent in either the image or the mask, is transparent in the result.
 



 The
 
 x
 
 and
 
 y
 
 values can move the mask from its normal
position. By default, the mask is centered over the center of the image.
 



 The
 
 MASK\_INVERSE
 
 flag will invert the alpha mask so that opaque
areas in the mask become transparent, and vice-versa. There is also a
 
 MASK\_SWAP
 
 flag which treats the source image as the mask and
vice-versa, which might be useful for some effects.
 



 Note: Unlike many other filters, this filter
 **is** 
 taken into account
for mouse-hit purposes.
 




---
Angular blur filter
---------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Motion blur (filters)](#/{notes}/filters/motion_blur) 






 Format:
 

 filter(type="angular\_blur", ...)
 



 Args:
 

 x: Horizontal center of effect, in pixels, relative to image center
 

 y: Vertical center of effect, in pixels, relative to image center
 

 size: Amount of blur (defaults to 1)
 


 Blurs the image by a certain amount in a circular formation, as if the
image is spinning. The size of the blur can roughly be thought of in "degrees"
worth of blur. As the distance from the center increases, the blur becomes
more noticeable since the same amount of angular motion has to travel farther
along a circle.
 



 Typically this blur is used with an entire plane, but it could be used to
give a sense of motion blur to a spinning object.
 



 Note: Large blurs will look worse toward the edges due to limited sampling.
Loss of accuracy will appear where
 
 size
 
 × distance is greater
than about 300. You can increase accuracy by breaking up large sizes into
multiple filter passes with differing sizes. The blur used is Gaussian, so
combining blur sizes A and B will give a total size of
sqrt(A
 2 
 +B
 2 
 ).
 




---
Bloom filter
--------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 





 Format:
 

 filter(type="bloom", ...)
 



 Args:
 

 threshold: Color threshold for bloom
 

 size: Blur radius of bloom effect (see Gaussian blur)
 

 offset: Growth/outline radius of bloom effect before blur
 

 alpha: Opacity of effect (default is 255, max opacity)
 


 Post-processing effect that makes bright colors look like they're a strong
light source, spreading their light additively to other nearby pixels. This is
a complex effect that involves multiple shader passes. For both performance and
visual reasons, it is usually best applied to an entire plane rather than to
individual objects.
 



 The color
 
 threshold
 
 determines which pixels this effect applies to.
If any of the red, green, or blue components of the pixel are greater than the
same component for the threshold, that pixel will bloom. The blooming pixels
then have their colors spread outward to create a glow that gets added to the
original image.
 



 The
 
 offset
 
 and
 
 size
 
 parameters are used to control the
glow effect. They work the same as they do in the drop shadow filter:
 
 offset
 
 causes the light to grow outwards, and a blur of
 
 size
 
 is then applied to soften it. Often just using a blur alone will produce a
pleasing effect. By playing with these two values you can make the bloom effect
appear differently.
 



 The
 
 alpha
 
 value is applied to any light contributions from bloomed
pixels that get added to the original image, so values lower than 255 can make
the effect less pronounced. This can be very useful if you choose to animate
the filter.
 




---
Gaussian blur filter
----------------------




**See also:** 


[Motion blur (filters)](#/{notes}/filters/motion_blur) 

[Radial blur (filters)](#/{notes}/filters/radial_blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 







 Format:
 

 filter(type="blur", ...)
 



 Args:
 

 size: Amount of blur (defaults to 1)
 


 Blurs the image by a certain amount. The size of the blur can roughly be
thought of in "pixels" worth of blur.
 



 Note: Large blurs will result in reduced performance. The
highest size that can be handled easily in this filter is 6. Higher sizes
require multiple passes, although the filter will "cheat" and use low-quality
passes for much higher sizes.
 




---
Color matrix filter
---------------------




**See also:** 


[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 

[Color space](#/{{appendix}}/color-space) 






 Format:
 

 filter(type="color", ...)
 



 Args:
 

 color: A color matrix
 

 space: Value indicating color space: defaults to
 
 FILTER\_COLOR\_RGB
 



 Applies a color matrix to this image. Unlike with the atom.color var, you
can apply color conversions other than the regular RGBA color space, depending
on the value of
 
 space
 
 . See
 [Color
space](#/{{appendix}}/color-space) 
 for more information.
 




---
Displacement map filter
-------------------------




**See also:** 


[Alpha mask (filters)](#/{notes}/filters/alpha) 

[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 






 Format:
 

 filter(type="displace", ...)
 



 Args:
 

 x: Horizontal offset of map (defaults to 0)
 

 y: Vertical offset of map (defaults to 0)
 

 size: Maximum distortion, in pixels
 

 icon: Icon to use as a displacement map
 

 render\_source:
 
 render\_target
 
 to use as a displacement map
 


 Uses an icon or render target as a template for various warping effects on
the main image.
 



 In the displacement map, pixels that have a higher red component will make
the image appear to warp to the left, lower reds warp it to the right, and
gray (r=128) will cause no horizontal warping. The green component affects the
vertical: higher to warp upward, lower to warp downward. Transparent pixels in
the displacement map will have no effect.
 



 This can be used for very complex distortion, unlike other distortion
filters such as wave and ripple that are confined to specific equations.
 




---
Drop shadow filter
--------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Outline (filters)](#/{notes}/filters/outline) 





 Format:
 

 filter(type="drop\_shadow", ...)
 



 Args:
 

 x: Shadow horizontal offset (defaults to 1)
 

 y: Shadow horizontal offset (defaults to -1)
 

 size: Blur amount (defaults to 1; negative values create inset shadows)
 

 offset: Size increase before blur (defaults to 0)
 

 color: Shadow color (defaults to 50% transparent black)
 


 Applies a drop shadow to this image. This is a combination of multiple
filters, since it will apply an outline if
 
 offset
 
 is included, a
Gaussian blur to the shadow, and will underlay the shadow beneath the image.
 



 You can also think of this filter as an outer glow.
 



 If you use a
 
 size
 
 less than 0, the shadow will appear inside the
image instead. This would be an inset shadow, or inner glow.
 




---
Layering (composite) filter
-----------------------------




**See also:** 


[icon var (atom)](#/atom/var/icon) 

[render\_target var (atom)](#/atom/var/render_target) 





 Format:
 

 filter(type="layer", ...)
 



 Args:
 

 x: Horizontal offset of second image (defaults to 0)
 

 y: Vertical offset of second image (defaults to 0)
 

 icon: Icon to use as a second image
 

 render\_source:
 
 render\_target
 
 to use as a second image
 

 flags:
 
 FILTER\_OVERLAY
 
 (default) or
 
 FILTER\_UNDERLAY
 


 color:
 [Color](#/atom/var/color) 
 or color matrix to apply to second image
 

 transform:
 [Transform](#/atom/var/transform) 
 to apply to second image
 

 blend\_mode:
 [Blend mode](#/atom/var/blend_mode) 
 to apply to the top image
 


 Composites another image over or under this image. Using the
 
 FILTER\_OVERLAY
 
 flag, which is the default, puts the second image
on top of what's already here.
 
 FILTER\_UNDERLAY
 
 puts it underneath.
 



 The
 
 x
 
 and
 
 y
 
 values can move the mask from its normal
position. By default, the second image is centered over the center of the
first.
 



 The
 
 color
 
 ,
 
 transform
 
 , and
 
 blend\_mode
 
 vars are
available for convenience. Because the bottom image is drawn over a blank
background,
 
 blend\_mode
 
 is always applied to the top image. All of
the other vars apply to the second image being drawn.
 



 Note: Transforms use default bilinear scaling, since
 [PIXEL\_SCALE](#/atom/var/appearance_flags) 
 is not
available here.
 



 Note: Like most other filters, this filter is
 **not** 
 taken into account
for mouse-hit purposes. Any layered icons will be strictly visual.
 




---
Motion blur filter
--------------------




**See also:** 


[filters var (atom)](#/atom/var/filters) 

[Gaussian blur (filters)](#/{notes}/filters/blur) 





 Format:
 

 filter(type="motion\_blur", ...)
 



 Args:
 

 x: Blur vector on the X axis (defaults to 0)
 

 y: Blur vector on the Y axis (defaults to 0)
 


 Applies Gaussian blur in one direction only. The amount and direction are
both specified by
 
 x
 
 and
 
 y
 
 . The size of the blur is equal to
 
 sqrt(x\*x + y\*y)
 
 .
 



 See
 [Gaussian blur](#/{notes}/filters/blur) 
 for more information.
 




---
Outline filter
----------------




**See also:** 


[Drop shadow (filters)](#/{notes}/filters/drop_shadow) 




 Format:
 

 filter(type="outline", ...)
 



 Args:
 

 size: Width in pixels (defaults to 1)
 

 color: Outline color (defaults to black)
 

 flags: Defaults to 0 (see below)
 


 Applies an outline to this image.
 



 At larger sizes, the outline is less accurate and will take more passes to
produce. Performance and appearance are best at sizes close to 1 or less.
 




 flags
 
 can be a combination of the following values:
 




 0
 

 Ordinary outline
 

 OUTLINE\_SHARP
 

 Avoid antialiasing in the outline
 

 OUTLINE\_SQUARE
 

 Extend the outline sharply from corner pixels; for a box this will maintain a box shape without rounded corners
 



---
Radial blur filter
--------------------




**See also:** 


[Gaussian blur (filters)](#/{notes}/filters/blur) 

[Angular blur (filters)](#/{notes}/filters/angular_blur) 

[Motion blur (filters)](#/{notes}/filters/motion_blur) 






 Format:
 

 filter(type="radial\_blur", ...)
 



 Args:
 

 x: Horizontal center of effect, in pixels, relative to image center
 

 y: Vertical center of effect, in pixels, relative to image center
 

 size: Amount of blur per pixel of distance (defaults to 0.01)
 


 Blurs the image by a certain amount outward from the center, as if the
image is zooming in or out. As the distance from the center increases, the
amount of blurring increases, and near the center the blur is hardly visible
at all. The
 
 size
 
 value is smaller by default for this filter than it
is for other filters, since it's typically used with an entire plane where the
distance from the center can easily be several hundred pixels.
 



 Typically this blur is used with an entire plane.
 



 Note: Large blurs will look worse toward the edges due to limited sampling.
Loss of accuracy will begin when
 
 size
 
 × distance is greather
than 6. You can increase accuracy by breaking up large sizes into multiple
filter passes. The blur used is Gaussian, so combining blur sizes A and B will
give a total size of sqrt(A
 2 
 +B
 2 
 ).
 




---
Rays filter
-------------




 Format:
 

 filter(type="rays", ...)
 



 Args:
 

 x: Horiztonal position of ray center, relative to image center (defaults to 0)
 

 y: Vertical position of ray center, relative to image center (defaults to 0)
 

 size: Maximum length of rays (defaults to 1/2 tile width)
 

 color: Ray color (defaults to white)
 

 offset: "Time" offset of rays (defaults to 0, repeats after 1000)
 

 density: Higher values mean more, narrower rays (defaults to 10, must be whole number)
 

 threshold: Low-end cutoff for ray strength (defaults to 0.5, can be 0 to 1)
 

 factor: How much ray strength is related to ray length (defaults to 0, can be 0 to 1)
 

 flags: Defaults to
 
 FILTER\_OVERLAY | FILTER\_UNDERLAY
 
 (see below)
 


 Draws random rays that radiate outward from a center point. (That point may
be outside of the image.) As they move outward, their alpha value diminishes
linearly. These are meant to be animated. The
 
 offset
 
 value determines
the "time", where every jump of +1 can be a very different set of rays, and
every 1000 units this filter will repeat.
 



 The
 
 threshold
 
 value can be thought of as a way of culling
lower-strength rays. Ray strength is anywhere from 0 to 1 at any given angle,
but values below
 
 threshold
 
 may as well be 0. Values above that are
re-scaled into a range of 0 to 1.
 



 The
 
 factor
 
 parameter allows you to tie the ray's length to its
strength. At 0, the length of every ray is the same. At 1, the length ranges
from 0 to
 
 size
 
 . Generally speaking, the higher
 
 factor
 
 is,
the more the rays will appear to move outward as they strengthen and inward
as they weaken.
 



 Ray
 
 color
 
 can be provided as a matrix. Only the diagonal values of the
color matrix will be used, but using a matrix will allow you to set values
outside of the normal color range.
 




 flags
 
 can have the following values:
 




 0
 

 The rays are drawn alone, erasing the existing image (useful for some effects).
 

 FILTER\_OVERLAY
 

 The rays are overlaid on top of the existing image.
 

 FILTER\_UNDERLAY
 

 The rays are drawn underneath the existing image.
 

 FILTER\_OVERLAY | FILTER\_UNDERLAY
 

 Default. For plane masters, this will use the
 
 FILTER\_OVERLAY
 
 behavior and draw the rays over the plane, and for all other images it will default to
 
 FILTER\_UNDERLAY
 
 to draw the rays beneath them.
 



---
Ripple filter
---------------




**See also:** 


[Wave (filters)](#/{notes}/filters/wave) 




 Format:
 

 filter(type="ripple", ...)
 



 Args:
 

 x: Horiztonal position of ripple center, relative to image center (defaults to 0)
 

 y: Vertical position of ripple center, relative to image center (defaults to 0)
 

 size: Maximum distortion in pixels (defaults to 1)
 

 repeat: Wave period, in pixels (defaults to 2)
 

 radius: Outer radius of ripple, in pixels (defaults to 0)
 

 falloff: How quickly ripples lose strength away from the outer edge (defaults to 1)
 

 flags: Defaults to 0; use
 
 WAVE\_BOUNDED
 
 to keep distortion within the image
 


 Applies a ripple distortion effect to this image.
 



 This filter is meant to be animated. A good animation will typically start
at a
 
 radius
 
 of 0 and animate to a larger value, with
 
 size
 
 decreasing to 0.
 



 The
 
 falloff
 
 parameter can be tweaked to your liking. A value of 1
should look reasonably like ripples in water, with the inner ripples losing
strength. A value of 0 will cause no reduction in strength.
 



 The equation governing the ripple distortion is size × sin(2πr') ÷ (2.5 × falloff × r'
 2 
 + 1),
where r' = (radius - distance) ÷ repeat.
 



 Up to 10 ripples can be stacked together in a single pass of the filter, as
long as they have the same
 
 repeat
 
 ,
 
 falloff
 
 , and
 
 flags
 
 values. (See the wave filter for the
 
 WAVE\_BOUNDED
 
 flag.)
 




---
Wave filter
-------------




**See also:** 


[Ripple (filters)](#/{notes}/filters/ripple) 




 Format:
 

 filter(type="wave", ...)
 



 Args:
 

 x: Horiztonal direction and period of wave
 

 y: Vertical direction and period of wave
 

 size: Maximum distortion in pixels (defaults to 1)
 

 offset: Phase of wave, in periods (e.g., 0 to 1)
 

 flags: Defaults to 0; see below for other flags
 


 Applies a wave distortion effect to this image.
 



 The
 
 x
 
 and
 
 y
 
 parameters specify both the direction and
period of the wave; the period is
 
 sqrt(x\*x + y\*y)
 
 .
 



 This filter is meant to be animated, from whatever
 
 offset
 
 you want
to
 
 offset+1
 
 , and then repeating. With multiple waves, you can produce
a very convincing water effect.
 


### 
 Example



 #define WAVE\_COUNT 7
atom/proc/WaterEffect()
 var/start = filters.len
 var/X,Y,rsq,i,f
 for(i=1, i<=WAVE\_COUNT, ++i)
 // choose a wave with a random direction and a period between 10 and 30 pixels
 do
 X = 60\*rand() - 30
 Y = 60\*rand() - 30
 rsq = X\*X + Y\*Y
 while(rsq<100 || rsq>900) // keep trying if we don't like the numbers
 // keep distortion (size) small, from 0.5 to 3 pixels
 // choose a random phase (offset)
 filters += filter(type="wave", x=X, y=Y, size=rand()\*2.5+0.5, offset=rand())
 for(i=1, i<=WAVE\_COUNT, ++i)
 // animate phase of each wave from its original phase to phase-1 and then reset;
 // this moves the wave forward in the X,Y direction
 f = filters[start+i]
 animate(f, offset=f:offset, time=0, loop=-1, flags=ANIMATION\_PARALLEL)
 animate(offset=f:offset-1, time=rand()\*20+10)
 

 The equation governing the wave distortion is size × sin(2π(d - offset)),
where d is the number of wave periods' distance from the center along the x, y
direction.
 



 The
 
 WAVE\_SIDEWAYS
 
 flag will cause the distortion to be transverse
(perpendicular) to the wave instead of in the same direction as the wave. The
 
 WAVE\_BOUNDED
 
 flag limits the distortion to the confines of this image,
instead of lettings its pixels spill out a little further from the distortion
(and likewise, transparent pixels spill inward).
 



 Up to 10 waves can be stacked together in a single pass of the filter, as long as they
have the same
 
 WAVE\_BOUNDED
 
 flags.
 




---
Generators
------------




**See also:** 


[Particle effects](#/{notes}/particles) 

[generator proc](#/proc/generator) 

[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 






 A generator is an object that can produce a random number, vector (list of 3 numbers), color (as a text string), or color matrix (list of 20 numbers) in a specified range according to rules you set down. It is used primarily for particle effects, since it can run on the client.
 



 There are several types of generators:
 


* **Numbers:** 
 Generate a random real number.
* **Vectors:** 
 Generate a random vector.
* **Shapes:** 
 Generate a random vector within a specific shaped region.
* **Colors:** 
 Generate a random color or color matrix.



 Generators can also be chained together with math operators and some procs. The second value can be a regular value instead of a generator, so for instance you can multiply a vector by 2, or by a matrix to transform it.


| 
 Operators
  | 
 Action
  |
| --- | --- |
| 
 + - \* /
  | 
 Arithmetic operators. You can multiply a 3D vector by a color matrix (where red,green,blue in the matrix correspond to x,y,z) to do a 3D transform, or by a 2D matrix for a 2D transform.
  |
| 
 - (unary)
  | 
 Negate the value, same as multiplying by -1.
  |
| 
 turn(), generator.Turn()
  | 
 Rotate a vector clockwise in the XY plane.
  |




---


Gliding
---------




**See also:** 


[Pixel movement](#/{notes}/pixel-movement) 

[animate\_movement var (movable atom)](#/atom/movable/var/animate_movement) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

[glide\_size var (movable atom)](#/atom/movable/var/glide_size) 

[bound\_x var (movable atom)](#/atom/movable/var/bound_x) 

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[fps var (client)](#/client/var/fps) 















 Gliding is a "glitz" effect applied by BYOND to cover up the visual sins
of tile-based movement, by making objects and the map appear to move smoothly
from one tile to another instead of immediately jumping. It is also available to
smooth over small jumps in pixel movement that might occur, for instance if the
client FPS is set higher than the server's.
 



 To control the gliding speed of an atom, set
 `glide_size` 
 to the
value of your choice. If this is not set, the client will attempt to adjust
the speed manually.
 `glide_size` 
 is measured in server ticks, so
if
 `client.fps` 
 is set to a value greater than
 `world.fps` 
 ,
it will be scaled appropriately.
 



 Whether an object glides or jumps is based on how far it moves relative to
its
 
 step\_size
 
 value, which by default is a full tile width. If the
movement goes too far past
 
 step\_size
 
 in the X or Y directions, it's
no longer a glide.
 



 The
 
 animate\_movement
 
 var can be used to control the way in which
an object glides, or suppress gliding altogether.
 



 By using the
 
 LONG\_GLIDE
 
 flag in
 
 appearance\_flags
 
 , a
diagonal glide will take just as long as a cardinal-direction glide by moving
a fullt
 
 glide\_size
 
 pixels in the dominant X or Y direction.
Otherwise, gliding tries to move by that many pixels in strict Euclidean
distance (a straight line) and diagonal glides take longer.
 



 In
 [LEGACY\_MOVEMENT\_MODE](#/world/var/movement_mode) 
 ,
gliding is turned off if you set any of the bound or step vars for an atom to
a non-default value. The only gliding that occurs in this case is when
client.fps is higher than world.fps. All other movement modes base gliding on
an atom's
 
 glide\_size
 
 value.
 




---
HUD / screen objects
----------------------




**See also:** 


[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[screen var (client)](#/client/var/screen) 

[view var (client)](#/client/var/view) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[layer var (atom)](#/atom/var/layer) 

[image objects](#/image) 









 HUD stands for Heads-Up Display, and refers to any atoms that appear on
the screen but don't move when the player moves. These are also called screen
objects. Any movable atom can be added to the HUD by setting its
 
 screen\_loc
 
 var, and adding it to
 
 client.screen
 
 for each user
who is supposed to see it. This can be used to display a character's vital
stats, scores, etc.
 



 If you want to have something like a health meter or name attached to a
moving atom, use overlays or
 
 /image
 
 objects instead. An
 
 /image
 
 object is similar to a screen object in that it can be shown
to only certain players instead of being shown to everyone.
 



 The size of the screen depends on
 
 client.view
 
 (or
 
 world.view
 
 ),
 
 world.map\_format
 
 , and
 
 world.icon\_size
 
 .
In a normal topdown map format,
 
 client.view
 
 is the same as the screen
size; in other map formats the screen might be a different size.
 



 The
 
 screen\_loc
 
 var can be set to a value like
 
 "1,1"
 
 (the
southwest tile of the screen),
 
 "4,NORTH"
 
 (fourth tile from the west,
along the north side of the screen),
 
 "SOUTHEAST"
 
 , and so on. You can
also include pixel offsets, percentages, and specify two corners to tile an
icon repeatedly from one end to the other. See
 [screen\_loc](#/atom/movable/var/screen_loc) 
 for more
details.
 




 screen\_loc
 
 can also be used to stretch the bounds of the HUD. A
value of
 
 "0,0"
 
 will cause the atom to appear to the southwest of the
southwest-most tile on the visible map, outside of the regular map bounds.
Using HUDs in this way, you can provide a nice decorative "frame" for your map.
 



 More complex
 



 You can use HUDs in other map controls as well, by preceding screen\_loc with
the name of the map you will use followed by a colon. For instance,
 
 screen\_loc="map2:1,1"
 
 will show an icon in the southwest corner of the
 
 map2
 
 control. The actual size of a secondary HUD is based on how far
out the icons in it extend in any direction. If you have one icon at
 
 "map2:1,1"
 
 and another at
 
 "map2:4,3"
 
 , then that HUD will be
four tiles wide and three high.
 




---
Isometric maps
----------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[pixel\_w var (atom)](#/atom/var/pixel_w) 

[pixel\_z var (atom)](#/atom/var/pixel_z) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[Side-view maps](#/{notes}/side) 

[Topdown maps](#/{notes}/topdown) 

[HUD](#/{notes}/HUD) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/topdown_layer) 















![](data:image/png;charset=utf-8;base64,iVBORw0KGgoAAAANSUhEUgAAANIAAAB4CAAAAACidfMWAAAGcklEQVR4XtzGoQ2AMBQE0BO/vpuwQi2qsiEoBsHWd4cuwQisg0OQ4ycsAOYETz3wd0CBmvIydYoYBMb1AgpU+MIxuP158578ZosIM1XsbubuY6qs4gCO/y4koFSmU7IxHdWYY8iI0cocLE3KJEsqyLDYBYKKEWkEEqSc+yAvYjfCjBmBehm+oZjELGeZL9HKuZI9KXPWLKpZrZxComR4721jc7/F5d77POece875/el2xj7z+sj3ueccI2ynDgC5J0MAAH7TAVxgZg6RK9qq8CYQNUFgdPpqgWaOJBe/3vtqqmOyMJKJf0u16XNMg46RCyTdArB5Cij4twQjLzhNgnoeKij4LsMCAChSiPQowIlGU6CvHs7PO70Mf4BypIVPA1SeMw46vijb2rccQQqShpumwtV8t0HQidSs5WeeDwZQmeS8vRHgSKsh0LdLMjPOWBGkKAkg6zGA0vP+F/Q+kZ52Nmfso1TXFXyIQ3Ps4GBhoh+Qbuut2DthLPNnGIA2sCpHirTnw0cXfYJO2b4p7wjxBPUDQBSilCFBXsch6PEB6tO+fmNH6PggQJRKJGiJG/IOOqN9WdbuHYQopUhRdUXeQGerjpY6wnyCEKUQCQp3j//B+6Hq85LWiX5BiFKHZNkcP+wJOrf2YHHzJC8g4SiLG1jnx+oDK18JNwbC6QerqqT+6v0rim42BUKUiqRfarqKVtxCAUKUWqRfaz8sXHkrFQhRKpHO1+0ueO02ahCiVCH9XrfrpeIpjCBEySf9Ub89r2QqMwhRskl/1rfnlkyjAAlBUbxt/Wt9m7VvukdUIICKpEO8LNIF+5as0xHj9VA/3AMDVKCjkA39mB5iP3gX7a3Plc3wkg+IogDhx08o6VJD87Pld3gBIYoOhChxpIF3Nj1THukDhCgaEKJEkf5ubHqqYqYfEKJoQIgSQbq8YWPam7MMgBBFA0JUoElDGzcsWR1lEIQoGhCiAkm68l7j4tV3mQAhigaEqECRrjY1LFpzt0kQouhAiOJPGt5kX1gZTQFCFA0IUbxJ/7z/1vzK2ZQgRNGAEMWTdO2D+iQSwwBCFA0IUbxI11rXPUBiGUGIogMhip3075a6e21xHECIQhANipU0srU2wRbPt4cA5rP1FEtcXHfUxO1L4N1DaTAgpKeQhKD26pjOxAD0EI+eookL57bqaNt93HtIVE95kpw7q+7U5nLvIcE9hSRw7aqaqc3j3kOiewpJrj3aDC2Zew+J7ikkuTu1adqD3HtIdE8hyb3PNrlqAfceEt5TSOqyhWsp3HtIeE8hqdsWqj3CvYck9pQlMdi2mHsPSe0pS08S9x6S3FMWN+8ektZTSOLbQxJ7Ckmce0h+TyGJvYcU6SmMC8aeSZO73ltc6Kw9JG098SAhSmYPIYoShCQ6FIIk9xTx/1+tztpDQtcTY78Q6aw9JGw9Mf5rq87aQ0LWE3NxoQvoIbb1xHwC6gJ6iH49oQt1XUAP0a0n9K9TdA49xH89YXrphSgESe4pwvRqElEIktxThM8LZF1WDyEKQWZI+JpfS/RAyeohRCHIDAm/jNESxqLaJPcQgJXzV2aYHpT5kAbAtJ7w/WJTfk8Rvl8/y+8pwnmTgPSeIvy3csjtKSJgw43QniICtkUJ7SkiYPOa0J4iArYYCu0pImYjqLieIuK264rpKSJ3UzX/niJyt77z7ymixgEFnWcPiSThMZKyiAD0FIJEkvCwz6rp/HvKKv9IFt+eImodnGPvKaLW8Ub2niJqHUJl7ymi3lFhtp4iah7opu8pou6xewoUgpS/HAFRNCD5JLzConCSQRSCVCXhRSMFEw2gEKQyCa+DeTnMHwpB8kmNjhuA7lk+Lu15MdQ3CkHySaX2G4Dvo31erZTnBSUAhNui+E3s7lO29eW5If8nxY+iEKQSyR4LABDpCxW3V7etq8iZMA4KQYEet7EpAYAv3Ibm5ONRLSMef+pwuAVNEHCfhO7Ortlbr49ZYLVKvPKPfRL379wT0+akAEh54qV+bIx1nPxUmRks8WJG/jP3oKMtdodLJon/zPuspXVOB6JUvGuy634ACDOBSj58jKwdvTD4Eia9Yg9xijmcFLfX5X6y2y1sgiDAs6Cn4e2Edz/JHlTygzc0mgphYSZRKSmfLrvmKtymIil1FFBRA2Yn4jKMbM9YKuyJJ2AOJC/NyRwS98ETMOXlIHD+A3oxNU80orubAAAAAElFTkSuQmCC)


 Isometric projection is a form of pseudo-3D in which the 2D icons used by
BYOND can be arranged in a way to give the appearance of three dimensions. If
you look at a map top-down, each tile on the map is a square. The map is
rotated 45° clockwise and then tilted at an angle (30°) so that each
square now looks like a foreshortened diamond from the viewer's perspective.
What was once north now points to the northeast end of the viewer's screen;
what was once east now points southeast to the viewer. Tiles that are more to
the south or east are "nearer" to the viewer, and tiles that are north or west
are "farther". The actual direction the map faces can be changed by using
 
 client.dir
 
 .
 



 It is important to remember that this is an illusion of 3D, not real 3D.
 



 To use isometric mapping, set
 
 world.map\_format
 
 to
 
 ISOMETRIC\_MAP
 
 . You should set
 
 world.icon\_size
 
 so the tile
width is a multiple of 4 pixels. The width of the tile is highly important.
The height of your tiles should be at least half that value. BYOND uses a 2:1
isometric format, meaning that the diamond base of each tile is half as high
as its width. For example if you have a 64x64 tile size, every diamond in the
map will be 64 pixels wide by 32 high, and you have an extra 32 pixels at the
top of your icon for vertical projections like buildings. If you set the tile
size to 64x80, the base is still a 64x32 diamond and you have 48 pixels left
over for vertical structures.
 



 In this mode
 
 pixel\_x
 
 and
 
 pixel\_y
 
 will offset icons along the
"ground". To adjust horizontal and vertical positions, use the
 
 pixel\_w
 
 and
 
 pixel\_z
 
 vars.
 


### 
 Layers



 The
 
 layer
 
 var behaves differently in isometric mode. Because some
tiles are nearer to the viewer than others, the tiles that are farther back
need to be drawn first so they are behind any tiles that should go in front of
them. So in isometric mode, the back row of tiles (a diagonal line of them) is
drawn first, followed by the next row forward, and so on. The
 
 layer
 
 var only matters when icons overlap each other in the "physical" space, like
an obj sitting on a turf.
 



 When pixel or step offsets, or gliding, place an object on multiple turfs,
it is drawn on top of the nearer turf (assuming its layer is higher).
 



 Using icons wider than the regular tile size can have an impact on layering
as well. See
 [Big icons](#/{notes}/big-icons) 
 for more information.
 



 Because of the order in which icons are drawn, you may want to limit the
ability of an atom to cut diagonally around corners. While moving northeast
behind a dense wall, for instance, a mob might temporarily appear in front of
the wall because its pixel offsets (from gliding) temporarily put it on the
same tile as the wall. If you do not want to limit corner-cutting, a simple
workaround for this case is to give the wall a higher layer than the mob.
 



 Screen objects (in
 
 client.screen
 
 ) are always drawn on top of all
isometric tiles, as is the case in other map modes as well.
 



 Since it may be desirable in some games to use a topdown map for some
situations (like a special battle map), you can add
 
 TOPDOWN\_LAYER
 
 to
any atom's layer—e.g.,
 
 TOPDOWN\_LAYER+TURF\_LAYER
 
 —to make
it appear in topdown mode. Topdown and isometric tiles really aren't meant to
be mixed, but if they do mix you'll see topdown tiles always display above
isometric tiles, just like screen objects do. The best way to use this is to
apply
 
 TOPDOWN\_LAYER
 
 to every tile in a certain part of the map that
the players can't walk to.
 



 If you want to use an overlay that should not be covered by other "nearer"
icons on the map, such as a name or health meter, you can add
 
 EFFECTS\_LAYER
 
 to the overlay's layer. Icons with
 
 EFFECTS\_LAYER
 
 will draw above regular icons. Then objects with
 
 TOPDOWN\_LAYER
 
 will draw on top of everything else. However, be aware
that
 
 EFFECTS\_LAYER
 
 has largely been superseded by the
 
 plane
 
 var.
 


### 
 Screen size



 In this mode,
 
 world.view
 
 or
 
 client.view
 
 is used to define
the minimum number of map tiles you will see,
 *not* 
 the screen/HUD size
which is calculated from client.view. Extra map tiles are shown to fill out
the screen size. HUD objects use screen coordinates, so 1,1 is still the lower
left.
 



 The actual HUD size is always a full number of tiles, whose size is defined
by
 
 world.icon\_size
 
 . If you have a tile size of
 
 64x64
 
 , and
 
 world.view=6
 
 (a 13x13 map), a full 13x13 diamond of map tiles will be
shown. The width of this diamond is 13 tiles. The height is only half that,
plus whatever vertical space is needed to show the icons in that area. Then
everything is rounded up to a full tile size, so the result is a 13x7-tile
screen. This is the formula you need if you want to calculate the screen size:
 



 pixel\_width = round(icon\_width \* (view\_width + view\_height) / 2)
pixel\_height = round(icon\_width \* (view\_width + view\_height - 2) / 4) + icon\_height

screen\_width = round((pixel\_width + icon\_width - 1) / icon\_width)
screen\_height = round((pixel\_height + icon\_height - 1) / icon\_height)
 

 If you use
 
 TOPDOWN\_LAYER
 
 , any topdown sections of the map will be
limited to this same view.
 




---
Numbers
---------



 In DM, all numbers are stored in floating point format. Specifically,
single-precision (32-bit) floating point. This is important to know if you
think you will be working with large numbers or decimal values a lot, because
the accuracy of the numbers is limited.
 



 32-bit floating point numbers can represent integers from -16777216
to 16777216 (2
 24 
 ). Non-integer values can get about as small as
2
 -126 
 and as large as 2
 127 
 .
 



 Floating point numbers do not handle most decimal values precisely. For
instance, 0.1 is not exactly 0.1, because floating point numbers are stored
in a binary format and in binary, 1/10 is a fraction that repeats
forever—the same way 1/3 repeats as 0.33333... in decimal numbers. It
ends up being rounded off, either a little higher or a littler lower than
its true value. This means that the following loop won't work like you might
expect:
 


### 
 Example:



 for(i = 0, i < 100, i += 0.1)
 world << i
 

 You might expect that code to loop exactly 1000 times, with
 
 i
 
 going from 0 up to 99.9 before stopping. The truth is more complicated,
because 0.1 stored in floating point is actually greater than the exact value
of 0.1. Other values might be more or less than their exact numbers, and as
you add these numbers together repeatedly you'll introduce more and more
rounding error.
 



 Even more insidious, if you add 0.1 a bunch of times starting from 0, and
then subtract it out again the same number of times, the result you get may
not be 0. This is counterintuitive, because you might expect rounding errors
to reverse themselves in the same order they crept in. Unfortunately it
doesn't work that way.
 



 You can correct for rounding error somewhat by using the
 [round
 
 proc](#/proc/round) 
 to adjust the loop var each time,
although for performance reasons it might be preferable to find another
alternative.
 



 for(i = 0, i < 100, i = round(i + 0.1, 0.1))
 world << i
 

 Only fractions whose denominators are powers of 2 are immune to this
rounding error, so 0.5 is in fact stored as an exact value.
 



 Another place floating point may lose accuracy is when you try to add
numbers of very different sizes. For instance as stated above, the upper
limit for accurate integers is 16777216. If you try to use a number such
as 100 million it will only be approximate, so adding 1 to that number
won't actually change it because the 1 is so much smaller, it will be
gobbled up by rounding error.
 



 Also for the same reasons stated above, division will cost you
accuracy. Again you can divide by powers of 2 easily enough, and you can
divide an integer by any of its factors (like dividing 9 by 3) without a
problem, but a fraction like 1/3 will repeat forever so it gets rounded
to as much precision as floating point can manage.
 



 In decimal, floating point numbers have at least six decimal digits of
precision. Since they're actually stored in binary, their true precision
is exactly 24 bits.
 




---
Particle effects
------------------




**See also:** 


[particles (movable atom var)](#/atom/movable/var/particles) 

[Generators](#/{notes}/generators) 

[generator proc](#/proc/generator) 

[Projection matrix](#/{notes}/projection-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







 A particle set is a special effect, whose computations are handled entirely
on the client, that spawns and tracks multiple pixels or icons with a
temporary lifespan. Examples of this might be confetti, sparks, rocket
exhaust, or rain or snow. Particles are rendered on a special surface and that
gets attached to an obj or a mob like an overlay.
 



 Particles can exist in 3 dimensions instead of the usual 2, so a particle's
position, velocity, and other values may have a z coordinate. To make use of
this z coordinate, you can use a
 [projection
matrix](#/{notes}/projection-matrix) 
 . (The value of the z coordinate must be between -100 and
100 after projection. Otherwise it's not guaranteed the particle will be
displayed.)
 



 To create a particle set, use
 
 new
 
 to create a new
 
 /particles
 
 datum, and then you can set the datum's vars. The vars can
be set to constant values, or generator functions that will allow the client
to choose from a range of values when spawning those particles. (The easiest
way to handle this is to create your own type that inherits from
 
 /particles
 
 , and set up the parameters you'll want at compile-time.)
 



 After the datum is created, it can be assigned to an obj or mob using their
 
 particles
 
 var. The particles will appear on the map wherever that obj
or mob appears.
 


### 
 Example:



 particles/snow
 width = 500 // 500 x 500 image to cover a moderately sized map
 height = 500
 count = 2500 // 2500 particles
 spawning = 12 // 12 new particles per 0.1s
 bound1 = list(-1000, -300, -1000) // end particles at Y=-300
 lifespan = 600 // live for 60s max
 fade = 50 // fade out over the last 5s if still on screen
 // spawn within a certain x,y,z space
 position = generator("box", list(-300,250,0), list(300,300,50))
 // control how the snow falls
 gravity = list(0, -1)
 friction = 0.3 // shed 30% of velocity and drift every 0.1s
 drift = generator("sphere", 0, 2)
obj/snow
 screen\_loc = "CENTER"
 particles = new/particles/snow

mob
 proc/CreateSnow()
 client?.screen += new/obj/snow
 

 These are the vars that can be used in a particle set. "Tick" refers to a
BYOND standard tick of 0.1s.


| 
 Particle vars that affect the entire set (generators are not allowed for these)
  |
| --- |
| 
 Var
  | 
 Type
  | 
 Description
  |
| 
 width
  | 
 num
  | 
 Size of particle image in pixels
  |
| 
 height
  |
| 
 count
  | 
 num
  | 
 Maximum particle count
  |
| 
 spawning
  | 
 num
  | 
 Number of particles to spawn per tick (can be fractional)
  |
| 
 bound1
  | 
 vector
  | 
 Minimum particle position in x,y,z space; defaults to list(-1000,-1000,-1000)
  |
| 
 bound2
  | 
 vector
  | 
 Maximum particle position in x,y,z space; defaults to list(1000,1000,1000)
  |
| 
 gravity
  | 
 vector
  | 
 Constant acceleration applied to all particles in this set (pixels per squared tick)
  |
| 
 gradient
  | [color gradient](#/{notes}/color-gradient)  | 
 Color gradient used, if any
  |
| 
 transform
  | [matrix](#/{notes}/projection-matrix)  | 
 Transform done to all particles, if any (can be higher than 2D)
  |
| 
 Vars that apply when a particle spawns
  |
| 
 lifespan
  | 
 num
  | 
 Maximum life of the particle, in ticks
  |
| 
 fade
  | 
 num
  | 
 Fade-out time at end of lifespan, in ticks
  |
| 
 fadein
  | 
 num
  | 
 Fade-in time, in ticks
  |
| 
 icon
  | 
 icon
  | 
 Icon to use, if any; no icon means this particle will be a dot
 
 Can be assigned a weighted list of icon files, to choose an icon at random
  |
| 
 icon\_state
  | 
 text
  | 
 Icon state to use, if any
 
 Can be assigned a weighted list of strings, to choose an icon at random
  |
| 
 color
  | 
 num or color
  | 
 Particle color (not a color matrix); can be a number if a gradient is used
  |
| 
 color\_change
  | 
 num
  | 
 Color change per tick; only applies if gradient is used
  |
| 
 position
  | 
 num
  | 
 x,y,z position, from center in pixels
  |
| 
 velocity
  | 
 num
  | 
 x,y,z velocity, in pixels
  |
| 
 scale
  | 
 vector (2D)
  | 
 Scale applied to icon, if used; defaults to list(1,1)
  |
| 
 grow
  | 
 num
  | 
 Change in scale per tick; defaults to list(0,0)
  |
| 
 rotation
  | 
 num
  | 
 Angle of rotation (clockwise); applies only if using an icon
  |
| 
 spin
  | 
 num
  | 
 Change in rotation per tick
  |
| 
 friction
  | 
 num
  | 
 Amount of velocity to shed (0 to 1) per tick, also applied to acceleration from drift
  |
| 
 Vars that are evalulated every tick
  |
| 
 drift
  | 
 vector
  | 
 Added acceleration every tick; e.g. a circle or sphere generator can be applied to produce snow or ember effects
  |



 The
 
 icon
 
 and
 
 icon\_state
 
 values are special in that they can't be assigned a generator, but they can be assigned a constant icon or string, respectively, or a list of possible values to choose from like so:
 



 icon = list('confetti.dmi'=5, 'coin.dmi'=1)
 

 The list used can either be a simple list, or it can contain weights as shown above.
 



 Changing a var on a particle datum will make changes to future particles.
For instance, you can set the datum's
 
 spawning
 
 var to 0 to make it
stop creating new particles. (Note: If you are changing a vector or color
matrix, such as
 
 gravity
 
 , you need to assign a new value. You can't
for instance set
 
 particles.gravity[2] = 0
 
 because it won't do
anything to update the particle stream.)
 



 The same particle datum can be assigned to more than one movable atom.
However the particles displayed by each atom will be different.
 




---


Pixel movement
----------------




**See also:** 


*Bounding boxes* 

[bound\_x var (movable atom)](#/atom/movable/var/bound_x) 

[bound\_y var (movable atom)](#/atom/movable/var/bound_y) 

[bound\_width var (movable atom)](#/atom/movable/var/bound_width) 

[bound\_height var (movable atom)](#/atom/movable/var/bound_height) 

*Speed and position* 

[step\_size var (movable atom)](#/atom/movable/var/step_size) 

[step\_x var (movable atom)](#/atom/movable/var/step_x) 

[step\_y var (movable atom)](#/atom/movable/var/step_y) 

[locs list var (movable atom)](#/atom/movable/var/locs) 

[contents list var (atom)](#/atom/var/contents) 

[fps var (world)](#/world/var/fps) 

*Movement* 

[Move proc (movable atom)](#/atom/movable/proc/Move) 

[Cross proc (atom)](#/atom/proc/Cross) 

[Crossed proc (atom)](#/atom/proc/Crossed) 

[Uncross proc (atom)](#/atom/proc/Uncross) 

[Uncrossed proc (atom)](#/atom/proc/Uncrossed) 

[movement\_mode var (world)](#/world/var/movement_mode) 

[appearance\_flags var (atom)](#/atom/var/appearance_flags) 

*Other topics* 

[bounds proc](#/proc/bounds) 

[bounds\_dist proc](#/proc/bounds_dist) 

[Gliding](#/{notes}/gliding) 


























 Pixel movement is a concept that allows atoms to escape the constraints of
BYOND's historically tile-based movement, and move in smaller steps. In the
past this had to be done with soft code, but that was sometimes inconvenient
and it did not perform as well in projects with many objects moving.
 



 The key to understanding pixel movement is to use the bound and step vars.
You use the bound family of vars to define a bounding box for a movable atom,
instead of just making it one full tile in size. The step vars can give it a
movement speed and offset it from the corner of the tile it's standing on.
 


* bound\_x: The left edge of the bounding box
* bound\_y: The bottom edge of the bounding box
* bound\_width: Width of the bounding box
* bound\_height: Height of the bounding box
* step\_size: default movement speed
* step\_x: x offset from the corner of loc
* step\_y: y offset from the corner of loc



 Those are for movable atoms only; they do not apply to turfs.
 



 If
 [world.movement\_mode](#/world/var/movement_mode) 
 is set to
 
 TILED\_MOVEMENT\_MODE
 
 , all movable atoms must be aligned
to the tile grid: their step\_x/y/size values must be multiples of the icon
size, and their bounds must also land on tile boundaries although the atom
can be bigger than one tile. In other movement modes you can specify that
only specific atoms use this behavior, by giving them the
 [TILE\_MOVER](#/atom/var/appearance_flags) 
 appearance
flag.
 


### 
 Bounding boxes



![](data:image/png;charset=utf-8;base64,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)

**Left:** 
 The bounding box (blue) is the only part of the mob that actually collides with anything. By default, it would cover the whole turf (brown). Any turfs covered by the bounding box are in the mob's locs var.
 **Right:** 
 The atom's true position (shaded) is offset from the turf by step\_x and step\_y.
 




 As an example, if your players' mobs have icons that only cover the center
24×24 pixels of a regular 32×32 icon, then you would set the
mobs' bound\_x and bound\_y to 4--because there are 4 pixels unused to the left
and bottom--and bound\_width and bound\_height to 24.
 



 The mob's physical location on the map depends on four things: Its loc,
its step\_x/y values, its bound\_x/y values, and its bound\_width/height. The
lower left corner of the bounding box, relative to the turf the mob is
actually standing on, begins at step\_x+bound\_x on the left and step\_y+bound\_y
on the bottom.
 



 The physical position of the bounding box is
 **not affected** 
 by the
pixel\_x/y/z vars. Those are still strictly visual offsets.
 



 The turfs the mob is covering can be read from the read-only locs var. The
mob will also appear in the contents of those turfs.
 



 Note: This means if an atom is in a turf's contents, its loc is
 *not
necessarily* 
 that turf. The contents list is made to include "overhangers"
from another tile for ease of use.
 


### 
 Movement



 All of the step and walk procs have been upgraded to take an additional
argument, which is the speed at which the atom should move. If that argument
is left out, the atom's own step\_size is used by default. The step\_size
determines how fast the step\_x and step\_y values will change when moving.
 



 Move() has two new arguments that handle the position change gracefully.
These are the step\_x and step\_y values for the target location.
 



 Pixel movement changes the behavior of the Move() proc, because a lot of
things are possible that were not possible when BYOND only supported moving
one tile at a time. For starters, a Move() is either a "slide" or a "jump"
depending on the distance. A slide is when the move can be stopped partway;
a jump is strictly pass/fail. Anything greater than one tile
 *and* 
 the
mover's regular step\_size is considered a jump. Changing z levels is also a
jump, as is moving to/from a non-turf.
 



 If step\_x and step\_y aren't within a good range, the new loc and the
step\_x/y values may be changed so that the southwest corner of the mover's
bounding box is standing on its actual loc, or as close to it as possible.
 



 Enter() and Exit() can be called for several turfs and/or areas, not
just one at a time. It is also possible for them not to be called at all,
if the moving atom moves within a turf but doesn't cross a new turf
boundary. Enter() and Exit() are only called when first attempting to enter
or fully exit. The behavior of these procs depends on
 [world.movement\_mode](#/world/var/movement_mode) 
 ; in
legacy mode, they look at some of the contents of the turfs as well as the
turfs themselves, to preserve behavior found in older BYOND versions.
 



 Cross() and Uncross() are the equivalent of Enter() and Exit() but apply
to objects the mover will either overlap or stop overlapping. (For turfs,
Enter() and Exit() call these procs by default, since the mover is both
stepping
 *into* 
 and
 *onto* 
 a turf.) Likewise Crossed() and
Uncrossed() are the equivalents of Entered() and Exited().
 



 If an atom is sliding, its movement can be halted if it encounters an
obstacle partway along its route. Bump() will still be called for any
obstacles the atom runs into, but Move() will return the number of pixels
moved (the most in any direction). When sliding at a speed so fast that the
distance is bigger than the atom itself, the move will be split up into
several smaller slides to avoid skipping over any obstacles.
 



 Gliding, which is used to show smooth movement between atoms in tile
movement, is mostly not used in pixel movement. It only applies when the
client uses a higher
 [fps](#/client/var/fps) 
 than the
server.
 


### 
 Pixel procs



 The bounds() and obounds() procs have been added to grab a list of atoms
within a given bounding box. That box can be relative to an atom, or in
absolute coordinates.
 



 bounds\_dist() tells the distance between two atoms, in pixels. If it is
positive, that is the minimum distance the atoms would have to traverse to be
touching. At 0, they are touching but not in collision. A negative value
means the two atoms are in collision.
 




---
Projection matrix
-------------------




**See also:** 


[Particle effects](#/{notes}/particles) 

[transform var (atom)](#/atom/var/transform) 

[matrix](#/matrix) 

[Color matrix](#/{notes}/color-matrix) 






 Note: Currently this feature applies only to particle effects, using the
 
 transform
 
 var.
 



 Normally icons in BYOND can only be transformed in 2D, using a simple 3x3
matrix. This is represented by the
 
 /matrix
 
 object, which cuts off the
last column because it isn't used. However particles can have coordinates in x,
y, and z, and the whole particle set can be given a transformation matrix that
handles all three dimensions.
 


### 
 Simple 2D transforms



 The easiest transformation for particles is a simple 2D one, which you can
do by setting the particle datum's
 
 transform
 
 var to a
 
 /matrix
 
 object.
 



```
          a d 0
x y 1  *  b e 0  =  x' y' 1
          c f 1
```


 When an x,y point is multiplied by the matrix, it becomes the new point
x',y'. This is equivalent to:
 



```
x' = a*x + b*y + c
y' = d*x + e*y + f
```


 This is called an
 **affine transform** 
 because all the operations are
"linear" in math terms. (That is, every term in the formula above has a single
variable, not raised to a higher power than 1.)
 


### 
 3x4 matrix (x,y,z with translation)



 3D affine transforms of this type are also affine transformations. There is
no special object for this so a list is used (see below).
 



```
            xx xy xz 0
x y z 1  *  yx yy yz 0  =  x' y' z' 1
            zx zy zz 0
            cx cy cz 1
```


 The way to read the vars above is that the first letter says what input
component is being transformed (x,y,z, or c for "constant"), and the second
letter is the output component.
 



```
x' = xx*x + yx*y + zx*z + cx
y' = xy*x + yy*y + zy*z + cy
z' = xz*x + yz*y + zz*z + cz
```


 To use this kind of matrix, you can cut off the 4th column and provide the
values in a list form, in row-major order:
 



 list(xx,xy,xz, yx,yy,yz, zx,zy,zz, cx,cy,cz)
 

 Note the 4th row is also optional.
 


### 
 4x4 matrix (x,y,z,w with projection)



 This is the most interesting matrix, since if you use all 4 columns you're
actually altering an "axis" called w. This isn't a real axis, but is just a
number that the resulting vector will be divided by.
 



```
            xx xy xz xw
x y z 1  *  yx yy yz yw  =  x'w' y'w' z'w' w'
            zx zy zz zw
            wx wy wz ww

w' = xw*x + yw*y + zw*z + ww
x' = (xx*x + yx*y + zx*z + wx) / w'
y' = (xy*x + yy*y + zy*z + wy) / w'
z' = (xz*x + yz*y + zz*z + wz) / w'
```


 In a regular affine transform, w always stays at 1. In projection you can
think of w as a distance from the "camera". 1 is where objects are their
"normal" size. If you make the z value affect w' by setting zw, you basically
make an object look smaller at higher z values.
 



 This is a simple projection matrix where x,y,z are left untouched, but
there's a projection effect. The "D" value is how far away the "camera" is
from z=0, so a point at z=D looks like it's twice as far away.
 



```
1  0  0  0
0  1  0  0
0  0  1  1/D
0  0  0  1

```


 This 4x4 matrix is handled as a list just like the 3x4 affine matrix:
 



 list(xx,xy,xz,xw, yx,yy,yz,yw, zx,zy,zz,zw, wx,wy,wz,ww)
 


---
Regular expressions
---------------------




**See also:** 


[regex datum](#/regex) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 








 Regular expressions are patterns that can be searched for within a text
string, instead of searching for an exact match to a known piece of text.
They are much more versatile for find and replace operations, and therefore
useful for parsing, filtering, etc.
 



 Some example regular expressions are:


| 
 Pattern
  | 
 Code
  | 
 Meaning
  |
| --- | --- | --- |
| 
 B.\*D
  | 
 regex("B.\*D")
  | 
 Find
 
 B
 
 , followed by any number of characters (including none), followed by a
 
 D
 
 .
  |
| 
 [0-3]
  | 
 regex(@"[0-3]")
  | 
 Find any digit from 0 to 3
  |
| 
 foo|bar
  | 
 regex("foo|bar","i")
  | 
 Find
 
 foo
 
 or
 
 bar
 
 , case-insensitive
  |
| 
 \d+
  | 
 regex(@"\d+","g")
  | 
 Find all sequences of digits
  |



 These are some of the patterns you can use. If you want to use any of the
operators as an actual character, it must be escaped with a backslash.
 



 It is highly recommended that you use
 [raw strings](#/DM/text) 
 like
 `@"..."` 
 for your regular expression patterns, because with a
regular DM string you have to escape all backslash
 `\` 
 and open
bracket
 `[` 
 characters, which will make your regular expression
much harder for you to read. It's easier to write
 `@"[\d]\n"` 
 than
 `"\[\\d]\\n"` 
 .
 




| 
 Pattern
  | 
 Matches
  |
| --- | --- |
| *a* 
 |
 *b*  | *a* 
 or
 *b*  |
| 
 .
  | 
 Any character (except a line break)
  |
| 
 ^
  | 
 Beginning of text; or line if
 
 m
 
 flag is used
  |
| 
 $
  | 
 End of text; or line if
 
 m
 
 flag is used
  |
| 
 \A
  | 
 Beginning of text
  |
| 
 \Z
  | 
 End of text
  |
| 
 [
 *chars* 
 ]
  | 
 Any character between the brackets. Ranges can be specified with a hyphen, like 0-9. Character classes like
 
 \d
 
 and
 
 \s
 
 can also be used (see below).
  |
| 
 [^
 *chars* 
 ]
  | 
 Any character NOT matching the ones between the brackets.
  |
| 
 \b
  | 
 Word break
  |
| 
 \B
  | 
 Word non-break
  |
| 
 (
 *pattern* 
 )
  | 
 Capturing group: the pattern must match, and its contents will be captured in the group list.
  |
| 
 (?:
 *pattern* 
 )
  | 
 Non-capturing group: Match the pattern, but do not capture its contents.
  |
| 
 \1
 *through* 
 \9
  | 
 Backreference;
 
 \
 *N* 

 is whatever was captured in the
 *N* 
 th capturing group.
  |
| 
 Modifiers
  |
| 
 Modifiers are "greedy" by default, looking for the longest match possible. When following a word, they only apply to the last character.
  |
| *a* 
 \*
  | 
 Match
 *a* 
 zero or more times
  |
| *a* 
 +
  | 
 Match
 *a* 
 one or more times
  |
| *a* 
 ?
  | 
 Match
 *a* 
 zero or one time
  |
| *a* 
 {
 *n* 
 }
  | 
 Match
 *a* 
 , exactly
 *n* 
 times
  |
| *a* 
 {
 *n* 
 ,}
  | 
 Match
 *a* 
 ,
 *n* 
 or more times
  |
| *a* 
 {
 *n* 
 ,
 *m* 
 }
  | 
 Match
 *a* 
 ,
 *n* 
 to
 *m* 
 times
  |
| *modifier* 
 ?
  | 
 Make the previous modifier non-greedy (match as little as possible)
  |
| 
 Escape codes and character classes
  |
| 
 \x
 *NN*  | 
 Escape code for a single character, where
 *NN* 
 is its hexadecimal ASCII value
  |
| 
 \u
 *NNNN*  | 
 Escape code for a single 16-bit Unicode character, where
 *NNNN* 
 is its hexadecimal value
  |
| 
 \U
 *NNNNNN*  | 
 Escape code for a single 21-bit Unicode character, where
 *NNNNNN* 
 is its hexadecimal value
  |
| 
 \d
  | 
 Any digit 0 through 9
  |
| 
 \D
  | 
 Any character except a digit or line break
  |
| 
 \l
  | 
 Any letter A through Z, case-insensitive
  |
| 
 \L
  | 
 Any character except a letter or line break
  |
| 
 \w
  | 
 Any identifier character: digits, letters, or underscore
  |
| 
 \W
  | 
 Any character except an identifier character or line break
  |
| 
 \s
  | 
 Any space character
  |
| 
 \S
  | 
 Any character except a space or line break
  |
| 
 Assertions
  |
| 
 (?=
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern to come next, but don't include it in the match
  |
| 
 (?!
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern NOT to come next
  |
| 
 (?<=
 *pattern* 
 )
  | 
 Look-behind: Require this pattern to come before, but don't include it in the match (must be a fixed byte length)
  |
| 
 (?<!
 *pattern* 
 )
  | 
 Look-behind: Require this pattern NOT to come before (must be a fixed byte length)
  |



 The optional flags can be any combination of these:
 




| 
 Flag
  | 
 Meaning
  |
| --- | --- |
| 
 i
  | 
 Case-insensitive matching
  |
| 
 g
  | 
 Global: In Find() subsequent calls will start where this left off, and in Replace() all matches are replaced.
  |
| 
 m
  | 
 Multi-line: ^ and $ refer to the beginning and end of a line, respectively.
  |



 After calling
 
 Find()
 
 on a
 
 /regex
 
 datum, the datum's
 
 group
 
 var will contain a list—if applicable—of any
sub-patterns found with the
 
 ()
 
 parentheses operator. For instance,
searching the string
 
 "123"
 
 for
 
 1(\d)(\d)
 
 will match
 
 "123"
 
 , and the
 
 group
 
 var will be
 
 list("2","3")
 
 .
Groups can also be used in replacement expressions; see the
 [Replace() proc](#/regex/proc/Replace) 
 for more details.
 




---


Understanding the renderer
----------------------------



 .renderlist {position: relative; display: inline-block; margin-left: 3em; text-align: center;}
 .renderlist-label, .renderlist-caption, .renderlist-note {display: block; margin: 3px 0; width: 100%;}
 .renderlist-caption {font-size: 1.1em; font-weight: bold;}
 .renderlist-note {font-size: 0.9em;}
 .renderlist-box {background: #eee; border: 1px solid #333; padding: 3px 10px; margin: 3px 0; border-radius: 10px;}
 body.dark .renderlist-box {color: white; background: #333; border-color: #aaa;}
 .renderlist-box .renderlist-box {background: #ddd; width: 100%;}
 body.dark .renderlist-box .renderlist-box {background: #444; width: 100%;}
 .renderlist-box .renderlist-box .renderlist-box {background: #ccc;}
 body.dark .renderlist-box .renderlist-box .renderlist-box {background: #555;}
 

 To get the most out of BYOND's visual effects, it helps to understand how
the map is displayed.
 



 Every atom has an
 [appearance](#/atom/var/appearance) 
 that holds
all of its visual info (and sometimes a little non-visual info). This
appearance has to be turned into sprites in order to be rendered.
 



 Although many atoms need little more than a simple
 [icon](#/atom/var/icon) 
 and
 [icon\_state](#/atom/var/icon_state) 
 and produce only a
single sprite, some are more complex with overlays, underlays, maptext, etc.
Also there may be
 [image objects](#/image) 
 and
 [visual contents](#/atom/var/vis_contents) 
 involved, although
they're not part of the atom's appearance.
 



 For a simple
 
 icon
 
 and
 
 icon\_state
 
 , just one sprite is
generated. The client looks up the icon it's given. Then it looks up an icon
state, which may be influenced by whether the atom is moving or not since you
can have moving and non-moving icon states. Then it determines which
 [direction](#/atom/var/dir) 
 to draw and which frame of the icon's
animation (if any) to use.
 



 So with several simple icons, and not worrying about layers for now, a list
of sprites lays out like this:
 




 Atom #1
 

 Atom #2
 

 &vellip;
 

 Atom #N
 

### 
 Overlays and underlays



 Now let's consider what happens when an appearance has overlays.
 




 Underlay #1
 

 &vellip;
 

 Underlay #N
 

 Main icon
 

 Overlay #1
 

 &vellip;
 

 Overlay #N
 


 The
 [underlays](#/atom/var/underlays) 
 list is processed
first, then
 [overlays](#/atom/var/overlays) 
 . These lists
contain appearances themselves, rather than actual atoms. This means that
overlays are recursive: an overlay can have overlays itself. To picture how
that works, just replace
one of the overlays above with another list.
 




 Underlay #1
 

 Underlay #2
 

 Main icon
 

 Underlays of overlay #1
 

 Overlay #1 icon
 

 Overlays of overlay #1
 

 Overlay #2
 

### 
 Image objects and visual contents



 Any atom can have an
 [image object](#/image) 
 attached, which can
be shown to only specific players. Most atoms, and image objects, can have
 [visual contents](#/atom/var/vis_contents) 
 that display other atoms
as if they're overlays.
 




 Underlays
 

 Main icon
 

 Overlays
 

 Image objects
 

 Visual contents
 


 As you see this is very similar to overlays. Just like overlays, image
objects and visual contents have appearances of their own (and may also have
their own images or visual contents), so this may be recursive as they add
new overlays, etc.
 



 A couple of things to keep in mind:
 


* If an image object uses the
 [override](#/atom/var/override) 
 var, it will replace the main appearance's icon and overlays, although it
 won't replace other images or visual contents.
* An object in visual contents can use
 [vis\_flags](#/atom/var/vis_flags) 
 to set
 
 VIS\_UNDERLAY
 
 and move itself before the parent's underlays.


### 
 Maptext and particles



 Any appearance may have
 [maptext](#/atom/var/maptext) 
 attached. That maptext draws above the icon but is grouped with it. That
grouping will be discussed further below.
 



 Particle effects also get grouped with the main icon in a similar way to
maptext.
 



 For simplicity, from this point forward the diagram will just treat underlays,
overlays, image objects, and visual contents as overlays.
 





 Main icon
 

 Maptext
 

 Particles
 


 Overlays
 

### 
 Color, transform, and filters



 An appearance's
 [color](#/atom/var/color) 
 and
 [alpha](#/atom/var/alpha) 
 vars (from here forwarded
they'll just be referred to by
 
 color
 
 ) and
 [transform](#/atom/var/transform) 
 are inherited by any
overlays, which also includes images and visual contents. You can avoid that
inheritance by giving those overlays special
 [appearance\_flags](#/var/appearance_flags) 
 :
 
 RESET\_COLOR
 
 ,
 
 RESET\_ALPHA
 
 , and
 
 RESET\_TRANSFORM
 
 .
 



 The appearance's filters are only applied to the main icon.
 





 Main icon
 

 Maptext
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 



 Overlays
 


 color
 
 and
 
 transform
 
 are inherited from Main
   


 filters
 
 are not inherited from Main
 



 When
 
 color
 
 and
 
 transform
 
 are inherited, they "stack". The
inherited color and transform values are applied after those of the overlays.
 


### 

 KEEP\_TOGETHER
 
 and
 
 KEEP\_APART



 There are times it's desirable for an appearance and all its overlays to be
treated as a single unit so any colors or filters can be applied all at once.
One simple example is if the appearance has an
 
 alpha
 
 of 128 to make it
translucent, you probably want to draw the whole atom faded instead of drawing
each sprite faded, one on top of the other.
 



 By using the
 
 KEEP\_TOGETHER
 
 value in
 [appearance\_flags](#/var/appearance_flags) 
 (called KT for
short), an appearance will group all of its underlays and overlays together.
If this is an atom with image objects and visual contents, those will be
grouped with it as well.
 





 KT group
 

 Main
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 apply
 


 Main icon
 

 Maptext
 


 Overlays
 



 With
 
 KEEP\_TOGETHER
 
 all of these sprites are rendered to a
temporary drawing surface, and then the main appearance's
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 are all applied to the combined
drawing. This comes with a trade-off, since you can no longer use flags
such as
 
 RESET\_COLOR
 
 to opt out of inheritance.
 



 If an overlay doesn't want to be part of a KT group, it can use the
 
 KEEP\_APART
 
 flag (KA for short). If there are multiple nested
KT groups, KA will only escape the innermost group.
 



 If an overlay inside a KT group has a different
 [plane](#/atom/var/plane) 
 than the group's owner, it
will be separated as if it defined
 
 KEEP\_APART
 
 , except it can
escape multiple nested groups.
 


### 
 Layers and planes



 Any appearance can have a
 [layer](#/atom/var/layer) 
 or
 [plane](#/atom/var/layer) 
 , and these influence how
it gets sorted. (There's also a concept called a "sub-plane" that's
influenced by whether an atom is a
 [HUD/screen object](#/{notes}/HUD) 
 or special layers like
 [BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 
 .)
 



 If a sprite is created with
 
 FLOAT\_LAYER
 
 (any negative value
counts as a floating layer) its layer has to be resolved, or "unfloated".
The main sprite for an atom can never float; it has to have a real layer.
Its overlays and underlays with floating layers will reorder themselves in
numerical order, then look for the next closest sprites in the rendering
list that has a non-negative layer.
 



 A similar process happens with
 
 FLOAT\_PLANE
 
 . Planes can have
negative values but
 
 FLOAT\_PLANE
 
 and the values close to it are
special. Sprites with floating planes have to resolve those as well.
 



 Once all atoms that will appear on the map are assembled into a rendering
list of sprites, the order in which they're rendered on the map is determined
in this order:
 


1. The
 
 plane
 
 var matters most.
2. Subplane is counted next. E.g., HUD objects render above non-HUD objects.
3. Depending on
 [world.map\_format](#/world/var/map_format) 
 ,
 
 layer
 
 or physical position determine the drawing order from here.
4. After everything else has been checked, the order the sprites were generated in is the final tie-breaker.



 In a typical topdown map,
 
 layer
 
 is basically all that matters
after the plane and subplane are taken into account. There is a legacy
concept called micro-layers that helps break ties between sprites with the
same layer; for instance if an atom is moving it's usually desirable to
draw it above other atoms with the same layer; this applies only to topdown
maps.
 


### 
 Plane masters



 Sometimes it's helpful to group multiple sprites on one plane as if the
plane itself were a KT group. For this,
 [appearance\_flags](#/var/appearance_flags) 
 has a value
called
 
 PLANE\_MASTER
 
 . An object with this flag will act as a "parent"
for everything else on the plane. All other sprites on the plane will be
grouped together and rendered on a temporary drawing surface, and then the
plane master's
 
 color
 
 ,
 
 transform
 
 , and
 
 filters
 
 will
be applied.
 



 A plane master does not, however, get an icon or maptext of its own;
they're simply ignored. It can have overlays added to the group.
 


### 
 Advanced topics



 There are other topics not covered in this article, such as
 [render targets](#/atom/var/render_target) 
 and special map formats.
Any details on how those features impact rendering are discussed in their
own articles.
 




---
Side-view maps
----------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[pixel\_w var (atom)](#/atom/var/pixel_w) 

[pixel\_z var (atom)](#/atom/var/pixel_z) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[Isometric maps](#/{notes}/isometric) 

[Topdown maps](#/{notes}/topdown) 

[HUD](#/{notes}/HUD) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[TOPDOWN\_LAYER](#/{notes}/topdown_layer) 















 The side-view map format is used for 3/4 perspective, where the map is
basically similar to a top-down view but is usually foreshortened. Just like
with isometric projection, tiles that are closer to the bottom of the screen
are considered to be closer to the viewer. This is a form of pseudo-3D in
which the 2D icons used by BYOND can be arranged in a way to give the
appearance of three dimensions.
 



 It is important to remember that this is an illusion of 3D, not real 3D.
 



 The
 
 layer
 
 var behaves much the same way it does in
 
 ISOMETRIC\_MAP
 
 mode.See
 [isometric maps](#/{notes}/isometric) 
 for more information.
 



 When using this mode you may want to use a foreshortened
 
 world.icon\_size
 
 , like a 32x24 format instead of 32x32 for example,
and use taller icons for any vertical structures like walls or buildings. If
you set
 
 world.icon\_size
 
 to use foreshortening, then
 
 pixel\_y
 
 (or
 
 pixel\_x
 
 , depending on the orientation of client.dir) will be
adjusted for you; the same applies to
 
 step\_x
 
 and
 
 step\_y
 
 .
For example, with
 
 world.icon\_size
 
 set to
 
 "64x32"
 
 , the
 *physical* 
 tile—what you would see if you were to look at it
straight down from above— is considered to be 64x64, so you would need
 
 pixel\_y=64
 
 or
 
 step\_y=64
 
 to offset by a whole tile. This
adjustment does not apply to screen objects,
 
 pixel\_w
 
 , or
 
 pixel\_z
 
 .
 




---
Tiled icons
-------------




**See also:** 


[icon](#/icon) 

[procs (icon)](#/icon/proc) 

[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[Big icons](#/{notes}/big-icons) 







 In BYOND 3.0, any file like a large .bmp would be treated like a regular
icon that had been broken up into several tile-sized icon states. All tiles
then were 32x32 pixels. An image that was 100x100 would therefore take at
least 4x4 tiles to display. The icon was padded to the right and the top with
blank space to become an even multiple of 32x32, and then broken up into
sections. The lower left section was given an icon\_state of
 
 "0,0"
 
 ,
the next to the right was
 
 "1,0"
 
 , and so on, up to the upper right
which was
 
 "3,3"
 
 . Another icon state, a 32x32 thumbnail of the big
image, was also included.
 



 BYOND 4.0 expanded on this concept by allowing icons to be defined that had
individual graphics bigger than 32x32, and it would break each one up into
tiles just like 3.0 did. If an icon had a state called
 
 "open"
 
 then it
might break down into
 
 "open 0,0"
 
 ,
 
 "open 1,0"
 
 , and so on,
while the actual
 
 "open"
 
 state would be a thumbnail image. To show the
whole image, you would have to have a separate atom or overlay for each
individual tile.
 



 In newer versions, breaking big icons into tiles is no longer done by
default. Instead, icons are shown and manipulated in their
 [native size](#/{notes}/big-icons) 
 . To use the old method of breaking
icons into tiles, set
 
 world.map\_format
 
 to
 
 TILED\_ICON\_MAP
 
 .
This is the default for all projects compiled before version 455.
 



 When using tiled icons, there are some important things to note:
 


* You need to use extra atoms or overlays to show any icon bigger than a
 single tile, where each atom/overlay shows an individual tile-sized piece
 of the big icon.
* The icon\_state names of each tile are always the original name followed
 by a space, followed by x,y tile coordinates such as 0,0 or 2,1, so the
 northeast corner of
 
 "flag"
 
 might for instance be
 
 "flag 3,2"
 
 . If the original icon\_state had no name, the space is
 left out and only the x,y coordinates are used.
* Every icon's size is a multiple of world.icon\_size. If an icon of an
 incompatible size is used, it will be padded to the nearest full tile
 size.
* Crop()
 
 and
 
 Scale()
 
 always pad their results to the
 nearest full tile size.
* icon.Insert()
 
 can insert a single-tile icon into a multi-tiled
 big icon using the appropriate icon\_state; e.g., inserting into
 
 "door 0,0"
 
 will replace the southwest corner of the
 
 "door"
 
 state.
* Using the
 
 icon()
 
 proc, you can extract a single tile from a
 multi-tiled big icon.



 This example shows a big icon being applied to an atom in tiled mode, as
overlays:
 


### 
 Example:



 // icon is 3 tiles wide by 2 high
icon\_state = "0,0"

// A temporary object used for the overlays
var/obj/O = new
O.icon = icon
O.layer = FLOAT\_LAYER

for(var/tile\_y=0, tile\_y<2, ++tile\_y)
 for(var/tile\_x=0, tile\_x<3, ++tile\_x)
 if(tile\_x && tile\_y)
 O.pixel\_x = tile\_x \* 32
 O.pixel\_y = tile\_y \* 32
 O.icon\_state = "[tile\_x],[tile\_y]"
 overlays += O
 


---
Topdown maps
--------------




**See also:** 


[map\_format var (world)](#/world/var/map_format) 

[icon\_size var (world)](#/world/var/icon_size) 

[dir var (client)](#/client/var/dir) 

[layer var (atom)](#/atom/var/layer) 

[plane var (atom)](#/atom/var/plane) 

[screen\_loc var (movable atoms)](#/atom/movable/var/screen_loc) 

[Big icons](#/{notes}/big-icons) 

[HUD](#/{notes}/HUD) 

[Isometric maps](#/{notes}/isometric) 

[Side-view maps](#/{notes}/side) 

[Understanding the renderer](#/{notes}/renderer) 













 By default, BYOND displays all maps in top-down format, so
 
 world.map\_format
 
 is set to
 
 TOPDOWN\_MAP
 
 unless you say
otherwise. This view means players are looking down on the map, and
"north" corresponds to the top of their screen. (This can be changed by
setting
 
 client.dir
 
 .)
 



 A related map\_format, used by older games, is
 
 TILED\_ICON\_MAP
 
 . This
is also topdown but it handles icons differently.
 



 In this form, the
 
 layer
 
 var behaves exactly as you would expect:
Icons with a lower layer are drawn beneath icons with a higher layer. The only
exception is when you use
 [big icons](#/{notes}/big-icons) 
 , which will
be drawn above any other icons on the same layer. Also an atom's underlays will
be drawn behind it unless their layer is changed, and its overlays will draw in
front of it unless otherwise stated.
 



 Topdown mode also guarantees that
 
 world.view
 
 or
 
 client.view
 
 will set the exact screen size used by the HUD, except for HUD objects that
appear outside of the normal bounds.
 



 Screen objects (also called the HUD) cannot be intermixed with topdown
icons. They will appear on top of other icons, unless using a lower plane or a
special layer like
 
 BACKGROUND\_LAYER
 
 .
 




---
TOPDOWN\_LAYER
----------------




**See also:** 


[layer var (atom)](#/atom/var/layer) 

[map\_format var (world)](#/world/var/map_format) 

[BACKGROUND\_LAYER](#/{notes}/BACKGROUND_LAYER) 

[EFFECTS\_LAYER](#/{notes}/EFFECTS_LAYER) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







 TOPDOWN\_LAYER is a special high value that can be added to the regular layer
of any atom. This is only available when using a non-topdown world.map\_format,
such as isometric mapping.
 



 The purpose of this value is to make an atom appear as if it belongs in a
top-down map, when using a map\_format other than TOPDOWN\_MAP or TILED\_ICON\_MAP.
This can be handy for title screens, or for special battle maps or the inside
of a building in an RPG.
 



 When using this special layer, it should be added to the layer an atom
normally uses. For instance a turf should have a layer of TOPDOWN\_LAYER +
TURF\_LAYER. Usually you will want one part of the map to have TOPDOWN\_LAYER,
and for players to be unable to walk to there from the regular map. Mixing
topdown icons and icons in the normal map\_format in view of each other could
look very strange. For safety's sake, the easiest thing to do is to keep them
on separate z layers.
 



 This can be mixed with EFFECTS\_LAYER. Anything in TOPDOWN\_LAYER will
display on top of EFFECTS\_LAYER, and TOPDOWN\_LAYER + EFFECTS\_LAYER will be
above both.
 



 This can also be mixed with BACKGROUND\_LAYER, which takes priority over
everything else.
 



 Images or overlays with FLOAT\_LAYER can be left alone. They will
automatically have the same layer as whatever atom they are attached to.
 




---
Unicode
---------




**See also:** 


[text](#/DM/text) 



 BYOND was originally written to handle 8-bit ("ANSI") characters only.
However as time has marched on, Unicode has become ubiquitous for supporting
multiple languages, special characters, and emojis. To adapt to this, BYOND
now supports Unicode.
 



 When ANSI was king, every character was exactly one byte in width, because
the only valid characters were between 1 and 255. (And technically, BYOND
reserved 255 for its own use.) Now, BYOND uses an encoding called UTF-8 to
store characters that can't fit in one byte.
 



 UTF-8 breaks up characters with codes of 128 or higher into multiple
bytes, like so:


| 
 Character code
  | 
 Size in bytes
  |
| --- | --- |
| 
 0 - 0x7F
  | 
 1
  |
| 
 0x80 - 0x7FF
  | 
 2
  |
| 
 0x800 - 0xFFFF
  | 
 3
  |
| 
 0x10000 - 0x10FFFF
  | 
 4
  |


### 
 Text handling



 Importantly, BYOND's text procs are based on the byte position, not the
character position which may be lower. In other words,
 
 length("abcdéfg")
 
 is greater than 7; it's 8, because
 
 é
 
 takes up 2 bytes in UTF-8. That also means
 
 f
 
 is at
position 7, not position 6.
 



 Why do the text procs work with byte position instead of character
position? Because ultimately, it's faster. Going by character position would
require counting every byte in a string (at least when it uses UTF-8) until
the right character position was found. This would be detrimental to
performance in most cases.
 



 For the most part, this distinction should be fairly invisible to you.
Most code isn't going to encounter problems, but if you do a lot of text
processing you should be aware of it.
 



 In particular,
 [text2ascii()](#/proc/text2ascii) 
 returns the Unicode value at a specific position, which may cover several
bytes. If you loop through a string calling this proc for each character,
you'll have to make adjustments for cases when multiple bytes have been
read.
 



 The read-only
 
 []
 
 index operator also uses byte positions.
 



 If you read a byte or cut text at an inappropriate point, any broken
characters resulting from the cut will be turned into the Unicode
replacement character � which is 0xFFFD.
 


### 

 \_char
 
 procs



 Most of the text handling procs have slower
 
 \_char
 
 versions (e.g.,
 
 copytext\_char
 
 ) that use character positions instead of byte
positions.
 



 These should be used sparingly if at all; whenever it's possible to use
byte positions, you should. When you do use a
 
 \_char
 
 version of a
proc, prefer using
 
 -offset
 
 instead of
 
 length\_char(text)-offset
 
 for positions near the end of the string.
Most text procs allow negative position values that count backwards from the
end, and counting a small number of characters backward is faster than
counting a lot of characters going forward.
 


### 
 Old code



 Code written in ANSI will be up-converted to UTF-8 by Dream Maker, based on
your current locale when the code is loaded.
 




---


User interface skins
----------------------




**See also:** 


[winset proc](#/proc/winset) 

[winget proc](#/proc/winget) 

[output proc](#/proc/output) 

[winclone proc](#/proc/winclone) 

[winexists proc](#/proc/winexists) 

[winshow proc](#/proc/winshow) 

[controls](#/{skin}/control) 

[parameters](#/{skin}/param) 

[macros (skin)](#/{skin}/macros) 

[commands](#/{skin}/commands) 












 BYOND games used to have very limited interface options, all effectively
sharing the same layout. In BYOND 4.0, skins were introduced, allowing
developers more control over the layout.
 



 A skin consists of
 [macro sets](#/{skin}/macros) 
 for
keyboard/gamepad input, menus, and windows and/or panes. All of these are
considered
 [controls](#/{skin}/control) 
 that a game can interact with
via
 [winset()](#/proc/winset) 
 ,
 [winget()](#/proc/winget) 
 ,
 [output()](#/proc/output) 
 , and a few other procs.
 



 About the simplest possible skin is a single window with a single
 [map control](#/{skin}/control/map) 
 , and a single macro set.
 




---
client commands
-----------------



 Several commands can be executed on the client that are not verbs, but raw instructions for Dream Seeker.
 




 .winset "
 *[control.param=value;...]* 
 "
 

 Sets parameters in response to a menu or button command (or a manually typed command). You can set more than one by separating them with semicolons. This command has a more complex format for conditional instructions (see below).
 

 .output
 *control* 
*text* 


 Sends output to a control. The text does not need quotes, but backslashes, newlines, and tabs should be escaped with a backslash. This works similarly to the
 [output()](#/proc/output) 
 proc.
 

 .options
 

 Shows the Options & Messages box.
 

 .reboot
 

 Reboots the world, when Dream Seeker is also acting as a server.
 

 .reconnect
 

 Reconnects to the same world.
 

 .host
 

 Opens hosting options box, when Dream Seeker is also acting as a server.
 

 .profile
 

 Opens the profiler. On a remote connection you may not have access to profile server procs, but you can look at the client and network profilers.
 

 .screenshot
 

 Saves a screenshot of the map. If there's more than one map control, the default map is used.
 

 .screenshot auto
 

 Saves a screenshot of the map, but does not prompt for a filename. The file will be saved in the client's user directory in BYOND/screenshots.
 

 .gamepad-mapping
 

 Opens the gamepad mapping dialog. Helpful if the user's gamepad is not supported or not configured to their liking.
 

 .command
 

 Prompts the user to enter a command, which can be one of these commands as well.
 

 .configure
 *option* 
*value* 


 Toggle certain Dream Seeker config options, such as
 
 .configure graphics-hwmode on
 
 . The only supported options you can use are
 
 graphics-hwmode
 
 ,
 
 sound
 
 , and
 
 delay
 
 which is an old mechanism for dynamically adapting to network delay. (Usually the
 
 delay
 
 is reset to 0.)
 

 .quit
 

 Closes Dream Seeker.
 

### 
 Conditional Winset



 The
 
 .winset
 
 command allows you to use conditional expressions,
like so:
 



```
condition ? choice1 : choice2
```


 The condition is the same as any other parameter you might use in
 
 .winset
 
 , but instead of setting the parameter, it checks to see if
it's true. If so, then the parameters in
 
 choice1
 
 will be set.
Otherwise, the parameters in
 
 choice2
 
 are set. This example makes the
window background red if bigbutton is checked.
 



```
.winset "bigbutton.is-checked=true ? window.background-color=#ff0000 : window.background-color=none"
```


 If you want to look for values that don't match instead of values that do,
use
 
 !=
 
 instead of
 
 =
 
 in the condition.
 



```
.winset "bigbutton.is-checked!=false ? window.background-color=#f00 : window.background-color=none"
```


 The
 
 choice2
 
 item is optional.
 



```
.winset "bigbutton.is-checked=true ? window.background-color=#f00"
```


 Because it's often useful to do more than one thing at a time,
 
 choice1
 
 and
 
 choice2
 
 don't have to be just one parameter. You
can use multiple parameters, but they are separated with a space instead of a
semicolon. (A semicolon indicates the conditional expression is over.)
 



```
.winset "bigbutton.is-checked=true ? window.text-color=#fff window.background-color=#f00 : window.text-color=none window.background-color=none"
```

### 
 Embedded Winget



 Commands that are initiated by the skin (like button.command, map.on-show,
etc.) have a special syntax that allows you to include information that would
normally require a winget call. By including
 
 [[
 *something* 
 ]]
 
 in
the command, the double-bracketed text will be replaced by the result of
running a winget on that parameter.
 



 A value of
 
 [[id.parameter]]
 
 will run a winget on the control with
the given ID. Just using
 
 [[parameter]]
 
 will run a winget for the
control that initiated this command. You can also use
 
 parent
 
 in place
of the ID to do something with the parent of the control, or
 
 parent.id
 
 for access to a sibling control. Position and size parameters can be further
broken down by appending
 
 .x
 
 or
 
 .y
 
 to get at the numbers
directly.
 



 Several commands already support some special cases like
 
 [[\*]]
 
 or
 
 [[width]]
 
 or such, where the special-case values are relevant to the
command. An example is that in
 
 on-size
 
 the value of
 
 [[\*]]
 
 is
a size value. The Any macro, gamepad macros, and mouse macros, also support this
syntax; see
 [macros](#/{skin}/macros) 
 for more info.
 



 You can choose how embedded wingets get formatted by following the value with
 
 as
 
 and a type, such as
 
 [[window.size as string]]
 
 . There are
several types you can use, and different types of parameters get formatted differently:
 




 arg
 

 Value is formatted as if it's an argument on a command line. Numbers are left alone; booleans are 0 or 1; size and position have their X and Y values separated by a space; pretty much everything else is DM-escaped and enclosed in quotes.
 

 escaped
 

 DM-escape the value as if it's in a quoted string but do not include the quotes. Size and position values both use
 
 ,
 
 to separate their X and Y values.
 

 string
 

 Value is formatted as a DM-escaped string with surrounding quotes.
 

 params
 

 Format value for a URL-encoded parameter list (see
 [list2params](#/proc/list2params) 
 ), escaping characters as needed.
 

 json
 

 JSON formatting. Numbers are left unchanged; size or position values are turned into objects with x and y items; boolean values are
 
 true
 
 or
 
 false
 
 .
 

 json-dm
 

 JSON formatting, but DM-escaped so it can be included in a quoted string. Quotes are not included.
 


 The
 
 arg
 
 type is the default, unless the
 
 [[
 
*...* 

 ]]
 
 expression has double quotes on both sides, in which case
 
 escaped
 
 is the
default.
 




---
controls (skin)
-----------------




**Control types:** 


[Bar](#/{skin}/control/bar) 
 : A progress bar or slider
 
[Browser](#/{skin}/control/browser) 
 : A browser
 
[Button](#/{skin}/control/button) 
 : A pushbutton or toggle button
 
[Child](#/{skin}/control/child) 
 : A container holding one or two panes, with a movable splitter
 
[Grid](#/{skin}/control/grid) 
 : For table-like or list-like output
 
[Info](#/{skin}/control/info) 
 : Classic BYOND statpanel
 
[Input](#/{skin}/control/input) 
 : Command input or other user-entered text
 
[Label](#/{skin}/control/label) 
 : Non-interactive text label
 
[Main](#/{skin}/control/main) 
 : A window or pane that holds other controls
 
[Macro](#/{skin}/control/macro) 
 : A
 [keyboard/gamepad/mouse macro](#/{skin}/macros) 

[Map](#/{skin}/control/map) 
 : The game map display
 
[Menu](#/{skin}/control/menu) 
 : An item in a drop-down menu
 
[Output](#/{skin}/control/output) 
 : Text output
 
[Tab](#/{skin}/control/tab) 
 : A tab control holding multiple panes, showing one at a time
 
















**Parameters common to all controls:** 


[id](#/{skin}/param/id) 

[is-disabled](#/{skin}/param/is-disabled) 

[parent](#/{skin}/param/parent) 

[saved-params](#/{skin}/param/saved-params) 

[type](#/{skin}/param/type) 






**Positionable controls only (not Macro or Menu):** 


[anchor1, anchor2](#/{skin}/param/anchor) 

[background-color](#/{skin}/param/background-color) 

[border](#/{skin}/param/border) 

[drop-zone](#/{skin}/param/drop-zone) 

[flash](#/{skin}/param/flash) 

[focus](#/{skin}/param/focus) 

[font-family](#/{skin}/param/font-family) 

[font-size](#/{skin}/param/font-size) 

[font-style](#/{skin}/param/font-style) 

[is-visible](#/{skin}/param/is-visible) 

[is-transparent](#/{skin}/param/is-transparent) 

[on-size](#/{skin}/param/on-size) 

[pos](#/{skin}/param/pos) 

[right-click](#/{skin}/param/right-click) 

[size](#/{skin}/param/size) 

[text-color](#/{skin}/param/text-color) 

















### 
 Creating/Destroying at runtime



 Controls can be created or deleted at runtime. (Only controls you created
during runtime may be deleted.) To create a control, call
 [winset()](#/proc/winset) 
 using the
 [id](#/{skin}/param/id) 
 of the new control, and the
parameter list should include
 [type](#/{skin}/param/type) 
 ,
 [parent](#/{skin}/param/parent) 
 , and probably also
 [pos](#/{skin}/param/pos) 
 ,
 [size](#/{skin}/param/size) 
 , and any
 [anchors](#/{skin}/param/anchor) 
 .
 



 To delete the control again, set its
 
 parent
 
 to a blank value.
 



 Menu items and macros work similarly, except they have no positional info.
For those, the
 [name](#/{skin}/param/name) 
 parameter is
important when you create them, and you will either need
 [command](#/{skin}/param/command) 
 or (for macros)
 [map-to](#/{skin}/param/map-to) 
 to do anything with them.
 




---
bar control (skin)
--------------------



 A progress bar or interactive slider. This can be made to use several different orientations. Its
 
 value
 
 can be read or set as a percentage from 0 to 100.
 




**Bar-specific parameters:** 


[angle1, angle2](#/{skin}/param/angle) 

[bar-color](#/{skin}/param/bar-color) 

[dir](#/{skin}/param/dir) 

[is-slider](#/{skin}/param/is-slider) 

[on-change](#/{skin}/param/bar-color) 

[value](#/{skin}/param/value) 

[width](#/{skin}/param/width) 










---
browser control (skin)
------------------------



 A browser panel integrated into the skin.
 




**Browser-specific parameters:** 


[auto-format](#/{skin}/param/auto-format) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[show-history](#/{skin}/param/show-history) 

[show-url](#/{skin}/param/show-url) 

[use-title](#/{skin}/param/use-title) 








 Browsers are capable of displaying HTML documents, and can also interact with the skin.
 


### 
 Browsers and popups



 A longstanding behavior of BYOND is the ability to create a new browser window by sending an extra argument to the
 [browse()](#/proc/browse) 
 proc. Since the advent of skins in BYOND 4.0, this behavior was kept. When you create a new browser popup, the window name you specify for the popup is used for the name of a new
 [window control](#/{skin}/control/main) 
 , and within that window there will be a new browser control simply called
 
 browser
 
 .
 



 If you want to interact with the new browser, its full "decorated"
 [id](#/{skin}/param/id) 
 is
 
*windowname* 
 .browser
 
 .
 


### 
 Running JavaScript from DM



 Sending
 [output()](#/proc/output) 
 to a browser will send a document to display there, but if you follow the browser's control name with a colon and a function name, you can call a JavaScript function in the document displayed within that browser.
 


### 
 Example:



 var/list/info = list("name"="fridge", "power"=12)
// send {"name":"fridge","power":12} to a JavaScript function
usr << output(url\_encode(json\_encode(info)), "mybrowser:myJSfunction")
 

 The text that you send as output will be parsed like URL parameters, where mutliple arguments to the function are separated by
 
 &
 
 or
 
 ;
 
 , which is why
 [url\_encode()](#/proc/url_encode) 
 is wrapped around the
 [json\_encode()](#/proc/json_encode) 
 call in this example.
 


### 
 Winset and Winget via JavaScript



 To allow better access to the skin via JavaScript, two new URL formats have been added. If
 
 window.location
 
 is set to these from JavaScript in a browser control, they can be used to interact directly.
 



**Winset URL:** 

 byond://winset?id=
 *[control ID]* 
 &
 *[property]* 
 =
 *[value]* 
 &...
 




 This works like an ordinary
 [winset()](#/proc/winset) 
 call from the server. If
 
 id
 
 is omitted, it's the same as a winset with a null ID. You can also leave the
 
 id
 
 blank if you use "fully decorated" property names such as
 
 mybutton.is-checked
 
 instead of just
 
 is-checked
 
 .
 



 Any text you use other than letters, numbers, hyphens, commas, and periods should be encoded via the
 
 encodeURIComponent()
 
 function in JavaScript.
 



**Winget URL:** 

 byond://winget?callback=
 *[callback function]* 
 &id=
 *[control ID/list]* 
 &property=
 *[property/list]* 





 In this winget, the IDs and properties you want can be separated by commas if you want to retrieve more than one. The winget operation works via a callback function you must define in JavaScript. The callback is given just one argument, a JavaScript object with all of the properties you requested. For example, this URL:
 



```
byond://winget?callback=wgcb&id=button1&property=is-checked,size,background-color
```


 ...might send this to the callback function wgcb:
 



```
{
    "is-checked": true,
    "size": {
        "x": 60,
        "y": 20
    },
    "background-color": {
        "value": "none",
        "isDefault": true,
        "red": 236,
        "green": 233,
        "blue": 216,
        "alpha": 255,
        "css": "#ece9d8"
    }
}

```


 The property names will be in the same format you would expect from
 [winget()](#/proc/winget) 
 , so when you're looking at multiple elements' properties, you'll get the full names in
 
 id.property
 
 format. The values are always sent back in a convenient form for JavaScript to work with; in the case of size, position, and color these will always be objects.
 



 An optional
 
 control
 
 parameter for the winget call can be used if you want to send data to a callback in a different browser control.
 




---
button control (skin)
-----------------------



 A button that can be pressed to run a
 [command](#/{skin}/commands) 
 , or possibly toggled.
 




**Button-specific parameters:** 


[button-type](#/{skin}/param/button-type) 

[command](#/{skin}/param/command) 

[group](#/{skin}/param/group) 

[image](#/{skin}/param/image) 

[is-checked](#/{skin}/param/is-checked) 

[is-flat](#/{skin}/param/is-flat) 

[text](#/{skin}/param/text) 










---
child control (skin)
----------------------



 A container that can hold one or two
 [panes](#/{skin}/control/main) 
 . If it holds two panes, a splitter may appear between them. This control can therefore be used to subdivide a window or pane into smaller units.
 




**Child-specific parameters:** 


[is-vert](#/{skin}/param/is-vert) 

[left, top](#/{skin}/param/left) 

[lock](#/{skin}/param/lock) 

[right, bottom](#/{skin}/param/right) 

[show-splitter](#/{skin}/param/show-splitter) 

[splitter](#/{skin}/param/splitter) 









---
grid control (skin)
---------------------



 A grid that contains multiple cells that can show various kinds of output data.
 




**Grid-specific parameters:** 


[cell-span](#/{skin}/param/cell-span) 

[cells](#/{skin}/param/cells) 

[current-cell](#/{skin}/param/current-cell) 

[enable-http-images](#/{skin}/param/enable-http-images) 

[highlight-color](#/{skin}/param/highlight-color) 

[is-list](#/{skin}/param/is-list) 

[line-color](#/{skin}/param/line-color) 

[link-color](#/{skin}/param/link-color) 

[show-lines](#/{skin}/param/show-lines) 

[show-names](#/{skin}/param/show-names) 

[small-icons](#/{skin}/param/small-icons) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 















 Sending output to a grid looks like this:
 


### 
 Example:



 // output to column 3, row 2
winset(usr, "thegrid", "current-cell=3,2")
usr << output("Text", "thegrid")

// or even easier:
usr << output("Text", "thegrid:3,2")

// when is-list is true:
usr << output("5th item", "thegrid:5")
 

 You can output an atom to the grid, which can be clicked, dragged, etc.
However, you should make sure that atom is
 *not* 
 temporary and will
persist until you no longer need it, or else the server may recycle it and
the object in the cell will either disappear or be impossible to interact
with anymore.
 



 There are some limitations to output in grid controls:
 


* Only one character style (font, color, bold, etc.) may appear within a single cell.
* A cell is either a link, or not.
* One image is allowed per cell.
* A cell can hold an object (atom), sent to it via the
 [output()
 
 proc](#/proc/output) 
 , which can be clicked, dragged, etc.; it will not act as a link.
* The same margin is used all around the cell, not different margins for left, right, top, bottom.
* There will always be a 1-pixel space for grid lines, whether they're shown or not.




---
info control (skin)
---------------------



 The classic BYOND statpanel, which contains both stat and verb tabs. This
is technically a 3-column grid with a variable number of rows.
 




**Info-specific parameters:** 


[allow-html](#/{skin}/param/allow-html) 

[highlight-color](#/{skin}/param/highlight-color) 

[multi-line](#/{skin}/param/multi-line) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[on-tab](#/{skin}/param/on-tab) 

[prefix-color](#/{skin}/param/prefix-color) 

[suffix-color](#/{skin}/param/suffix-color) 

[tab-background-color](#/{skin}/param/tab-background-color) 

[tab-font-family, tab-font-size, tab-font-style](#/{skin}/param/tab-font) 

[tab-text-color](#/{skin}/param/tab-text-color) 













 Output to a statpanel is done via the
 [stat()](#/proc/stat) 
 and
 [statpanel()](#/proc/statpanel) 
 procs, during
 [mob/Stat()](#/atom/proc/stat) 
 .
 



 The same limitations that apply to
 [grid](#/{skin}/control/grid) 
 output apply here.
 




---
input control (skin)
----------------------



 A text box into which the user can type. By default this is used for sending
 [commands](#/{skin}/commands) 
 , but it can be used for other purposes as well.
 




**Input-specific parameters:** 


[command](#/{skin}/param/command) 

[is-password](#/{skin}/param/is-password) 

[multi-line](#/{skin}/param/multi-line) 

[no-command](#/{skin}/param/no-command) 

[on-blur](#/{skin}/param/on-blur) 

[on-focus](#/{skin}/param/on-focus) 

[text](#/{skin}/param/text) 









 Note that when in "standard" mode of accepting user commands, built-in verbs like
 
 .click
 
 , or local commands like
 
 .winset
 
 , are not accepted when typed in. This kind of command can still be entered manually through the Client menu of the Options & Messages window.
 




---
label control (skin)
----------------------



 A text label that appears on the skin.
 




**Label-specific parameters:** 


[align](#/{skin}/param/align) 

[allow-html](#/{skin}/param/allow-html) 

[image](#/{skin}/param/image) 

[image-mode](#/{skin}/param/image-mode) 

[keep-aspect](#/{skin}/param/keep-aspect) 

[text](#/{skin}/param/text) 

[text-wrap](#/{skin}/param/text-wrap) 










---
macro control (skin)
----------------------



 A
 [keyboard/gamepad/mouse macro](#/{skin}/macros) 
 , usually designed to run a
 [command](#/{skin}/commands) 
 . The control is a means of interacting with the macro as an object, allowing some of its properties to be changed at runtime.
 




**Macro-specific parameters:** 


[command](#/{skin}/param/command) 

[map-to](#/{skin}/param/map-to) 

[name](#/{skin}/param/name) 






---
main control (skin)
---------------------



 A container for other controls. The Main control takes two forms: a window or a pane.
 



 A window exists independently and can be moved around on the screen. A pane has to be used within another container control such as a
 [Child](#/{skin}/control/child) 
 or
 [Tab control](#/{skin}/control/tab) 
 .
 




**Main-specific parameters:** 


[icon](#/{skin}/param/icon) 

[image](#/{skin}/param/image) 

[image-mode](#/{skin}/param/image-mode) 

[inner-size](#/{skin}/param/inner-size) 

[is-pane](#/{skin}/param/is-pane) 

[keep-aspect](#/{skin}/param/keep-aspect) 

[outer-size](#/{skin}/param/outer-size) 

[title](#/{skin}/param/title) 

[on-status](#/{skin}/param/on-status) 










**Windows only:** 


[alpha](#/{skin}/param/alpha) 

[can-close](#/{skin}/param/can-close) 

[can-minimize](#/{skin}/param/can-minimize) 

[can-resize](#/{skin}/param/can-resize) 

[is-maximized](#/{skin}/param/is-maximized) 

[is-minimized](#/{skin}/param/is-minimized) 

[macro](#/{skin}/param/macro) 

[menu](#/{skin}/param/menu) 

[on-close](#/{skin}/param/on-close) 

[statusbar](#/{skin}/param/statusbar) 

[titlebar](#/{skin}/param/titlebar) 

[transparent-color](#/{skin}/param/transparent-color) 













**Panes only:** 


[can-scroll](#/{skin}/param/can-scroll) 



 The font parameters have no impact on a window's statusbar or titlebar; those are drawn by the operating system.
 




---
map control (skin)
--------------------



 A map that will display icons from the game.
 




**Map-specific parameters:** 


[icon-size](#/{skin}/param/icon-size) 

[letterbox](#/{skin}/param/letterbox) 

[on-hide](#/{skin}/param/on-hide) 

[on-show](#/{skin}/param/on-show) 

[style](#/{skin}/param/style) 

[text-mode](#/{skin}/param/text-mode) 

[view-size](#/{skin}/param/view-size) 

[zoom](#/{skin}/param/zoom) 

[zoom-mode](#/{skin}/param/zoom-mode) 












---
menu control (skin)
---------------------



 A menu item, that when activate will run a
 [command](#/{skin}/commands) 
 .
 




**Menu-specific parameters:** 


[can-check](#/{skin}/param/can-check) 

[command](#/{skin}/param/command) 

[group](#/{skin}/param/group) 

[index](#/{skin}/param/index) 

[is-checked](#/{skin}/param/is-checked) 

[name](#/{skin}/param/name) 









---
output control (skin)
-----------------------



 Displays text output.
 




**Output-specific parameters:** 


[enable-http-images](#/{skin}/param/enable-http-images) 

[image](#/{skin}/param/image) 

[legacy-size](#/{skin}/param/legacy-size) 

[link-color](#/{skin}/param/link-color) 

[max-lines](#/{skin}/param/max-lines) 

[style](#/{skin}/param/style) 

[visited-color](#/{skin}/param/visited-color) 










---
tab control (skin)
--------------------



 A tab control, where each tab holds a different
 [pane](#/{skin}/control/main) 
 .
 




**Tab-specific parameters:** 


[current-tab](#/{skin}/param/current-tab) 

[multi-line](#/{skin}/param/multi-line) 

[on-tab](#/{skin}/param/on-tab) 

[tabs](#/{skin}/param/tabs) 







---
macros (skin)
---------------



 Macros are used to convert keyboard and gamepad events into actions. There
are two ways this works: A macro can run a command, or in some cases (such as
gamepad controls) it can be used to remap one control to another.
 



 A collection of macros is called a macro set, and the window currently in
use defines which macro set will be used via its
 [macro](#/{skin}/param/macro) 
 parameter.
 



 Macros can be changed at runtime. If a macro does not have an
 [id](#/{skin}/param/id) 
 , you can refer to it by its key
combination (
 [name](#/{skin}/param/name) 
 ). If you have a
macro set named
 
 macro1
 
 and have a
 
 Ctrl+E
 
 macro for instance,
you could use
 [winset()](#/proc/winset) 
 with
 
 "macro1.Ctrl+E"
 
 . See the
 [Macro
control](#/{skin}/control/macro) 
 for information on which parameters you can change with
 
 winset()
 
 .
 



 The
 
 name
 
 of the macro is actually the full key combination as it
would appear in the macro editor, like
 
 CTRL+E
 
 ,
 
 Space+REP
 
 , or
 
 Alt+Shift+F1
 
 . This is not case-specific and it doesn't matter where
you put modifiers like
 
 CTRL+
 
 ,
 
 SHIFT+
 
 , etc.
 


### 
 The Any macro



 Oftentimes it's desirable to keep track of key presses yourself rather than
have a hundred different macros defined. BYOND makes this possible via the
 
 Any
 
 and
 
 Any+UP
 
 macros, which respond to any key or gamepad
button.
 
 UP
 
 is the only allowed modifier for this macro, since other
modifier keys are handled by this same macro.
 



 Typically, you will want to use
 [set
instant=1](#/verb/set/instant) 
 on the verbs that will be tied to the Any macro, so that
keyboard input doesn't queue up and lag behind.
 



 In the
 [command](#/{skin}/param/command) 
 that goes with
this macro,
 
 [[\*]]
 
 will be replaced with the name of the key or gamepad
button that was pressed/released. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 


### 
 Mapping



 The
 [map-to](#/{skin}/param/map-to) 
 parameter is used
by
 **mappings** 
 , which are like macros but are used to convert gamepad
inputs easily and quickly to keyboard inputs. E.g.,
 
 GamepadLeft
 
 can
map to
 
 West
 
 which is the left arrow key. A set of default mappings
will be added automatically at runtime if you don't include any gamepad
mapping in your project.
 


### 
 Gamepads



 BYOND will support up to four gamepads, and breaks up their input into the
following categories:
 


* **Buttons:** 
 Buttons on the controller that are either pressed or not pressed.
* **Directions:** 
 Directions pressed on the D-pad, which act like buttons. Diagonals are also included.
* **D-pad:** 
 The D-pad itself, which can be used to read a
 [dir](#/atom/var/dir) 
 number.
* **Analog:** 
 The analog sticks (BYOND supports left and right).



 See the list of available macros below for information on how to harness
these inputs.
 



 To let a user configure their gamepad, you need to call the client-side
 
 .gamepad-mapping
 
[command](#/{skin}/commands) 
 . Or, if they
have access to the Options & Messages window and Dream Seeker's default
menus, they can reach it from there. However it's a good idea to make this
easy for them to find. Several common gamepads are already known by BYOND.
 



 There is also the
 
 GamepadRaw
 
 macro, which is similar
to
 
 Any
 
 in some ways and will avoid doing any processing (e.g.
checking for dead zones on the analog sticks) so you can handle all input
yourself.
 
 GamepadRaw
 
 does not rely on BYOND's controller
configuration, so it will not, for instance, know that button 0 should be
 
 GamepadFace1
 
 . See below for more information on how to use this
macro.
 


### 
 Mouse macros



 You can add macros (not local player-defined ones) for any of the mouse
input commands, thereby bypassing the normal mouse verbs. This can be helpful
for designing custom setups where you don't want to have to parse the normal
parameter string that provides most of the info, and instead want to provide
data directly to the verb. You will want
 
 set instant=1
 
 on any such
verb.
 



 Mouse macro commands use the
 
 [[...]]
 
 syntax to embed values, just
like
 [embedded wingets](#/{skin}/commands) 
 . These are the values you
can include in a mouse macro:


| 
 Embedded keyword
  | 
 Meaning
  |
| --- | --- |
| 
 action
  | 
 Name of the mouse action (e.g. MouseDown, MouseMove, etc.).
  |
| 
 src
  | 
 Object the mouse is touching, or dragging/dropping.
  |
| 
 loc
  | 
 Turf or statpanel that
 
 src
 
 is over; in a drag-drop you should split this into
 
 src.loc
 
 and
 
 over.loc
 
 .
  |
| 
 button
  | 
 Mouse button used for this action, if any:
 
 left
 
 ,
 
 middle
 
 , or
 
 right
 
 .
  |
| 
 drag
  | 
 Mouse button currently used for dragging.
  |
| 
 buttons
  | 
 Mouse buttons currently down or involved in this action, separated by commas.
  |
| 
 keys
  | 
 Modifier keys currently held (
 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
 
 ), separated by commas.
  |
| 
 over
  | 
 Object the mouse is over in a drag/drop operation.
  |
| 
 id
  | 
 Control ID; in a drag-drop you should split this into
 
 src.id
 
 and
 
 over.id
 
 .
  |
| 
 icon
  | 
 The icon offset (starting from 1,1 at the lower left) where the mouse action occurred.
 \*  |
| 
 tile
  | 
 The tile where the mouse action occurred, if relevant.
 \*  |
| 
 vis
  | 
 Pixel coordinates relative to the icon's position on screen (same as
 
 icon
 
 but without taking transform into account).
 \*  |
| 
 screen\_loc
  | 
 The regular
 
 screen\_loc
 
 cordinate string.
 \*  |
| 
 screen
  | 
 screen\_loc
 
 coordinates but entirely in pixels starting at 0,0 from lower left.
 \*  |
| 
 screen\_tile
  | 
 screen\_loc
 
 coordinates but only the tile number starting at 1,1.
 \*  |
| 
 screen\_offset
  | 
 screen\_loc
 
 coordinates but only the pixel offset from the tile, starting at 0,0.
 \*  |
| 
 delta
  | 
 Wheel changes in a mouse wheel command.
 \*  |
| 
 left
 
 ,
 
 right
 
 ,
 
 middle
  | 
 1 if this button is down or involved in this action, 0 otherwise
  |
| 
 shift
 
 ,
 
 ctrl
 
 ,
 
 alt
  | 
 1 if this modifier key is held, 0 otherwise
  |
| 
 link
  | 
 1 if the mouse is over a maptext link, 0 otherwise
  |
| \* 
 Coordinate values are comma-separated, but you can follow them with
 
 .x
 
 or
 
 .y
 
 to get the individual X and Y numbers.
  |



 An example mouse macro command might look like this:
 



> 
> 
> ```
> my-mousedown-verb [[src]] [[button]] "keys=[[keys as params]];drag=[[drag as params]]"
> ```
> 
> 



 In the example, the
 
 src
 
 value is a reference such as you would get
with the
 [ref()
 
 proc](#/proc/ref) 
 . It can be used as a verb
argument directly and won't be enclosed by quotes by default. The
 
 button
 
 value is a string and the default formatting will put quotes around it. The
 
 keys
 
 and
 
 drag
 
 values were given the
 
 as params
 
 format
specifier so they would behave as part of a
 [parameter
list](#/proc/list2params) 
 .
 



 In drag/drop actions, you can precede any value with
 
 src
 
 or
 
 over
 
 if there may be different information for the dragged object and
the mouseover object/location. This also applies to things like
 
 keys
 
 ,
which by default will be the currently held keys but you can use
 
 src.keys
 
 to refer to the values from when the drag began.
 


### 
 Available macros



 This is a list of all keys and gamepad events that can be used in macros.
 




| **Macro modifiers** 
 are part of the macro name, and control the conditions in which the macro will fire.
  |
| 
 Modifier
  | 
 Meaning
  |
| 
 SHIFT+
  | 
 This macro only counts if either Shift key is pressed.
  |
| 
 CTRL+
  | 
 This macro only counts if either Ctrl key is pressed.
  |
| 
 ALT+
  | 
 This macro only counts if either Alt key is pressed.
  |
| 
 +REP
  | 
 If a key/button is held down, this macro repeats.
  |
| 
 +UP
  | 
 This macro fires when the key/button is released.
  |
| **Keyboard keys** 
 are the garden-variety macros. (This list is abridged to exclude keys probably no one has.)
  |
| 
 Key
  | 
 Description
  |
| 
 A
 
 -
 
 Z
  | 
 Letter key
  |
| 
 0
 
 -
 
 9
  | 
 Number key
  |
| 
 Numpad0
 
 -
 
 Numpad9
  | 
 Numpad numbers
  |
| 
 North
  | 
 Up arrow
  |
| 
 South
  | 
 Down arrow
  |
| 
 East
  | 
 Right arrow
  |
| 
 West
  | 
 Left arrow
  |
| 
 Northwest
  | 
 Home key
  |
| 
 Southwest
  | 
 End key
  |
| 
 Northeast
  | 
 Page Up key
  |
| 
 Southeast
  | 
 Page Down key
  |
| 
 Center
  | 
 Center key (numpad)
  |
| 
 Return
  | 
 Enter / Return key
  |
| 
 Escape
  | 
 Esc key
  |
| 
 Tab
  | 
 Tab key
  |
| 
 Space
  | 
 Space bar
  |
| 
 Back
  | 
 Backspace key
  |
| 
 Insert
  | 
 Ins key
  |
| 
 Delete
  | 
 Del key
  |
| 
 Pause
  | 
 Pause key
  |
| 
 Snapshot
  | 
 Snapshot / Print Screen key
  |
| 
 LWin
  | 
 Left Windows key
  |
| 
 RWin
  | 
 Right Windows key
  |
| 
 Apps
  | 
 Apps key
  |
| 
 Multiply
  | 
 Multiply key
  |
| 
 Add
  | 
 Add key
  |
| 
 Subtract
  | 
 Subtract key
  |
| 
 Divide
  | 
 Divide / Slash key
  |
| 
 Separator
  | 
 Separator / Backslash key
  |
| 
 Shift
  | 
 Shift key (when not used as a modifier)
  |
| 
 Ctrl
  | 
 Ctrl key (when not used as a modifier)
  |
| 
 Alt
  | 
 Alt key (when not used as a modifier)
  |
| 
 VolumeMute
  | 
 Mute key
  |
| 
 VolumeUp
  | 
 Volume up key
  |
| 
 VolumeDown
  | 
 Volume down key
  |
| 
 MediaPlayPause
  | 
 Play/pause media key
  |
| 
 MediaStop
  | 
 Stop media key
  |
| 
 MediaNext
  | 
 Next track key
  |
| 
 MediaPrev
  | 
 Previous track key
  |
| **Special macros**  |
| 
**Any** 
 | 
 A special macro that can run a command on press/release of any key or gamepad button.
 
 UP
 
 is the only modifier allowed. In the command,
 
 [[\*]]
 
 is replaced with the key/button name.
 \*  |
| 
**GamepadRaw** 

\*  | 
 Captures raw input from a gamepad, without regard to the adjustments done by the Gamepad Setup dialog. In the command,
 
 [[id]]
 
 is replaced by the name of the button or axis changed ("Button0" through "Button15" and "Axis0" through "Axis11"),
 
 [[value]]
 
 is replaced with the value of the button or axis, and
 
 [[\*]]
 
 is equivalent to
 
 [[id]] [[value]]
 
 .
  |
| 
\* 
 If no gamepad mappings are included in a game's interface, the default mappings are used instead, which will map the Dpad buttons to the arrow keys. This will cause the Any macro to register both a gamepad directional button and the mapped key on the same press. If you plan on using macros to capture gamepad input, you may wish instead to map any one of the directional buttons to "None", which will override the default gamepad mappings completely.
  |
| **Gamepad buttons** 
† 
 can use another gamepad button as a modifier (but not CTRL, SHIFT, ALT), and can be mapped to one or two keyboard keys or mouse buttons.
  |
| 
 Button
  | 
 Description
  |
| 
 GamepadFace1
  | 
 A (Xbox), X (PS), bottom of diamond
  |
| 
 GamepadFace2
  | 
 B (Xbox), Circle (PS), right of diamond
  |
| 
 GamepadFace3
  | 
 X (Xbox), Square (PS), left of diamond
  |
| 
 GamepadFace4
  | 
 Y (Xbox), Triangle (PS), top of diamond
  |
| 
 GamepadL1
  | 
 Left top shoulder
  |
| 
 GamepadR1
  | 
 Right top shoulder
  |
| 
 GamepadL2
  | 
 Left bottom shoulder
  |
| 
 GamepadR2
  | 
 Right bottom shoulder
  |
| 
 GamepadSelect
  | 
 Select / Back
  |
| 
 GamepadStart
  | 
 Start / Forward
  |
| 
 GamepadL3
  | 
 Left analog click
  |
| 
 GamepadR3
  | 
 Right analog click
  |
| 
 Directional buttons: only one can pressed at a time, and the diagonal buttons are virtual.
  |
| 
 GamepadUp
  | 
 Up button
  |
| 
 GamepadDown
  | 
 Down button
  |
| 
 GamepadLeft
  | 
 Left button
  |
| 
 GamepadRight
  | 
 Right button
  |
| 
 GamepadUpLeft
  | 
 Up+left virtual button
  |
| 
 GamepadUpRight
  | 
 Up+right virtual button
  |
| 
 GamepadDownLeft
  | 
 Down+left virtual button
  |
| 
 GamepadDownRight
  | 
 Down+right virtual button
  |
| **Gamepad analog sticks** 
† 
 can have commands and/or map to
 
 GamepadDir
 
 ,
 
 GamepadDir4
 
 , or
 
 Mouse
 
 . They can use a gamepad button as a modifier. In a command,
 
 [[x]]
 
 and
 
 [[y]]
 
 are replaced by coordinates, and
 
 [[\*]]
 
 is replaced by both with a comma for separation.
  |
| 
 GamepadLeftAnalog
  | 
 Left analog stick
  |
| 
 GamepadRightAnalog
  | 
 Left analog stick
  |
| **Gamepad Dpads** 
†‡ 
 can have commands or are used as mapping targets for analog sticks. A gamepad button can be used as a modifier. In a command,
 
 [[\*]]
 
 is replaced by a direction number, which can be 0.
  |
| 
 GamepadDir
  | 
 Dpad, converted to one of the eight standard directions.
  |
| 
 GamepadDir4
  | 
 Dpad, converted to a cardinal direction.
  |
| 
† 
 All of the gamepad macros defined above apply to the first gamepad. BYOND can now support up to four gamepads, and you can replace Gamepad in the names above with Gamepad2, Gamepad3, or Gamepad4 to access them. Each gamepad also has its own raw macro (i.e., Gamepad2Raw).
 

‡ 
 If you use a Dpad macro like GamepadDir as a
 
 map-to
 
 target, you don't have to specify gamepad 2-4 in map-to; the mapping will automatically know that when Gamepad2LeftAnalog is mapped to GamepadDir, it means Gamepad2Dir.
  |
| **Mouse macros** 
 can have commands but not be used as mapping targets.
  |
| 
 MouseDown
  | 
 Mouse button pressed (replaces MouseDown verb)
  |
| 
 MouseUp
  | 
 Mouse button released (replaces MouseUp verb)
  |
| 
 MouseOver
  | 
 Mouse has moved over a new icon or entered/exited a control (replaces MouseEntered and MouseExited verbs)
  |
| 
 MouseMove
  | 
 Mouse has moved to a new pixel of the same icon (replaces MouseMove verb)
  |
| 
 MouseDrag
  | 
 Mouse has begin dragging or is over a new drop target (replaces MouseDrag verb)
  |
| 
 MouseDragMove
  | 
 Mouse is dragging and is over a new pixel of the same drop target (replaces MouseDrag verb in situations where MouseMove would apply)
  |
| 
 MouseDrop
  | 
 Mouse drag has been released over a target (replaces MouseDrop verb)
  |
| **Mouse targets** 
 can only be used as mapping targets for another macro.
  |
| 
 Mouse
  | 
 The mouse cursor, mappable by a gamepad analog stick.
  |
| 
 MouseLeftButton
  | 
 Left button, mappable by a gamepad button.
  |
| 
 MouseRightButton
  | 
 Right button, mappable by a gamepad button.
  |
| 
 MouseMiddleButton
  | 
 Middle button, mappable by a gamepad button.
  |




---


parameters (skin)
-------------------



 Controls can be interacted with via
 [winset()](#/proc/winset) 
 and
 [winget()](#/proc/winset) 
 to change or read various
parameters.
 



 Parameters come in a few different formats:
 


* Boolean:
 
 true
 
 or
 
 false
* Numeric: any number, sometimes allowing decimal or negative numbers
* String: text
* Position:
 *x* 

 ,
 
*y*
* Size:
 *width* 

 x
 
*height*
* Enumerated: one of several text choices, sometimes accepting numbers or true/false values as shortcuts



 The list of
 [all controls](#/{skin}/control) 
 which shows which
parameters are universal, and each individual control type lists additional
parameters that apply to that type specifically.
 



 Note: In any parameter's "Applies to" section, "all" refers to positionable
controls only, not Macro or Menu controls. Macro and Menu will be listed
separately if supported.
 




---
align parameter (skin)
------------------------




**See also:** 


[allow-html parameter](#/{skin}/param/allow-html) 




**Applies to:** 


[Label](#/{skin}/control/label) 




**Possible values:** 


 center
 
 left
 
 right
 
 top
 
 bottom
 
 top-left
 
 top-right
 
 bottom-left
 
 bottom-right
 











**Default value:** 


 center
 


 Default alignment of text/image, both horizontal and vertical.
 



 A BYOND direction flag like
 
 WEST
 
 may be assigned to this parameter, or 0 for center alignment.
 




---
allow-html parameter (skin)
-----------------------------




**Applies to:** 


[Label](#/{skin}/control/label) 

[Info](#/{skin}/control/info) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 Info control: Allow HTML tags to be used in
 [stat()](#/proc/stat) 
 info. The same limitations apply as to the
 [Grid control](#/{skin}/control/grid) 
 .
 



 Label control: Currently, the label control will not actually use the HTML; it will simply strip it out. Full support may appear in a later version.
 




---
alpha parameter (skin)
------------------------




**See also:** 


[transparent-color parameter](#/{skin}/param/transparent-color) 




**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 number
 



**Default value:** 


 255
 


 Opacity of the window, from 0 (invisible) to 255 (opaque).
 




---
anchor1, anchor2 parameters (skin)
------------------------------------




**See also:** 


[pos parameter](#/{skin}/param/pos) 

[size parameter](#/{skin}/param/size) 





**Applies to:** 


[All](#/{skin}/control) 
 (except
 [Main](#/{skin}/control/main) 
 )
 



**Format:** 


 none
 
*x* 
 ,
 *y* 





**Default value:** 


 none
 


 Anchors the control within the window or pane. If the anchor is not
 
 none
 
 , it is expressed as pecentages of the container's width and height. For example, an anchor of 100,100 means that the X and Y position are tied to the lower right of the container, and 50,0 is tied to the top center.
 



 Setting only
 
 anchor1
 
 will control the position of the control but won't affect its size.
 



 Setting
 
 anchor2
 
 as well will allow you to stretch the control as the container's size changes. You can think of this
 
 anchor1
 
 controlling the top left corner, and
 
 anchor2
 
 the bottom right corner.
 




---
angle1, angle2 parameters (skin)
----------------------------------




**See also:** 


[dir parameter](#/{skin}/param/dir) 

[width parameter](#/{skin}/param/width) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 number
 



**Default value:** 



 angle1
 
 : 0
 

 angle2
 
 : 180
 



 The angle of the bar control's arc when its
 [dir](#/{skin}/param/dir) 
 is
 
 clockwise
 
 or
 
 counterclockwise
 
 . Angles are measured clockwise from due north, so 0 is north, 90 is east, and so on.
 
 angle1
 
 is the beginning of the arc, and
 
 angle2
 
 is the end.
 




---
auto-format parameter (skin)
------------------------------




**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false (was once true in old versions)
 


 When true, the browser control will inject conditional scripting into HTML documents to make them behave nicer in very old browsers. However, it is unlikely there are any systems left that need this.
 




---
background-color parameter (skin)
-----------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[tab-background-color parameter](#/{skin}/param/tab-background-color) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 



 The control's background color. The exact way this applies depends on the control.
 




---
bar-color parameter (skin)
----------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[is-transparent parameter](#/{skin}/param/is-transparent) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 



 The color of the bar or slider.
 




---
border parameter (skin)
-------------------------




**Applies to:** 


[All](#/{skin}/control) 




**Possible values:** 


 none
 
 line
 
 sunken
 





**Default value:** 


 none
 


 Border type around the control or window. May not work the same in all controls.
 




---
button-type parameter (skin)
------------------------------




**See also:** 


[group parameter](#/{skin}/param/group) 

[is-checked parameter](#/{skin}/param/is-checked) 





**Applies to:** 


[Button](#/{skin}/control/button) 




**Possible values:** 


 pushbutton: press once
 
 pushbox: press to toggle
 
 checkbox: press to toggle, and displays a checkmark if checked
 
 radio: press to check, and other buttons with the same
 
 group
 
 will be unchecked
 






**Default value:** 


 pushbutton
 


 Changes the type of button.
 




---
can-check parameter (skin)
----------------------------




**See also:** 


[group parameter](#/{skin}/param/group) 

[is-checked parameter](#/{skin}/param/is-checked) 





**Applies to:** 


[Menu](#/{skin}/control/menu) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 If true, this menu item is toggled like a checkbox or radio button when clicked.
 




---
can-close parameter (skin)
----------------------------




**See also:** 


[on-close parameter](#/{skin}/param/on-close) 

[can-resize parameter](#/{skin}/param/can-resize) 

[titlebar parameter](#/{skin}/param/titlebar) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Allow the window to be closed, and also shows a system menu for the window.
 




---
can-minimize parameter (skin)
-------------------------------




**See also:** 


[can-resize parameter](#/{skin}/param/can-resize) 

[titlebar parameter](#/{skin}/param/titlebar) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Allow the window to be minimized.
 




---
can-resize parameter (skin)
-----------------------------




**See also:** 


[on-size parameter](#/{skin}/param/on-size) 

[can-minimize parameter](#/{skin}/param/can-minimize) 

[titlebar parameter](#/{skin}/param/titlebar) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Allow the window to be resized or maximized.
 




---
can-scroll parameter (skin)
-----------------------------




**See also:** 


[on-size parameter](#/{skin}/param/on-size) 

[size parameter](#/{skin}/param/size) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (pane only)
 



**Possible values:** 


 none
 
 horizontal
 
 vertical
 
 both
 






**Default value:** 


 none
 


 Allow this pane to retain its horizontal and/or vertical size and show scrollbars if necessary, instead of shrinking to fit the container.
 




---
command parameter (skin)
--------------------------




**See also:** 


[Commands](#/{skin}/commands) 




**Applies to:** 


[Button](#/{skin}/control/button) 

[Input](#/{skin}/control/input) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 







**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is activated.
 



 For the Input control, whatever the user types in follows this command. If your command starts with an exclamation point
 
 !
 
 , everything after the
 
 !
 
 is shown as a default prompt that may be cleared by the user.
 




---
cell-span parameter (skin)
----------------------------




**See also:** 


[cells parameter](#/{skin}/param/cells) 




**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


*columns* 
 ,
 *rows* 




**Default value:** 


 1x1
 


 The span of the current grid cell; it can be merged with cells to the right and down. If
 
 is-list
 
 is true, this setting is ignored. This setting is only available at runtime.
 




---
cells parameter (skin)
------------------------




**See also:** 


[cell-span parameter](#/{skin}/param/cell-span) 

[current-cell parameter](#/{skin}/param/current-cell) 

[is-list parameter](#/{skin}/param/is-list) 






**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


*columns* 
 ,
 *rows* 

*items* 





**Default value:** 


 0x0
 


 The number of columns and rows in the grid. Using -1 for either columns or rows will leave that value unchanged.
 



 If
 [is-list](#/{skin}/param/is-list) 
 is true, this value can be set to a single number.
 




---
current-cell parameter (skin)
-------------------------------




**See also:** 


[cell-span parameter](#/{skin}/param/cell-span) 

[cells parameter](#/{skin}/param/cells) 

[is-list parameter](#/{skin}/param/is-list) 






**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


*columns* 
 ,
 *rows* 

*items* 





**Default value:** 


 0x0
 


 The active cell. Any output sent to the grid, that is not sent to a specific cell, will go into this cell.
 



 If
 [is-list](#/{skin}/param/is-list) 
 is true, this value can be set to a single number.
 




---
current-tab parameter (skin)
------------------------------




**See also:** 


[on-tab parameter](#/{skin}/param/on-tab) 

[tabs parameter](#/{skin}/param/tabs) 





**Applies to:** 


[Tab](#/{skin}/control/tab) 




**Format:** 


 string
 


 The name of the
 [pane](#/{skin}/control/main) 
 in the active/default tab. If set to a pane that is not currently in this tab control, the pane by that name will be added as another tab.
 




---
dir parameter (skin)
----------------------




**See also:** 


[value parameter](#/{skin}/param/angle) 

[angle1, angle2 parameters](#/{skin}/param/angle) 

[width parameter](#/{skin}/param/width) 






**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Possible values:** 


 north
 
 south
 
 east
 
 west
 
 clockwise
 
 counterclockwise
 








**Default value:** 


 east
 


 The direction/orientation of the bar. As the
 [value](#/{skin}/param/value) 
 increases the bar will move further in this direction.
 



 Shorthand values like
 
 cw
 
 and
 
 ccw
 
 can be used, or also numerical BYOND directions.
 




---
drop-zone parameter (skin)
----------------------------




**See also:** 


[mouse handling](#/DM/mouse) 




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 



 true
 
 for
 [Grid](#/{skin}/control/grid) 
 ,
 [Info](#/{skin}/control/info) 
 ,
 [Map](#/{skin}/control/map) 


 false
 
 for everything else
 



 True if dragged objects may be dropped here. Default is true for Map, Info, and Grid controls, false for others. When in use, this will be the value of the
 
 over\_control
 
 argument in
 [MouseDrop()](#/client/proc/MouseDrop) 
 if you drop an atom here.
 



 Grids can also add
 
 drag-cell
 
 and
 
 drop-cell
 
 to mouse proc parameters. The mouse procs'
 
 src\_location
 
 and
 
 over\_location
 
 arguments are in the form
 
 "[column],[row]"
 
 (or
 
 "[item"]
 
 if
 [is-list](#/{skin}/param/is-list) 
 is true) when dragging to/from a grid cell.
 



 In Info controls,
 
 src\_location
 
 and
 
 over\_location
 
 in mouse procs will be the name of the statpanel tab.
 




---
enable-http-images parameter (skin)
-------------------------------------




**See also:** 


[small-icons parameter](#/{skin}/param/small-icons) 

[style parameter](#/{skin}/param/style) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Output](#/{skin}/control/output) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 Allows images to be pulled from the Web when using the
 
 <img>
 
 tag; otherwise only locally stored images can be shown.
 




---
flash parameter (skin)
------------------------




**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 number
 



**Default value:** 


 0
 


 Set to a positive number to make the window flash that many times, -1 to flash forever, and 0 to stop flashing.
 




---
focus parameter (skin)
------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[winget proc](#/proc/winget) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 This parameter is true if this control currently has focus.
 



 This is also a special read-only global parameter. Calling
 [winget()](#/proc/winget) 
 with no
 
 id
 
 and
 
 focus
 
 as the parameter will return the
 [id](#/{skin}/param/id) 
 of the currently focused control, if any.
 




---
font-family parameter (skin)
------------------------------




**See also:** 


[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 


 Leave blank to use the default font. This can be used for CSS-style fallback fonts, e.g. "Arial,Helvetica".
 



 You can include fonts in your resource file, making them available to the client, like so:
 



 var/list/extra\_resources = list(\
 'myfont.ttf',
 'myfont\_bold.ttf')
 


---
font-size parameter (skin)
----------------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-style parameter](#/{skin}/param/font-style) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 number
 



**Default value:** 


 0
 


 Point size of the font, or leave at 0 for the default size.
 



 The
 [Output control](#/{skin}/control/output) 
 behaves differently for legacy reasons, unless
 [legacy-size](#/{skin}/param/legacy-size) 
 is false.
 




---
font-style parameter (skin)
-----------------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[All](#/{skin}/control) 




**Possible values:** 


 bold
 
 italic
 
 underline
 
 strike
 






**Default value:** 


*empty* 



 Sets the font style. Any combination of the above values may be used, or none of them. Multiple values may be separated by spaces or commas.
 




---
group parameter (skin)
------------------------




**See also:** 


[button-type parameter](#/{skin}/param/button-type) 

[can-check parameter](#/{skin}/param/can-check) 

[is-checked parameter](#/{skin}/param/is-checked) 






**Applies to:** 


[Button](#/{skin}/control/button) 

[Menu](#/{skin}/control/menu) 





**Format:** 


 string
 


 Used for "radio" buttons and menu items, where only one of them in the same group may be checked at a time. This value is a text string, or may be left empty.
 



 Buttons in different windows/panes, or menu items in another menu/submenu, are always treated as a different group.
 




---
highlight-color parameter (skin)
----------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[background-color parameter](#/{skin}/param/background-color) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Info](#/{skin}/control/info) 





**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #00ff00
 


 The color used to highlight moused-over statpanel items or verbs. In grids, this color is used when hovering over objects or links.
 




---
icon parameter (skin)
-----------------------




**See also:** 


[title parameter](#/{skin}/param/title) 

[titlebar parameter](#/{skin}/param/titlebar) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 '
 *file* 
 '
 



**Default value:** 


*empty* 



 Custom icon used for the window. If no icon is specified, the Dream Seeker icon is used by windows by default.
 



 If this control is a pane, its icon will appear on the tab if the pane is inside a tab control. Lack of an icon will mean no icon appears in the tab.
 



 Note: The Windows
 
 .ico
 
 format is not used. Only image formats BYOND can already use are supported.
 




---
icon-size parameter (skin)
----------------------------




**See also:** 


[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 





**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 number
 



**Default value:** 


 0
 


 Size, in pixels, of icons on the map. A size of 0 stretches to fit available space.
 



 This parameter has been deprecated. Use
 [zoom](#/{skin}/param/zoom) 
 instead.
 




---
id parameter (skin)
---------------------




**See also:** 


[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 


 The name of this control. Read-only.
 



 If this is a
 [Main control](#/{skin}/control/main) 
 , the name should always be unique. For others, it is usually still a good idea to use a unique name, but they can be referenced by
 *window* 
 .
 *id* 
 at runtime.
 



 You can use a colon in front of the
 [type](#/{skin}/param/type) 
 to refer to the default control of a certain type, if one exists, e.g.
 
 :map
 
 is the default map.
 




---
image parameter (skin)
------------------------




**See also:** 


[image-mode parameter](#/{skin}/param/image-mode) 

[keep-aspect parameter](#/{skin}/param/keep-aspect) 





**Applies to:** 


[Button](#/{skin}/control/button) 

[Label](#/{skin}/control/label) 

[Main](#/{skin}/control/main) 

[Output](#/{skin}/control/output) 







**Format:** 


 '
 *file* 
 '
 


 A background image to show in this control.
 



 In the Output control this image is always tiled.
 



 Note: Icons displayed in the output control will not show the background image underneath their transparent parts, but will instead show the background color.
 



 For Label and Main, use
 [image-mode](#/{skin}/param/image-mode) 
 to control how the image is displayed.
 




---
image-mode parameter (skin)
-----------------------------




**See also:** 


[image parameter](#/{skin}/param/image) 

[keep-aspect parameter](#/{skin}/param/keep-aspect) 





**Applies to:** 


[Label](#/{skin}/control/label) 

[Main](#/{skin}/control/main) 





**Possible values:** 


 center
 
 stretch
 
 tile
 





**Default value:** 


 center
 


 Determines how the background image is displayed.
 




---
index parameter (skin)
------------------------




**Applies to:** 


[Menu](#/{skin}/control/menu) 




**Format:** 


 number
 



**Default value:** 


 1000
 


 Moves the menu item to the
 *N* 
 th position among its siblings. 0 or less is no change. Write-only.
 




---
inner-size parameter (skin)
-----------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 

[outer-size parameter](#/{skin}/param/outer-size) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


*width* 
 x
 *height* 



 Read-only.
 



 If the control is a window, this refers to its current interior size: i.e., not counting titlebar, statusbar, borders, etc. If it's maximized, this will be the true size of the window interior, as opposed to
 
 size
 
 which is the interior size once this window is no longer maximized.
 



 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true, this is the size of the display area not including the scrollbars.
 




---
is-checked parameter (skin)
-----------------------------




**See also:** 


[button-type parameter](#/{skin}/param/button-type) 

[can-check parameter](#/{skin}/param/can-check) 

[group parameter](#/{skin}/param/group) 






**Applies to:** 


[Button](#/{skin}/control/button) 

[Menu](#/{skin}/control/menu) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if the button or menu item is checked. Menu items can set this even if
 [can-check](#/{skin}/param/can-check) 
 is false.
 




---
is-default parameter (skin)
-----------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[parent parameter](#/{skin}/param/parent) 

[type parameter](#/{skin}/param/type) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Specifies that this is a default control. This should be true for your main window, and for your primary map, info, output, input, and browser controls.
 



 The default control of a given type can be referenced in
 [winset()](#/proc/winset) 
 and other skin-related procs by the name
 
 ":
 *type* 
 "
 
 , e.g.
 
 ":map"
 
 .
 



 Changing this value at runtime should be avoided, especially for windows. Results may be unpredictable.
 




---
is-disabled parameter (skin)
------------------------------




**See also:** 


[is-checked parameter](#/{skin}/param/is-checked) 

[is-visible parameter](#/{skin}/param/is-visible) 





**Applies to:** 


[All](#/{skin}/control) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 






**Format:** 


 true/false
 



**Default value:** 


 false
 


 Disables the control, menu item, or macro.
 




---
is-flat parameter (skin)
--------------------------




**See also:** 


[button-type parameter](#/{skin}/param/button-type) 




**Applies to:** 


[Button](#/{skin}/control/button) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Gives this button a flat appearance instead of pseudo-3D highlights.
 




---
is-list parameter (skin)
--------------------------




**See also:** 


[cells parameter](#/{skin}/param/cells) 

[current-cell parameter](#/{skin}/param/current-cell) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if the grid is used for a flexible list of items; the number of columns and rows may change to fit them.
 




---
is-maximized parameter (skin)
-------------------------------




**See also:** 


[can-resize parameter](#/{skin}/param/can-resize) 

[is-minimized parameter](#/{skin}/param/is-minimized) 

[size parameter](#/{skin}/param/size) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 false
 


 Maximize the window.
 




---
is-minimized parameter (skin)
-------------------------------




**See also:** 


[can-resize parameter](#/{skin}/param/can-resize) 

[is-maximized parameter](#/{skin}/param/is-maximized) 

[size parameter](#/{skin}/param/size) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 false
 


 Minimize the window.
 




---
is-pane parameter (skin)
--------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[Child control](#/{skin}/control/child) 

[Tab control](#/{skin}/control/tab) 






**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if this is a pane that will be used in other container controls, instead of an independent window. Read-only.
 




---
is-password parameter (skin)
------------------------------




**See also:** 


[command parameter](#/{skin}/param/command) 

[multi-line parameter](#/{skin}/param/multi-line) 

[no-command parameter](#/{skin}/param/no-command) 






**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Hide text with asterisks. Copy to clipboard is not available in this mode, but the
 [text](#/{skin}/param/text) 
 parameter can still read the control's contents.
 



 Note: For obvious reasons, you should never use the same password in a game that you would use anywhere else.
 




---
is-slider parameter (skin)
----------------------------




**See also:** 


[value parameter](#/{skin}/param/value) 




**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Make this an adjustable slider capable of being changed by the user, instead of a progress bar.
 




---
is-transparent parameter (skin)
---------------------------------




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Make this control transparent.
 



 Transparency support is extremely limited. Only some controls can actually use it, and only when on top of certain other controls.
 



 Bars and labels handle transparency reasonably well, when not on top of other controls (or only on top of other conrols of these types).
 




---
is-vert parameter (skin)
--------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 The splitter between the two panes in this control is vertical.
 




---
is-visible parameter (skin)
-----------------------------




**See also:** 


[is-disabled parameter](#/{skin}/param/is-disabled) 




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 True if this control can be seen. The main window should usually be made visible.
 




---
keep-aspect parameter (skin)
------------------------------




**See also:** 


[image parameter](#/{skin}/param/image) 

[image-mode parameter](#/{skin}/param/image-mode) 





**Applies to:** 


[Label](#/{skin}/control/label) 

[Main](#/{skin}/control/main) 





**Format:** 


 true/false
 



**Default value:** 


 false
 


 If stretching a background image, preserve its aspect ratio.
 




---
left, top parameters (skin)
-----------------------------




**See also:** 


[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 string
 
 none
 




**Default value:** 


 none
 


 The
 [id](#/{skin}/param/id) 
 of the left/top pane in this control. The parameter names
 
 left
 
 and
 
 top
 
 can be used interchangeably.
 




---
legacy-size parameter (skin)
------------------------------




**See also:** 


[font-size parameter](#/{skin}/param/font-size) 




**Applies to:** 


[Output](#/{skin}/control/output) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 When true, font sizes are scaled slightly larger for readability, which is legacy (and default) BYOND behavior. Set to false for exact font sizing.
 




---
letterbox parameter (skin)
----------------------------




**See also:** 


[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 






**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 If map auto-scales its icons (
 [zoom](#/{skin}/param/zoom) 
 is 0), make sure the entire map fits, and fill excess space with the background color.
 



 If
 
 letterbox
 
 is not enabled, auto-zoom will fill all available space, and any excess will be cut off.
 




---
line-color parameter (skin)
-----------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[show-lines parameter](#/{skin}/param/show-lines) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #c0c0c0
 


 The color of grid lines.
 




---
link-color parameter (skin)
-----------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[visited-color parameter](#/{skin}/param/visited-color) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Output](#/{skin}/control/output) 





**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #0000ff
 


 The color used for links. In some controls
 [visited links](#/{skin}/param/visited-color) 
 may have a different color.
 




---
lock parameter (skin)
-----------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 








**Applies to:** 


[Child](#/{skin}/control/child) 




**Possible values:** 


 left
 
 right
 
 none
 





**Default value:** 


 none
 


 Allows one pane to "lock" the splitter so if this Child control is resized, the splitter will stay put on that side.
 




---
macro parameter (skin)
------------------------




**See also:** 


[Keyboard/gamepad macros](#/{skin}/menu) 

[menu parameter](#/{skin}/param/menu) 

[id parameter](#/{skin}/param/id) 






**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 string
 


 The
 [id](#/{skin}/param/id) 
 of the macro set this window will use, if any, when it's active.
 




---
map-to parameter (skin)
-------------------------




**See also:** 


[macros (skin)](#/{skin}/macros) 

[command parameter](#/{skin}/param/command) 

[id parameter](#/{skin}/param/id) 

[name parameter](#/{skin}/param/name) 







**Applies to:** 


[Macro](#/{skin}/control/macro) 




**Format:** 


 string
 


 The
 [macro name](#/{skin}/macros) 
 (e.g., "SOUTH") of a key combo, Dpad, mouse button, etc. that this macro maps to.
 




---
max-lines parameter (skin)
----------------------------




**Applies to:** 


[Output](#/{skin}/control/output) 




**Format:** 


 number
 



**Default value:** 


 1000
 


 Maximum number of lines before the control drops old text to make room for more. 0 is no limit.
 



 An overflow of 5% is allowed, to reduce flicker.
 




---
menu parameter (skin)
-----------------------




**See also:** 


[macro parameter](#/{skin}/param/macro) 

[id parameter](#/{skin}/param/id) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 string
 


 The
 [id](#/{skin}/param/id) 
 of the menu this window will use, if any, when it's active.
 




---
multi-line parameter (skin)
-----------------------------




**Applies to:** 


[Info](#/{skin}/control/info) 

[Input](#/{skin}/control/input) 

[Tab](#/{skin}/control/tab) 






**Format:** 


 true/false
 



**Default value:** 



 false
 
 : Input control
 

 true
 
 : Info and Tab controls
 



 Input control: Create a multi-line input control. Read-only for this control.
 



 Info and Tab controls: Show tabs in multiple rows if there are too many to fit in a single row.
 




---
name parameter (skin)
-----------------------




**See also:** 


[macros (skin)](#/{skin}/macros) 

[id parameter](#/{skin}/param/id) 





**Applies to:** 


[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 





**Format:** 


 string
 


 Macro control: The key/gamepad combination such as
 
 R+REP
 
 ,
 
 CTRL+Northwest
 
 ,
 
 GamepadLeft
 
 .
 



 Menu control: This is the menu item label. A tab character can be used between the name and a keyboard shortcut, like "Help\tF1". (Keyboard shortcuts must be implemented as macros in order to work. This is just a label.) A blank name shows just a separator.
 




---
no-command parameter (skin)
-----------------------------




**See also:** 


[command parameter](#/{skin}/param/command) 

[is-password parameter](#/{skin}/param/is-password) 

[multi-line parameter](#/{skin}/param/multi-line) 






**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if this input control is for typing only; hitting Enter will not run a command.
 




---
on-blur parameter (skin)
--------------------------




**See also:** 


[focus parameter](#/{skin}/param/focus) 

[on-focus parameter](#/{skin}/param/on-focus) 





**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the control loses focus.
 




---
on-close parameter (skin)
---------------------------




**See also:** 


[can-close parameter](#/{skin}/param/can-close) 

[on-size parameter](#/{skin}/param/on-size) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the window is closed.
 




---
on-change parameter (skin)
----------------------------




**See also:** 


[value parameter](#/{skin}/param/value) 




**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the
 [value](#/{skin}/param/value) 
 of the bar/slider is changed. If you drag the slider around, the command will not run until you let go.
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the control's new
 
 value
 
 . (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




---
on-focus parameter (skin)
---------------------------




**See also:** 


[focus parameter](#/{skin}/param/focus) 

[on-blur parameter](#/{skin}/param/on-blur) 





**Applies to:** 


[Input](#/{skin}/control/input) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the control gains focus.
 




---
on-hide parameter (skin)
--------------------------




**See also:** 


[on-show parameter](#/{skin}/param/on-show) 




**Applies to:** 


[Browser](#/{skin}/control/browser) 

[Info](#/{skin}/control/info) 

[Map](#/{skin}/control/map) 






**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is hidden by the game. Must be the default control for the game to show/hide it.
 



 Currently not editable in Dream Maker.
 




---
on-show parameter (skin)
--------------------------




**See also:** 


[on-hide parameter](#/{skin}/param/on-hide) 




**Applies to:** 


[Browser](#/{skin}/control/browser) 

[Info](#/{skin}/control/info) 

[Map](#/{skin}/control/map) 






**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is shown by the game. Must be the default control for the game to show/hide it.
 



 Currently not editable in Dream Maker.
 




---
on-size parameter (skin)
--------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when this control is resized. If you are dragging a window edge or splitter, the command won't run until you finish.
 



 No command will be sent in response to size or splitter changes made by
 [winset()](#/proc/winset) 
 .
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the control's new size. Likewise,
 
 [[width]]
 
 will be replaced with the width and
 
 [[height]]
 
 with the height. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




---
on-status parameter (skin)
----------------------------




**See also:** 


[statusbar parameter](#/{skin}/param/statusbar) 




**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the text that would go in the statusbar is changed. This applies even if this control is a pane and not a window, or is a window without a statusbar. It applies to all panes and windows that directly or indirectly contain whatever control generated the statusbar text (e.g., a map).
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the new text. (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




 [[from]]
 
 can be used to reference the control (if any) that generated the next text. You can also use expressions like
 
 [[from.type]]
 
 ,
 
 [[from.parent.pos.x]]
 
 , etc.
 




---
on-tab parameter (skin)
-------------------------




**See also:** 


[current-tab parameter](#/{skin}/param/current-tab) 

[tabs parameter](#/{skin}/param/tabs) 





**Applies to:** 


[Info](#/{skin}/control/info) 

[Tab](#/{skin}/control/tab) 





**Format:** 


 string
 


[Command](#/{skin}/commands) 
 executed when the current tab is changed.
 



 If you include
 
 [[\*]]
 
 in the command, it will be replaced by the new tab's
 [id](#/{skin}/param/id) 
 . (See "Embedded Winget" in
 [client commands](#/{skin}/commands) 
 for more details on the
 
 [[...]]
 
 format.)
 




---
outer-size parameter (skin)
-----------------------------




**See also:** 


[size parameter](#/{skin}/param/size) 

[inner-size parameter](#/{skin}/param/inner-size) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


*width* 
 x
 *height* 



 Read-only.
 



 If the control is a window, this refers to its current exterior size
 *including* 
 titlebar, statusbar, borders, etc.
 



 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true, this is the size of the display area including the scrollbars.
 




---
parent parameter (skin)
-------------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[type parameter](#/{skin}/param/type) 

[name parameter](#/{skin}/param/name) 






**Applies to:** 


[All](#/{skin}/control) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 






**Format:** 


 string
 


 The
 [id](#/{skin}/param/id) 
 of this control's parent. Write-only, used when creating a new control at runtime or deleting a control that was created this way.
 




---
pos parameter (skin)
----------------------




**See also:** 


[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[size parameter](#/{skin}/param/size) 





**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


*x* 
 ,
 *y* 

 none
 




**Default value:** 


*x* 
 ,
 *y* 

 none
 



 Position of this control's upper left corner, relative to its container. (Not applicable to panes.)
 




---
prefix-color parameter (skin)
-------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[suffix-color parameter](#/{skin}/param/suffix-color) 





**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 The color used for the prefix/header column of statpanel displays. No color means the default
 [text-color](#/{skin}/param/text-color) 
 will be used.
 



 In BYOND 3.0, this color was red.
 




---
right, bottom parameters (skin)
---------------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 string
 
 none
 




**Default value:** 


 none
 


 The
 [id](#/{skin}/param/id) 
 of the right/bottom pane in this control. The parameter names
 
 top
 
 and
 
 bottom
 
 can be used interchangeably.
 




---
right-click parameter (skin)
------------------------------




**See also:** 


[mouse handling](#/DM/mose) 

[popup\_menu setting (verb)](#/set/popup_menu) 

[drop-zone parameter](#/{skin}/param/drop-zone) 






**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 True if this control should allow right-clicks to behave like any other click instead of opening up popup menus or similar special behavior.
 




---
saved-params parameter (skin)
-------------------------------




**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


 string
 



**Default value:** 


*varies* 



 A semicolon-separated list of parameters that get saved with this control. This is often used for things a user might set, like zoom level for a map.
 



 Currently not editable in Dream Maker.
 




---
size parameter (skin)
-----------------------




**See also:** 


[pos parameter](#/{skin}/param/pos) 

[anchor1, anchor2 parameters](#/{skin}/param/anchor) 

[on-size parameter](#/{skin}/param/on-size) 

[inner-size parameter](#/{skin}/param/inner-size) 

[outer-size parameter](#/{skin}/param/outer-size) 








**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


*width* 
 x
 *height* 



 The size of this control.
 



 Setting 0 for width or height uses up any available space right/downward.
 



 If the control is a window, this refers to its
 *interior size when not maximized or minimized* 
 . That is, it does not count borders, titlebar, menu, or statusbar, and if the window is minimized/maximized, this refers to the window's normal size when it is restored. See the
 [inner-size](#/{skin}/param/inner-size) 
 and
 [outer-size](#/{skin}/param/outer-size) 
 params for comparison.
 



 If this control is a pane and
 [can-scroll](#/{skin}/param/can-scroll) 
 is true,
 
 size
 
 refers to the total scrollable size of the pane, NOT the smaller size displayed. In this case,
 
 outer-size
 
 and
 
 inner-size
 
 refer to the display area with and without scrollbars, respectively.
 




---
show-history parameter (skin)
-------------------------------




**See also:** 


[show-url parameter](#/{skin}/param/show-url) 

[use-title parameter](#/{skin}/param/use-title) 





**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Show forward/back navigation buttons.
 




---
show-lines parameter (skin)
-----------------------------




**See also:** 


[line-color parameter](#/{skin}/param/line-color) 




**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Possible values:** 


 none
 
 horizontal
 
 vertical
 
 both
 






**Default value:** 


 both
 


 Determines which grid lines to display.
 




---
show-names parameter (skin)
-----------------------------




**See also:** 


[name var (atom)](#/atom/var/name) 

[small-icons parameter](#/{skin}/param/small-icons) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 When atoms are output to the grid, show the atom's name next to its icon.
 



 If the atom has no icon and
 
 show-names
 
 is false, the grid cell will be blank.
 




---
show-splitter parameter (skin)
--------------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[splitter parameter](#/{skin}/param/splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 true/false
 



**Default value:** 


 true
 


 Show a splitter if both the left and right (or top and bottom) panes are in use. The splitter can be dragged to resize the panes.
 




---
show-url parameter (skin)
---------------------------




**See also:** 


[show-history parameter](#/{skin}/param/show-history) 

[use-title parameter](#/{skin}/param/use-title) 





**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Shows an address bar for this browser control.
 




---
small-icons parameter (skin)
------------------------------




**See also:** 


[show-names parameter](#/{skin}/param/show-names) 




**Applies to:** 


[Grid](#/{skin}/control/grid) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 When output(object,grid) is sent, show smaller icons in this control instead of larger ones.
 




---
splitter parameter (skin)
---------------------------




**See also:** 


[left parameter](#/{skin}/param/left) 

[right parameter](#/{skin}/param/right) 

[is-vert parameter](#/{skin}/param/is-vert) 

[show-splitter parameter](#/{skin}/param/show-splitter) 







**Applies to:** 


[Child](#/{skin}/control/child) 




**Format:** 


 number (0 to 100)
 



**Default value:** 


 50
 


 Position of the splitter when two panes are in use, whether
 [show-splitter](#/{skin}/param/show-splitter) 
 is true or not. This value is a percentage. Specifically, it is the percentage of the available width/height that is given to the left/top pane.
 




---
suffix-color parameter (skin)
-------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[prefix-color parameter](#/{skin}/param/prefix-color) 





**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 The color used for the suffix column of statpanel displays. No color means the default
 [text-color](#/{skin}/param/text-color) 
 will be used.
 



 In BYOND 3.0, this color was blue.
 




---
statusbar parameter (skin)
----------------------------




**See also:** 


[titlebar parameter](#/{skin}/param/titlebar) 

[on-status parameter](#/{skin}/param/on-status) 





**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Shows a status bar at the bottom of the window. This will show the name of an atom when you hover over it with the mouse.
 




---
stretch parameter (skin)
--------------------------




**See also:** 


[image parameter](#/{skin}/param/image) 

[image-mode parameter](#/{skin}/param/image-mode) 





**Applies to:** 


[Label](#/{skin}/control/label) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Stretch the background image. Deprecated; use
 [image-mode](#/{skin}/param/image-mode) 
 instead.
 




---
style parameter (skin)
------------------------




**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Map](#/{skin}/control/map) 

[Output](#/{skin}/control/output) 






**Format:** 


 string
 


 Custom stylesheet used for the control. Changes made at runtime will usually not impact any existing text.
 



 For Map controls, this affects any
 [maptext](#/atom/var/maptext) 
 drawn, and changes to the style should appear on the next refresh.
 




---
tab-background-color parameter (skin)
---------------------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[tab-text-color parameter](#/{skin}/param/tab-text-color) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 Affects the background color for tabs. The regular
 [background-color](#/{skin}/param/background-color) 
 is used for the content area.
 




---
tab-font-family, tab-font-size, tab-font-style parameters (skin)
------------------------------------------------------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 

[tab-text-color parameter](#/{skin}/param/tab-text-color) 

[tab-background-color parameter](#/{skin}/param/tab-background-color) 








**Applies to:** 


[Info](#/{skin}/control/info) 



 Affects the font for tabs. The regular versions of these without the
 
 tab-
 
 prefix are used for the content area.
 




---
tab-text-color parameter (skin)
---------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[tab-background-color parameter](#/{skin}/param/tab-background-color) 

[tab-font-family, tab-font-size, tab-font-style parameters](#/{skin}/param/tab-font) 






**Applies to:** 


[Info](#/{skin}/control/info) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 Affects the text color for tabs. The regular
 [text-color](#/{skin}/param/text-color) 
 is used for the content area.
 




---
tabs parameter (skin)
-----------------------




**See also:** 


[current-tab parameter](#/{skin}/param/current-tab) 

[id parameter](#/{skin}/param/id) 

[multi-line parameter](#/{skin}/param/multi-line) 






**Applies to:** 


[Tab](#/{skin}/control/tab) 




**Format:** 


 string
 


 A comma-separated list of
 [id](#/{skin}/param/id) 
 values for the panes included as tabs in this control.
 



 When setting this value, you can put
 
 +
 
 in front of the list to add tabs to the existing control, without affecting current tabs. You can likewise use
 
 -
 
 in front of the list to remove tabs.
 



 Note: When using this with
 [winset()](#/proc/winset) 
 , remember you will need to escape
 
 +
 
 as
 
 %2B
 
 via
 [url\_encode()](#/proc/url_encode) 
 or
 [list2params()](#/proc/list2params) 
 .
 




---
text parameter (skin)
-----------------------




**See also:** 


[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 

[text-wrap parameter](#/{skin}/param/text-wrap) 







**Applies to:** 


[Button](#/{skin}/control/button) 

[Input](#/{skin}/control/input) 

[Label](#/{skin}/control/label) 






**Format:** 


 string
 


 Text shown in this control. For Input controls this setting is only available at runtime.
 




---
text-color parameter (skin)
-----------------------------




**See also:** 


[background-color parameter](#/{skin}/param/background-color) 

[font-family parameter](#/{skin}/param/font-family) 

[font-size parameter](#/{skin}/param/font-size) 

[font-style parameter](#/{skin}/param/font-style) 







**Applies to:** 


[All](#/{skin}/control) 




**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 



 The control's foreground text color.
 




---
text-mode parameter (skin)
----------------------------




**See also:** 


[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 





**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Show text mode even if icons are available. Text mode will be used if no icons are present, regardless of this setting.
 




---
text-wrap parameter (skin)
----------------------------




**See also:** 


[text parameter](#/{skin}/param/text) 




**Applies to:** 


[Label](#/{skin}/control/label) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Wrap text that is too long for the width of the label.
 




---
title parameter (skin)
------------------------




**See also:** 


[name var (world)](#/world/var/name) 

[icon parameter](#/{skin}/param/icon) 





**Applies to:** 


[Main](#/{skin}/control/main) 




**Format:** 


 string
 


 The title of this window or pane. For a window, the title will appear in the titlebar if present. For a pane, this will be displayed on the tab if this pane is in a
 [Tab control](#/{skin}/control/tab) 
 .
 



 If this is the default window,
 [world.name](#/world/var/name) 
 takes precedence over the window title.
 




---
titlebar parameter (skin)
---------------------------




**See also:** 


[can-close parameter](#/{skin}/param/can-close) 

[can-minimize parameter](#/{skin}/param/can-minimize) 

[can-resize parameter](#/{skin}/param/can-resize) 

[icon parameter](#/{skin}/param/icon) 

[title parameter](#/{skin}/param/title) 

[use-title parameter](#/{skin}/param/use-title) 

[statusbar parameter](#/{skin}/param/statusbar) 

[name var (world)](#/world/var/name) 











**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


 true/false
 



**Default value:** 


 true
 


 Show a titlebar for this window. This is also required for the close, minimize, and maximize buttons to appear.
 




---
transparent-color parameter (skin)
------------------------------------




**See also:** 


[alpha parameter](#/{skin}/param/alpha) 




**Applies to:** 


[Main](#/{skin}/control/main) 
 (window only)
 



**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 none
 


 A color that will be turned into transparency wherever it appears in this window. Overall, this method of transparency comes with many limitations, so it is considered deprecated.
 




---
type parameter (skin)
-----------------------




**See also:** 


[id parameter](#/{skin}/param/id) 

[parent parameter](#/{skin}/param/parent) 





**Applies to:** 


[All](#/{skin}/control) 

[Macro](#/{skin}/control/macro) 

[Menu](#/{skin}/control/menu) 






**Format:** 


 string
 


 The type of this control. Read-only.
 




---
use-title parameter (skin)
----------------------------




**See also:** 


[show-history parameter](#/{skin}/param/show-history) 

[show-url parameter](#/{skin}/param/show-url) 

[title parameter](#/{skin}/param/title) 

[titlebar parameter](#/{skin}/param/titlebar) 







**Applies to:** 


[Browser](#/{skin}/control/browser) 




**Format:** 


 true/false
 



**Default value:** 


 false
 


 Use the browser's document title to override the title of the window or pane it appears in.
 




---
value parameter (skin)
------------------------




**See also:** 


[is-slider parameter](#/{skin}/param/is-slider) 

[dir parameter](#/{skin}/param/dir) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 number
 



**Default value:** 


 0
 


 The "fullness" of this bar/slider, as a percentage.
 




---
view-size parameter (skin)
----------------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[zoom parameter](#/{skin}/param/zoom) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 

[icon\_size var (world)](#/world/var/icon_size) 

[view var (world)](#/world/var/view) 

[view var (client)](#/client/var/view) 

[HUD / screen objects](#/{notes}/HUD) 










**Applies to:** 


[Map](#/{skin}/control/map) 
 (window only)
 



**Format:** 


*width* 
 x
 *height* 



 The size, in pixels, of the map after
 
 zoom
 
 has been applied.
 



 For instance, if the client view has 10×10 tiles (this includes any extended tiles caused by HUD objects) and
 
 world.icon\_size
 
 is 32x32, the map has a native size of 320×320 pixels. If the map has a zoom level of 2, then
 
 view-size
 
 will be 640x640.
 



 With a
 
 zoom
 
 value of 0, which is the default for most projects, the actual zoom level is automatically determined by the size of the map control, the map's native pixel size as explained above, and the value of the
 [letterbox](#/{skin}/param/letterbox) 
 parameter.
 




---
visited-color parameter (skin)
--------------------------------




**See also:** 


[text-color parameter](#/{skin}/param/text-color) 

[link-color parameter](#/{skin}/param/link-color) 





**Applies to:** 


[Grid](#/{skin}/control/grid) 

[Output](#/{skin}/control/output) 





**Format:** 


[#rrggbb](#/{{appendix}}/html-colors) 

 none
 




**Default value:** 


 #0000ff
 


 The color used for visited links.
 




---
width parameter (skin)
------------------------




**See also:** 


[dir parameter](#/{skin}/param/dir) 

[is-slider parameter](#/{skin}/param/is-slider) 





**Applies to:** 


[Bar](#/{skin}/control/bar) 




**Format:** 


 number
 



**Default value:** 


 10
 


 Width, in pixels, of the bar or slider. A value of 0 uses all available width.
 




---
zoom parameter (skin)
-----------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[view-size parameter](#/{skin}/param/view-size) 

[zoom-mode parameter](#/{skin}/param/zoom-mode) 






**Applies to:** 


[Map](#/{skin}/control/map) 




**Format:** 


 number
 



**Default value:** 


 0
 


 Zoom factor for icons on the map. 1 means to show the icons at their original size, 2 is 200%, 0.5 is 50%, and so on. A value of 0 stretches to fit available space.
 




---
zoom-mode parameter (skin)
----------------------------




**See also:** 


[letterbox parameter](#/{skin}/param/letterbox) 

[view-size parameter](#/{skin}/param/view-size) 

[zoom parameter](#/{skin}/param/zoom) 






**Applies to:** 


[Map](#/{skin}/control/map) 




**Posisble values:** 


 normal
 
 distort
 
 blur
 





**Default value:** 


 normal
 


 Controls the way the map is upscaled.
 




 normal
 


 Preserves a pixelated look, but does some blending between adjacent pixels when the zoom factor is not an integer. This is equivalent to upscaling by the next highest integer, then downscaling.
 

 distort
 

 Uses nearest-neighbor sampling to upscale. This may look odd if the zoom factor is not an integer, since for instance some pixels might scale up to be 2 pixels wide, others 3 pixels wide. Some users prefer it anyway.
 

 blur
 

 Uses bilinear sampling to upscale. This will cause a blurry appearance if the zoom factor is high, but it may be desired in some cases.
 


---
Appendix
----------



 This section contains miscellaneous information that may apply to multiple
vars or procs.
 




[CSS attributes](#/{{appendix}}/css) 

[HTML colors](#/{{appendix}}/html-colors) 

[Color space](#/{{appendix}}/color-space) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







---
CSS attributes
----------------



 DM-CSS is a subset of CSS, and only supports some kinds of selectors and
attributes.
 



 The following table lists all supported attributes, and whether they are
supported in text output, maptext, and in other controls (labels/etc.) Other
controls will often allow only one style for an entire unit of text. A
checkbox in "Other" only indicates that
 *some* 
 support exists in other
controls, but it may vary by the type of control.






| 
 Attribute
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |
| 
 color
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Alpha colors may not be supported in some controls.
  |
| 
 background
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 In most cases, only applies to the entire text body.
  |
| 
 background-color
  | 
 ✔️
  | 
 ✔️
  |  |  |
| 
 background-image
  | 
 ✔️
  |  |  |  |
| 
 font
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-family
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-style
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-weight
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 font-size
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 text-decoration
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 underline
 
 ,
 
 overline
 
 ,
 
 line-through
 
 ,
 
 blink
 
 , and
 
 none
 
 . Support for each of these may vary depending on where they are used.
  |
| 
 text-align
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  | 
 justify
 
 is supported in output and maptext.
  |
| 
 vertical-align
  |  | 
 ✔️
  | 
 ✔️
  | 
 Limited to
 
 top
 
 ,
 
 middle
 
 , and
 
 bottom
 
 .
  |
| 
 text-indent
  | 
 ✔️
  | 
 ✔️
  |  |  |
| 
 margin-left
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 margin-right
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 margin-top
  |  |  | 
 ✔️
  |  |
| 
 margin-bottom
  |  |  | 
 ✔️
  |  |
| 
 margin
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 width
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |
| 
 height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Applies only to some elements such as images.
  |
| 
 line-height
  | 
 ✔️
  | 
 ✔️
  |  | 
 Support in output control is limited; line heights less than 1 are not respected.
 
 Only unitless numbers, percentages, or em units are allowed.
  |
| 
 white-space
  | 
 ✔️
  | 
 ✔️
  |  | 
 normal
 
 ,
 
 nowrap
 
 ,
 
 pre
 
 ,
 
 pre-wrap
 
 ,
 
 pre-line
  |
| 
 text-shadow
  |  | 
 ✔️
  |  |  |
| 
 -dm-text-outline
  |  | 
 ✔️
  |  | 
 Custom attribute: Adds an outline to text. Values are in the form:
 
*width color style* 

 .
 
 The style is either blank, or any combination of the
 
 sharp
 
 and
 
 square
 
 keywords (see
 [Outline filter](#/{notes}/filters/outline) 
 ).
  |



 These pseudo-classes are allowed in some contexts, but they can only change
the text color.
 








| 
 Psuedo-class
  | 
 Output
  | 
 Maptext
  | 
 Other
  | 
 Notes
  |
| 
 :link
  | 
 ✔️
  | 
 ✔️
  | 
 ✔️
  |  |
| 
 :visited
  | 
 ✔️
  |  |  |  |
| 
 :active
  |  |  |  | 
 Currently not used, but future support is planned.
  |
| 
 :hover
  |  | 
 ✔️
  |  |  |




---


HTML colors
-------------




**See also:** 


[rgb proc](#/proc/rgb) 



 Text colors may be specified by name or RGB value. The RGB color format
uses hexadecimal numbers, with 2 hex digits each for red, green, and blue.
These range from 0 (00 in hex) to 255 (FF in hex). In certain situations
BYOND will also honor a fourth pair of digits for alpha.
 



```
#rrggbb
#rrggbbaa

```


 It is also possible to use 4 bit values by using only one hex digit per
color. The full 8 bit color is produced by repeating each digit. For example,
 `#F00` 
 (red) is the same as
 `#FF0000` 
 .
 



 The named colors supported by BYOND, and their corresponding RGB values,
are listed in the following table:






| 
 black
  | 
 #000000
  |  |
| 
 silver
  | 
 #C0C0C0
  |  |
| 
 gray
 *or* 
 grey
  | 
 #808080
  |  |
| 
 white
  | 
 #FFFFFF
  |  |
| 
 maroon
  | 
 #800000
  |  |
| 
 red
  | 
 #FF0000
  |  |
| 
 purple
  | 
 #800080
  |  |
| 
 fuchsia
 *or* 
 magenta
  | 
 #FF00FF
  |  |
| 
 green
  | 
 #00C000
  |  |
| 
 lime
  | 
 #00FF00
  |  |
| 
 olive
 *or* 
 gold
  | 
 #808000
  |  |
| 
 yellow
  | 
 #FFFF00
  |  |
| 
 navy
  | 
 #000080
  |  |
| 
 blue
  | 
 #0000FF
  |  |
| 
 teal
  | 
 #008080
  |  |
| 
 aqua
 *or* 
 cyan
  | 
 #00FFFF
  |  |




---


Color space
-------------




**See also:** 


[rgb proc](#/proc/rgb) 

[rgb2num proc](#/proc/rgb2num) 

[gradient proc](#/proc/gradient) 

[animate proc](#/proc/animate) 

[Color gradient](#/{notes}/color-gradient) 

[Color matrix filter](#/{notes}/filters/color) 








 There are different ways of interpreting color besides RGB. Several parts of
BYOND are capable of using other color spaces.
 


### 
 COLORSPACE\_RGB



 The default color space is RGB, where each color is split into red, green,
and blue components, as well as an optional alpha. All of these components range
from 0 to 255.
 



 The color yellow for instance is
 
 rgb(255,255,0)
 
 which is red and
green mixed together at their maximum brightness, but no blue component.
 


### 
 COLORSPACE\_HSV



![](data:image/png;charset=utf-8;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAACWCAYAAAA8AXHiAAAgQklEQVR4Xu2dDbAW1XnHz+677718XLkXAlEJUFCJWoGEWAtJDNUq0WrSRJNiVWq0EjRCk4ramphpTJ2mSRW1qZgPNMZINNRomvhVqxhQ0qEEO1WjQEDUCKiBGECC3Pved7f/uf5nntfnuc+cC5MZnZ1d5jfPOWfv7uXd/d/nefbsOedNiqII1Vbx+yalraiohFVRCauiElZFxe+PrLWSJAlLFYoZ4AwwGDwEfgAKUG1EPwRWHivObLAcXAjOAbeDL4Jqq0LhfpOBhSCh15pOT3UxvVe1VcLaL6aAd4KN4GdgDcvDwdRKPpWw9pcxtC8G2bbSHkxbUQlrnzmAtjvI1pAwWW2VsPaPX9MOD7KNoN1CW1EJa5/Z0JJrdVJgR9FrPeMcU1G58yjPs99qJljGtnZwM3gVVFvlsfab2eAucDg4BHwT/M3v48SVx6ryrE+G0myVx6qohFVRUQmrohJWRSWs8nMlKe9WCauiElZFJayKikpYFVXPexFWwjRJTktCrymLbbCs6eH+HtYbYonXxnZtR4Ep4CjUD8G5x6N8EOxIMALUQ8g7+vx7LVwCGiELr8Juh30Z9nnYTaEenoZ9EmxDOfSR0WqyAbTVQBtta1umqCmb0tZISsu2ZHo5hAVqtAno1bJrLZOUttbSlrOet7RntE0ek4BUkRgLDgMngQ+iAsI4wC3l+RICQ8umDjYOR/lQEEjrKX6FOkacgjQ8iPJG/nqfmion0kYrbQJF5NWdnw/lEhbJKIQg4pGyEpoWVBCPxzZeSSW4Zn/iOgJ2NuwZ4DCqwWCFnti/gcSpUzx9Qk1AGs5k20aIYCnKS1BeB1pE45Qz62msF7KCtG3alinHsp+Y1BxSY3mltZ+P3KFkBOrzwSqwFvUr3hBVsF5M1CGIglxxAXtYasqHgStQXgu7CsxHeQQ9kxaBkEX3wXpezIRH7i+Jx7L6TXRZUbhleimSSl28GG16OM69APYcMMgPjcEVk/VaNOZjGTGxLigBTSNXg+9h37Ww6ykKP4xlghWMxQ+1JfJY9mplOpGIXSHnKpsr926wBOVnsH/uG6KSu8qyIGITXPF7niqGm1MNgp0L+wz4Psrvln02FHrh01pFpnOvUgkrca5IJtYJb84+fY6RYBF4GpyNfamKH76YiGxWYD5+BLW/1o3YKTgLPA0WgZHAj+6ZLltLrEdLSiesLCKYNCI2tz3BceejvgFchHoGjKB0G4kLzBcT0VfRRlwS9zJZyGAvAhvAHLQntjtBl3VbhKx0oTCNXRXbHmc8jnkE3IRyV//h0oqMVvDzrn30WCrSiqYdz+Um3F2oL4Z9BHa8mx3EHTzPWf4cy/Eg0T9FscJstD0BjuvnSTHmKtzcygqsGGDoc9rTAYjJj/DHgSfAbOA78nqsK0JfzrdOWBM5POS74HowI9jtdHAT+BY4Ue0bCi4Dt4KvggkmxxLcsEe0aNrBYrTdhrZh/STysbgQCYXRkBgXWmqRMCQ43koLZxj23Qa7GLTHuxbsJbAh2P0Ufw6+wfv2aaWRc8At4AYwfX+F9RnwD+AT4HNgBTgzyHYVuIu/bC6nR81qmRr1KPgXHvP3YHUSJhzkeKOIwFJQD6zjHNljsHPQ5h4L7JW0sUnwXc++iSlR1ATdRvxuAyuyOeAxcHDsdQ6Iey+rgR+AH4MLed/PD7ItptjOBvPAY2DGPguLv2QEp5dfw7azaN8FLge76dlms/3ztOeC94FloAPcCUaCuf36/YF32EwC/4PyMao98jxuMl8To2wSFFxL4/9IKrAt6kF8UUidf0fHgFVonyT7JRRaXHHpbS6YRcGM5n07g/umgr8GW8FB4O9ARrvPwloNdrC8Wy2KMYMnXg5eoOdqgPdSjCfwuDtAD1jK+p9Ge9v98DUd+x4F4/TP2Le3vuiIERkwapDNvuax+lM6DfE+Jisghf80OA72UdjpVkBeSIyGwgtbbIMO5YXA+0Z7L3iVToft+yosOdETDIk/AV9yVl/ZC37D8sH0aNyvVmbx44C98iKUGbAPoW0420226ovJv+IWEZhVTyHlwguBfsSF9ckEu89lOHgIl2GGPc7J6TJiQ+EQMBl0Mx/eRqfyT+p+b6Z9iVdhMBi+P8IaD97J/RPBEWwfRtsTZOulrYNOlrv1yixRf22v8DSc8j60dYBAtKfSQtXC06HSy7+0+1GYl8/+U2DNtXHtE/vRzMfqAPeiPC0iToqNWGENZ2s72AMuZpT6AjgaDFP3swlylrP9EdYkeqBzwZHg+2r1lS65rFCuqPoVtTrLO2i3+IEf1l7FybAPou6IKhOk7uwzV1lZIzAS2bz8KnE/HqwRif0bqXvezIjuANgHYSe7OVx82Mx2kJNzwfVMbwKFpe9nF8/SzWMHLizl4tbQjqACNrD+AapgKrsXtjAkcn/4EO2xtE+a8OO/lxgNez9spxKTf9XtHfAFJXUlJLZFuxpsCBT8m+lHZ3cgn/3YdXNsJ+z9YIz/9ssXFgWyka2jlTN4GWxQ9/GDtE+BYl+F9TgfPb8DHmTb3VT1I+BZMJH7/h0EKr3gMTmYx8R9AdV948CS9XobLH5XNkbaoh5L4+VikcFLCTH5luOlIiKzIoo72rrg/7wR0BjwQ9DmXF43FJLraR/kU/xHeY8fBj8C2ymse8C3eMx1+5O8r2An2NlMzv8ZfKYltzoV/JTqHcLO1IUtT5Rn8ani42AT+FgR9jxjQw+wIlsEpgH/qtt9GraL9UWX+q997OYPm0kdMsEXmKn7//3MZRrOf6N7iVknevsm7+FQMBPcBz4M9jCRPwWsZlsP+Cy4fX/GY51H67E+8ri5lJhRo8x6Sa7Dzmz8zBzJEbnxOP8dXmHg+CxFrwiPZT+ZF7jZp0Lb1QC8Tk/fUwmeF3MEasc/ng+Wo32JfuCVMrGf6ssExvBzMO3tOmwmMno0G4+2Rf1muWIdTOzwQmOkazohLGuR+T3ufoSN/7dt2dZ9z2fztkWw4/3Xo6Uc3ZDg36DrkjB4fhKGZiKuLIH9jnr3F3seJ20xIam2WNe0DYXSQUqTOk+Cok+dlFutt0WidUxc/giHYbC3gIQiCslgXOBBYX7SFq4rp7AA4/mfgV8kYcgpvBrnwx7vDFLyMtkIbUp4hO061yKRUQ+RvqvMWt8jiTW0EdcZRwb8peE4MAd1iKovZflfcBq4Be0hT0okrBwUIQX5enAqqvPBNaPDhOVNWPfxyb9DniuI3y0h7rVg7RYZFpMpHL0T7ot3z/mh0JKHcPXYQ8N/8CnuqqIIJ+RFeDKn0y2NsNhdC5JQ9FE8jOp7loY7anhK7vRHkYolnmhIRmuIhMpabKyWJfFe3ajTa723s12LjPuk7oqL+H29aT10fveWvn6pyRDUnTLdBLY8M6HpsdTtgrgmwEyn5OSqoGyfHPPIZIeCSJ3nFWSWNWlQVD3Ouw9nM09bNp/yQ54rKlrPaXvj1/3BsSecGKY2izAOQvolYIpYMmE1QaLEhfKXUM4SaREBGZogeHVVLgS5nKQJ2iisOsWl3UKP47nEALcrzjpS0i4WKC/m5VSR5wwr8tZPn+Vv9E+dlYuoyuexkpYypHQ4+MuC7Sn2JiIMWk1qBCXYjcKyopJ+LdKjXILgnjsVbMIeCYOsi8ikbvMposKeN02S4mm1Z8D+I+w61kGJhNVQ1wLSuQSkSkoUmCMoCig+e9nK2nqtXoqsQUtxEd1Z6udWRESlRKPLqi5CE2reu3Nih5GJkKxNwQKU55ZMWPbWQhIjwWyWKbQ3WcqrJrJz863UWWgkifbGS57VY2KQHwpVs+rLJSYECmqf7Y7zR2jbaZLyyRxhsTwb9guw2xkGy+mxIItzYAd7czoJ6yms7kDK/VF2FgmLxms1SDvF1a3vpucFrah8L2UZRHTinilS/2G1AEZIfnkw7KfAQraVK3kvRBKfFpHBEu1jUrEgNd6K4XHgC3qwLA/d8nRIJUTFZecGmnwKaCE5XktyKzmPP4SfgoqIyN83B3Zh6UJhr9yPo2GPgBUPZt6KUD4si/gSUHNyr9TxeWbop+p+IPRYKtlRAvUmSKjwNigKxeW8cTIrzMQF1Yx7riPA0Sg/DsrTQdqQWzgLiK8QdBuzIGtzZ0imSloicWgwMXebxxuv5U7qFg9kBcRf4f8alq24RNt5YnvhGrT7Ugaz2FYaYbUK5nRJmSkoKyorulaxkcLGIj9zppgsQ5w7L+KiqFQotLmVaJV2qLTJPqVx74U0KBIrEisWQa6rPY6cTlsujwUOBYc54qHQnAvmXrSEAlOeizjeSjGEUBU81nY70IieVfhTp5O67xzbrbgKnLup/5B8zx4XHeG1P7SnbB4LnGyFFKfHvWitNwAC06FRBOUIaSitYB/ZakSEJaFKRCXa1KfXkdfpv6pRUMlArgcwbRZ7nXkPypS88yXJsbIaqZ9upxHkVjOxF8ulplDy6LfromhJ4PeSPXLnjceS931Gqx1kKBmixWS7ywognSBCLrCuyzaBD7rd7jsW9UWl6seCED6oOgm0mPxBmbqdVgQl9aYIzJzFn43Tq8QlYVGOU2GQzpDeiaKSMsUmpzHPBf4C5az7glLtRaRPK0j92FINm+kOYRRu2VjPbXcLuk38iGrrdugR+AQp+ZbNrjs4o3wYQTl0KEVkcpkSVtvlFDgEyOE8hZxGh0GcMq+9OVR1a6vK7mc357A0uI92DNpGlSl5n6JFpesiItbtRZU2A9sdoTUZu1oU4QirU8rYL49uKaCp8xQd6jBCYTEUUlQiKBGL4nW2w8rnUaKyImPdCtNea8lR31smYR3VHfVSxAiIdV9IvDG0xHq5JBSh3uqxyAFUxHDQRUuBQRkSDmna2CyHyaHDSMebRZVDjI1EC8YXF8v+zzt/hKpMTNuRZUreD7Fr7NNG1tZwE/vIRH0ZJKAnfaVobwtJv8MHAmhSirvBq2Bwq7DorSikES10UWxDpBuhyEx3gGBeiducirY1f2KdODlWYDmoNh5zSJmENcF9mwfSiOCcyfBEC4ttKle2E2BqYLBaQRbwdsl8zVd4BA8eSg81Eozi0invoKcSUUmoV6+8tbBylpWQWCexpJxYgVmRhTIJC254tPJWIhxbjq8S5DwluqtCkLZ+RwbX+wiEZ6YkdoGXqBZG0S5wIBhNRrGN+X5DhSLT76a8VC6WOIKyQmLZEmi192L94DJ5rJEiKOu5Ck9YntC8BYnduQ3xgQiDUGrjHnoosIceayOgtzoIjCOj6b0gqp6U+ZAIy3bwWlEBG/KskGgdQkRYqm1UmTxWl7MQI4XliwrY0GnFJz1Vbpj0h1BJl1QK7XRgXzv3BobDdYDhbyI4EkwAEFUDJ/pdy0NDN7GCovWE5Ic3trMeL4uXUvCYzjJ1kNaUeLjZeqLrjrjcsOlOUvbXj203XVP10IV4V0cNG9gAHnlj+bn3g6MgHCTwO1F8DVBYVlAkd3ImzyuFmDeyYqHnt/uCHX+blcljHcAP7i2OJ3UKQAtR6oITXmWf49kSR2itnREHgJHwXmPCNPquG/vWie6ZFsJmLga2k4LqIcojgXiiHVxLtGAcUZnj/GM6ypNj+R+WWAEVTpvzVYEWfQ4jQv8c9v8wDeUiJNMS+38hqt0KwV9t0j2n/3N2s+3+7y6Tx3qtoNeKiatwLmJBlDCAP5vQQq9hPIuEr26m7LvolTYDeKkQVoEwPdRRGMt0i91W9t0yqJFAmygi4Z1bNH3w23yx7i6Tx2r6bloE4O+Ll/28RWgqGoS5UXid+dJrDHPIo5BPgb8K3GbjmCJsCk+HF3F/OuXlj7y5IWZaoCIRq1Azlhxx8WdsThoXW2+ZhLUDIugy3sXzTFY0LFtyW5Zk2fdMsPZF7x4Kq1FnN8IEJut8CYICG3B8eC5sD7+FABsUFnBHyID4d5BJ2WL7+4h5gtbWtu0sUyjcDhGMj3gdWoUWl37NERFTL8veiNVu8jpopIxtI9iNeASYyLgn/Q1gB6WwBef4LWp78C+XSTl2pIw/X4IoYVkbFxw3v43t28okrK0sWu+jQpdtB5H3Y01fVPRSYnvtC1q0UxFDQSd70/+AnaAHst30kO4BBSWzA+faA/aGbmetDyCdtLHvBY+Li3VfXKmfy71UplD4HIvRd1xBys5MX4u8cxPbJGZCgqKo08UMBcNavNVoaqiL+wPVFzqptl0yhFEkA3F1o7UBG1mgz+ny8L9KypZDRGyOyJ4rk7A2uTlTXEgsi+2l9b2UNyFBbFGTrncOg4GIwDvJKOZZHaAulwsN8hYaXkpy4Rp5PRRhL4TVgz1NWK4S0SKwlNb/EgniCKwWGxVCQv9tz5ap5/2ZwvdW/nRx0nQTc2Lrdm4iyVPqQ0Qlg/beAUaQTrbLqBkWBlOFw5nq96iVncUP5aEHQF4o6VdKFJr9Cs/IQuHRhF8LznYYry3T0OQngHkSAzJYjVbKTKpp1QA4Qe0jZn8PBJUz7PU7MrlLj/Pjz7RpYbUpNfIgWDOElM+JeahDYgloHdRnR43S2gGM7oja+LDubjuS9MkyjSDdBjbrMdhSR1kLTaEvrtRFTFas9FwyI4yzapSwOgWOXcd+GVslVymVOV+iSmJOYOYrNkMWGhSYfF5jiW3zr5P9o2z0374ZXvuV0giLAlrZLWXrnXSb4I9pVyLV589rdi4FhQXsPArrbECmhcWTarfHk/EEZtC7UIfAUhGBY6OTRlxBsa3/LpaVpZqwSq+00kyoMJ7LislOvvBF2SBNZsd6CrxM17JTtsTJkHbJsM36RXZihqgS8GREpunoxbHykOrefyEiIuBfB6nra/OznrKtj5WH8J9uT7nFDs9162KLRH+VNK2ZAaYcS4eavdyu5qsaj2VnrIoEevXgYOcZr7fPFvgUTZCjxM8icyZJ7sy1bHo9+H5i/0BawtVmnm0AEBzP5ZZZ9xcLSdh9oNZT95ZtoICIaCO+LkhhF28QN0grZbsiiL9GZIFzNkMiXSP+Z7fXjUSWKHiWlMtj0UvdnYdwmTMdPOK1VLcDsWuBkrr1VrJQR2RNkDphfmW7Gv0xqHaqhP+NmeK5EpL3ebBeWP6U9VoEdeOpmsZbCTB3cV9phNUaHJbCXuZ2fqpZKr7o7Ne30RIjKqCdiLd+Fcmcbmwq2RdXQwkLyEAgRWoXkqPN+U/LMCeJ03FqwqDU72S9dKEQNjwOuw4EwYY3O1ZcyJPIIv0UEq0w2AmLZk1Qp2fSLJkMKC6e2K5wYy0xyym7L33ykNg5iA4NostgPVhTxoXXWrnJfHDTS27LuSwh5Ia8+NJYtIT7nJX1SOJ9iY5N6vwl/dp9QRErrJoWmC8q/erKlhdLWzlDIQi3onwV7OAm2/yw6HyNYI2Y8KeFZkOc1AW7Goz7dTpmegYPUk8MPbQSEtVwRmduUkOFyKbUUS5CTtCqrl1KWG5tfx32VtlXFo9lvc92lJdQbPqvTkicGaittGkhWVH5S2GTurcOqJeQ2K9TtTGY2DVQzX/EUldkxlUXIZWX7p4VloDtoHweq2n7r64F56Oc2pfQ8cUaJFR53koEZD2Tn97IOU0G7E060/kWadd/Jt7qC8540Ib97iA7rwmlAuQys8lOAM4hwOvUvhKFQtspuo5PiGdKW2QVEPX63ybwTp5l6lZQQvS7A1xB2YSvoYRmQ6I/aspcDAlkFBnbKLUiNEFq5bcUrBUJl+5LmqxXAleCv0A9s7NM457Kdi2oMq3NlQU5zlu0n9jswf8GTIoKVgX4NjXwJ0SmmGqaRPbrToic56MEe7H3y0DyrVJ1N7gTG5Ln8mTlKgpHUHURT/wbtmwy7llzTtp44k5r3aeNy0bd/pcU2n1C5lBzvxulgHzyZeH/oKwXKGOhTMLKTYdnciLME6GY1Qy15i4b8sw1BN63vXuJvCsyS03hDce0K3y1kDkCyxwhRRTPstjod81JPU93FeeGLag81Uz6okIQyvnVvYdDVPeheAO4NNS3HhfS2qX+l2cLVlBKSMZRaGt+Lj43y9/8JNDmW7Tmu3s9XFGRyF9fEvqu6YvZx1G5AHwxT8IyCGxKKT1WkfQVLwQPgEmhrbifN/ImsNx6K3uvrLj8LgfBejYRruOphIiooosnDfDbxn18MRHr6pejfhMIoag/goajwY/AeaX7hlXxAMXFUpaUAJwHnoCIhul8WMoa7zv/NJ4wdV7lhUATCjWRPpDeFttkGdYmCMQRMjCvnHkL5VzJLpTPg5UTFfjFobiBKTx/Q1EKj2X/uBNzD54H86x3dyKCJ6C2iKic3DcuKkELSkicWF63CWI8lrvxmnjt81F/vv8LnYp9i0Lh+8CPwctgF1gW/CWc7+F0og8H2SaDFWAv2Ao+r9bw92ZrLgE3Ww9l634a4iTmRlQOKfFFZbsERJHEPC1adceVb9tsu3bpN8Pexroi1R9uBPhXutHPBW5s/yp4ErwCfgZOVfr4NHgabAcPgSMHKqxzwXTwc/A8+FPwExs2w2ngI+CQlrnCneC/wIfAvZTAV0JP8gmVhhCT68yDCFY7T+/KAXhi8u6B9zujK3ZE+plSYn6BY+vuByM23scT+DUozwNBYQWf9H4WhS0AFo3cyAywAOzlvf8AuLtFPGeCb4OR4BfgRN7n2kCEdSeYAD4K/hjsBmPBoYEbBfRv9iEjnA0Oosf7JLic7RcoUXmdnt2wn4DdrMUgYjI2Tl0LVQnJ5liRXEfXU/81T/zpznO7zvFGsJthTwPdNuxZuH7OL+k49LYRTOF9nwaWUdl/wv2Xtzif4ymuQ8DJAxHWY2APy8PBINBUc/4X0UstVcdOoV1O+9+0R9k/HuXJhc3gFLATxEVUj0Qaf1aoYD2UrdtOUkXqUBP8mO2JKSaunbCngM1eTy9Q5XAJeA94SouBQlmnHEhoWZN8Et32T2lXSvoTFRYRz5OBb4BdbJ9Lz/S3wc5Rexftq8oeGHYmifVUFrY/BXsy2G2jhy37eW4kHKYKV0wxcaWC++EyHxv7/fAp59qN8smwTwF9AX2BFcOiC6/xoIXgj8B6cD/1kDKC7eUBv6E9eEDCYmx9HBwDbgYXs/04hsAl4NZgt0Kdt077uzCyKLSnsNdO2sAqcCrFZb2UTWGEmrWCt6yLIrgey8VfcZ5ELoArMvvBd8OeivoqLVz/w0o5so1gX+MCJukngW79vXykRrsnKiy6yQdBF9eym9MyjOdTjLkfozf6DNu/By5sCZejacfQvui9E6T1rs+jKM8EOyJ/6G7K4t9f7akM/kqfwBcWsQKLeCYjMM/z7cBxM1F+VJ1XC8gXmL8NAg+DmeBmOpYXuO9lUAROolT3efNAOkivBh187FzLntvA8gq1Vu37wWTmUhu4by6YxcfZs3nsspDZyXFo8yOIeKVVsDNg7wXjuD8qMFuPrLYhGB3FRx/EBWa9VLOlnJMMFGJJy/YrnP8jb86PEvm7bx27xbJs+UBi/EVgKrsRviIhjotEIwcDk3l/f9jSzbQiJqyUYZBPAEC2qeC7JJBrKaxvgmVU/AL2e+0EGb3Y1xh2dKSwNnNzrungx+AYKyonx3K9pJdvO+Ew+mSYOlhFU1SeuETAlp+Dj6OwlT9HGo4XKpxvlA0+8vQ3Uy13dClzrispqMXgetDBlOgXMWEl4CpHzVuD3e5lAv8063vBsVT+4eBX4BthTLE1HiV8cTFivAQ7A/YG7D/f9Uqpdx6SuoLyt8QUHPV5K1XVNBSRiEpswXaWAcPSfJSZNA+I2NK3D4BtYI1qWxvstpr2bnASI9EQ8FOKLMSE1QRfk2qUR0jrtoNuNBARTeL2Y7EcTcb3ws6BXQ67CHaYk5/RxsXkf8WFioBR1aVOp2mTmFBIS4GxrgZp70J5Psq3SVsSm5jhrSqvw+EPSRAQeeLbQ+Rt8a7QzyttfmWxuewSlKeCFX7uSry2RDAdo344jK8CynbB/08RL36vQHkq7G3uwD6bN/gXUz5kaYbN+MlzJkSTbrtvE+zxsHNxzh02L1MoAam2yEr9LvH1joWBdj/sgJ0LezzsJiUWbXXZis8eWx5h2T8yx5sYgYnV15f1AnYx6hPBjSj36nNaR2HmKlrs5sTFqCfzVxO1C3P3wt4IOxEsBoUSTERUce9FsZfNY8Xe07pP5n6bHL8ddh7aJqF8O2xuk/n9WDSddeK5tIG+5vFygBz1O8AklOehbTvswFy3HwrcdlAujyVERQYiQkzd7oT14Gzwh+DbYK/rpVK/70qsgz0wkrgBG4v3wn4bHIXyWWC96dyLd4DGUOdLyhQKtZfRAtHYF9W+CN2+yPWwF8COg70UrHNfOKcRocW9leO13OHL68ClKI+DvYB17osk32yPvov0/3pLlrxnINEeOhYCiT+8yGInr2wDC6GHI2GPgb0GdqP/1LfP+VW0z4Jq3oi2a8Ax4EjUF8JuE8EkzhNfKliRedO/Yo/JZUzeB/q+MN557b/zc8ewr4G9DEwk88EdaN8senC6guLhUPdjbEH5Dtj5YCLKILkMdo3/slra46Ewi4jI1klZQ2Hc49hUwhGUfy4/1Ilj2QgWgbPQPhb2QL7GuBh8HdyDttVgUyjCb1H/XYuYUE7QFjaxR/oe1L/OY2eifCAYA5A3pYvorbTqvcfiyPTvqGh8AUp7iWbprErC23z7NXiYeNuVylbEPFZFRSWsikpYFZWwKireiuS9okraK49VUQmrohJWRUUlrIpKWG897uor5ETwKOfVrQZnDGT1lUpY1eauvsKZRvdyEu9dYCy4A5wQW32lEla1uauvcDmmdi4rMA9cARJwfGz1lUpY1eauvsLQ1wtm0HudBHKwLLb6StVBWm27g789CS7ghNF1bFtAIY2lx3/NWX2lElaFyzQm9c8xtzqNE3rXktjqK5YqFFYwh+oAc5hfncEQ+PmBr75SCavC0lQLyo2j7QXdTNYTMAt0qtVXqlBY4XI912L9DriMCXwOrgUhuvpK5bEqwAPga2r1lZVgCrgOPANuAFPBfWr1le/x+IsAwma1JUVRhGqrqDxWRSWsikpYFRWVsCre/vw/jy4G2fRxv14AAAAASUVORK5CYII=)
 Hue values on the color wheel
 

 HSV stands for hue, saturation, and value.
 


* Hue ranges from 0 to 360 on a color wheel, where 0 is red, 60 is yellow,
120 is green, and so on as seen in the image.
* Saturation is how colorful this color is; it ranges from 0 which means a
shade of gray, to 100 which is fully colored.
* Value is the brightness of the biggest red, green, or blue component, and
ranges from 0 to 100. A value of 0 is always black.



 All pure hues such as red (hue=0) have a saturation of 100 and a value of
100. As saturation decreases, the colors turns whiter. Lower values mean
darker colors and darker shades of gray.
 



 In HSV, saturation is less meaningful as value gets closer to 0. Black
of course always has a value of 0. With 10 as the value, saturation=100 gives
you a very dark color whereas saturation=0 is a 10% shade of gray.
 


### 
 COLORSPACE\_HSL



 HSL is a little more intuitive than HSV. Here, the value is replaced by
luminance, which again ranges from 0 to 100. Luminance is the average of the
minimum and maximum values of the red, green, and blue components.
 



 Black has a luminance of 0; white has a luminance of 100. Pure hues all
have a saturation of 100 and luminance of 50. As saturation decreases, the
color will approach a grayscale shade of L%.
 



 Saturation is less meaningful the closer luminance is to 0 or 100. At a
luminance of 100, the saturation is totally irrelevant. At 90, high saturation
will get you a very light shade of the hue but that isn't very far off from a
90% shade of gray.
 


### 
 COLORSPACE\_HCY



 HCY stands for
 **hue** 
 ,
 **chroma** 
 , and the Y is for grayscale
luminance. (Again chroma and Y range from 0 to 100.) This color space is
based around the apparent brightness of each color according to a rough
approximation of human vision.
 



 Chroma is similar to saturation in that it determines how far from
grayscale the color is. As chroma decreases toward 0, the color approaches
a grayscale shade of Y%. What's different about HCY color from HSV or HSL
is that at chroma=0 and chroma=100 the colors should appear equally
bright. Pure red, therefore, has a hue of 0, a chroma of 100, and a Y
luminance of only 29.9—roughly what red would look like in black &
white with all the color leached out.
 




---
stddef.dm file
----------------



 This is a special file that's included in all projects when you compile.
It contains various constants, definitions of some built-in datums, and so on.
 



 You can see the contents of this file by creating a new file in Dream
Maker called
 
 stddef.dm
 
 . It will automatically be filled with the
standard definitions.
 



 The contents of
 
 stddef.dm
 
 may change with new BYOND versions.
However an eye is always kept on backwards-compatibility.
 




---


 Note: You can specify a different hub path and hub\_password
by adding these as extra arguments, but this is not recommended for security
reasons. If you use this feature, it should only be on games that cannot be
downloaded by the public.





---



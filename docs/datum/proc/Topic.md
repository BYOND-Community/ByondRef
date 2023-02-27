

 Topic proc (datum)
--------------------




**See also:** 


[Topic proc (client)](#/client/proc/Topic) 

[ref text macro](#/DM/text/macros/ref) 




**See also:** 

**See also:**

[Topic proc (client)](#/client/proc/Topic) 

[ref text macro](#/DM/text/macros/ref) 


[Topic proc (client)](#/client/proc/Topic)

[ref text macro](#/DM/text/macros/ref) 

[ref text macro](#/DM/text/macros/ref)


**Format:** 


 Topic(href,href\_list[])
 


**Format:** 

**Format:**

 Topic(href,href\_list[])



**Args:** 


 href: the hyperlink data (following ? in the URL).
 
 href\_list: key/value list (from params2list(href)).
 



**Args:** 

**Args:**

 href: the hyperlink data (following ? in the URL).
 
 href\_list: key/value list (from params2list(href)).
 


 href\_list: key/value list (from params2list(href)).


 This procedure is called by the default
 
 client.Topic()
 
 proc when
the href contains a parameter called "src" containing an object reference.




 client.Topic()

### 
 Example:



 mob/verb/test()
 usr << "Click
 [here](?src=\ref[src];action=startgame) 
 !"
mob/Topic(href,href\_list[])
 switch(href\_list["action"])
 if("startgame")
 usr << "Starting game..."

[here](?src=\ref[src];action=startgame)

 The above example uses an embedded reference to the player's own mob to
create a hyperlink to that mob's
 
 Topic()
 
 proc. You can easily add
different actions, parameters, and so forth. Just remember that the parameter
values are always stored as text, so you need to convert those to whatever
data format you need using procedures such as
 
 text2num()
 
 ,
 
 locate()
 
 , etc.




 Topic()


 text2num()


 locate()


 Always validate the input in
 
 Topic()
 
 calls
to make sure it's correct and the query you're recieving is legitimate.




 Topic()



---



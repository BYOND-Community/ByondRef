

 link proc
-----------




**See also:** 


[<< output operator](#/operator/%3c%3c/output) 

[Topic proc (client)](#/client/proc/Topic) 

[file proc](#/proc/file) 

[run proc](#/proc/run) 






**See also:** 

**See also:**

[<< output operator](#/operator/%3c%3c/output) 

[Topic proc (client)](#/client/proc/Topic) 

[file proc](#/proc/file) 

[run proc](#/proc/run) 




[<< output operator](#/operator/%3c%3c/output)

[Topic proc (client)](#/client/proc/Topic) 

[file proc](#/proc/file) 

[run proc](#/proc/run) 



[Topic proc (client)](#/client/proc/Topic)

[file proc](#/proc/file) 

[run proc](#/proc/run) 


[file proc](#/proc/file)

[run proc](#/proc/run) 

[run proc](#/proc/run)


**Format:** 


 O << link(url)
 


**Format:** 

**Format:**

 O << link(url)


 This causes the recipient (O) to view the specified url. The url could
be a web or BYOND address. In the latter case, the player will disconnect
from the current world and connect to the specified one.




 The format of a BYOND url is as follows:




 byond://address:port?TopicData


 To access a registered world, address:port may be replaced by the
registered name in the hub. The optional topic data is processed by the
world once the player has connected. If only a topic is specified, the
current world processes it.



### 
 Example:



 usr << link("byond://byond.com:6000") //BYOND address
usr << link("http://www.byond.com") //web address
usr << link("?myTopic") //topic



---



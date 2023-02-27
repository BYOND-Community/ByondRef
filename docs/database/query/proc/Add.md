

 Add proc (database query)
---------------------------




**See also:** 


[database query datum](#/database/query) 

[Clear proc (database query)](#/database/query/proc/Clear) 




**See also:** 

**See also:**

[database query datum](#/database/query) 

[Clear proc (database query)](#/database/query/proc/Clear) 


[database query datum](#/database/query)

[Clear proc (database query)](#/database/query/proc/Clear) 

[Clear proc (database query)](#/database/query/proc/Clear)


**Format:** 


 Add(text, item1, item2, ...)
 


**Format:** 

**Format:**

 Add(text, item1, item2, ...)



**Args:** 


 text: Text to add to the query
 
 item1, item2, etc.: Items that will replace question marks in text
 



**Args:** 

**Args:**

 text: Text to add to the query
 
 item1, item2, etc.: Items that will replace question marks in text
 


 item1, item2, etc.: Items that will replace question marks in text


 Adds text to a database query. If this datum was already used to run a
query, Clear() will be called automatically.




 If your text includes question marks, they will be replaced with the other
items listed in the proc arguments. If that item is a string, quotes will be
put around it for the query text. Files in the cache (such as icons) will be
added as BLOB values.




 After the query has been built, call Execute() to run it.



### 
 Example:



 var/database/db = new("mydb.db")
var/database/query/q = new
q.Add("INSERT INTO quests (name, quest, complete) VALUES (?,?,?)", usr.key, quest\_name, 1)
q.Execute(db)


 In the example above, the query text might look like this:





 INSERT INTO quests (name, quest, complete) VALUES ('Tom','Save the Dog',1)
 




 INSERT INTO quests (name, quest, complete) VALUES ('Tom','Save the Dog',1)



---



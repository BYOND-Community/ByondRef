

 database datum
----------------




**See also:** 


[database query datum](#/database/query) 

[procs (database)](#/database/proc) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 





**See also:** 

**See also:**

[database query datum](#/database/query) 

[procs (database)](#/database/proc) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 



[database query datum](#/database/query)

[procs (database)](#/database/proc) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 


[procs (database)](#/database/proc)

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[stddef.dm file](#/{{appendix}}/stddef%2edm)

 A /database datum gives you the ability to create or access a database
using SQLite, which allows you to run complex database queries on any
platform.




 Creating a /database/query datum will let you put together a query, and
once it's ready you can call its Execute() proc to run it.




 SQLite databases in BYOND support numerical values (such as INTEGER or
FLOAT), text (TEXT), and cache files such as icons (BLOB). Null values are
also allowed.



### 
 Example:



 var/database/db = new("mydb.db")
var/database/query/q = new("SELECT \* FROM my\_table WHERE name=?", usr.key)

if(q.Execute(db) && q.NextRow())
 // returns a list such as list(name="MyName", score=123)
 return q.GetRowData()
// no data found
return null



---



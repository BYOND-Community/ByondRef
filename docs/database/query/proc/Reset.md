

 Reset proc (database query)
-----------------------------




**See also:** 


[database datum](#/database) 

[database query datum](#/database/query) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 






**See also:** 

**See also:**

[database datum](#/database) 

[database query datum](#/database/query) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 




[database datum](#/database)

[database query datum](#/database/query) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 



[database query datum](#/database/query)

[Execute proc (database query)](#/database/query/proc/Execute) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 


[Execute proc (database query)](#/database/query/proc/Execute)

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[NextRow proc (database query)](#/database/query/proc/NextRow)


**Format:** 


 Reset()
 


**Format:** 

**Format:**

 Reset()


 If a query returns any rows of results, Reset() will go back to the
beginning just after Execute() was called. This is useful if you have
called NextRow() repeatedly to retrieve a number of rows, but need to
go back to the start of the query for some other reason. This can also be
used to count the total number of result rows if needed, but for best
performance that isn't recommended.





---



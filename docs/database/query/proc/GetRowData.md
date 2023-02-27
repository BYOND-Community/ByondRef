

 GetRowData proc (database query)
----------------------------------




**See also:** 


[database datum](#/database) 

[database query datum](#/database/query) 

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 









**See also:** 

**See also:**

[database datum](#/database) 

[database query datum](#/database/query) 

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 







[database datum](#/database)

[database query datum](#/database/query) 

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 






[database query datum](#/database/query)

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 





[Columns proc (database query)](#/database/query/proc/Columns)

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 




[Execute proc (database query)](#/database/query/proc/Execute)

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 



[GetColumn proc (database query)](#/database/query/proc/GetColumn)

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 


[NextRow proc (database query)](#/database/query/proc/NextRow)

[Reset proc (database query)](#/database/query/proc/Reset) 

[Reset proc (database query)](#/database/query/proc/Reset)


**Format:** 


 GetRowData()
 


**Format:** 

**Format:**

 GetRowData()


 Returns a list with the current result row for this query. If you
haven't already called Execute() and NextRow(), you should do that
first.




 The list returned is an associative list with name=value pairs. A
typical result might look like this:





 list("name" = "Tom", "quest" = "Save a Dog", complete = 1)
 




 list("name" = "Tom", "quest" = "Save a Dog", complete = 1)


 The values returned depend on what type the database table thinks they
are. For instance if you defined a column as INTEGER or FLOAT, the value
should be a number. TEXT is still text, and null values are returned as null.
If an icon was saved into a BLOB field, the result is an icon file.





---



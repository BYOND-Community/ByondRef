

 NextRow proc (database query)
-------------------------------




**See also:** 


[database datum](#/database) 

[database query datum](#/database/query) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[Reset proc (database query)](#/database/query/proc/Reset) 








**See also:** 

**See also:**

[database datum](#/database) 

[database query datum](#/database/query) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[Reset proc (database query)](#/database/query/proc/Reset) 






[database datum](#/database)

[database query datum](#/database/query) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[Reset proc (database query)](#/database/query/proc/Reset) 





[database query datum](#/database/query)

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[Reset proc (database query)](#/database/query/proc/Reset) 




[Execute proc (database query)](#/database/query/proc/Execute)

[GetColumn proc (database query)](#/database/query/proc/GetColumn) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[Reset proc (database query)](#/database/query/proc/Reset) 



[GetColumn proc (database query)](#/database/query/proc/GetColumn)

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[Reset proc (database query)](#/database/query/proc/Reset) 


[GetRowData proc (database query)](#/database/query/proc/GetRowData)

[Reset proc (database query)](#/database/query/proc/Reset) 

[Reset proc (database query)](#/database/query/proc/Reset)


**Format:** 


 NextRow()
 


**Format:** 

**Format:**

 NextRow()


 If there are result rows in this query (Execute() must be called to run
the query first), NextRow() will retrieve the next row and return 1 if it
found a row, or 0 if the results are all finished. NextRow() is typically
called in a while() loop.




 After calling NextRow(), you can call GetColumn() or GetRowData() to get
information about the results in this row.




 Call Reset() if you want to rewind the query to the beginning.





---



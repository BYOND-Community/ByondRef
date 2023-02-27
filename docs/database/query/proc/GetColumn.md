

 GetColumn proc (database query)
---------------------------------




**See also:** 


[database datum](#/database) 

[database query datum](#/database/query) 

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 









**See also:** 

**See also:**

[database datum](#/database) 

[database query datum](#/database/query) 

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 







[database datum](#/database)

[database query datum](#/database/query) 

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 






[database query datum](#/database/query)

[Columns proc (database query)](#/database/query/proc/Columns) 

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 





[Columns proc (database query)](#/database/query/proc/Columns)

[Execute proc (database query)](#/database/query/proc/Execute) 

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 




[Execute proc (database query)](#/database/query/proc/Execute)

[GetRowData proc (database query)](#/database/query/proc/GetRowData) 

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 



[GetRowData proc (database query)](#/database/query/proc/GetRowData)

[NextRow proc (database query)](#/database/query/proc/NextRow) 

[Reset proc (database query)](#/database/query/proc/Reset) 


[NextRow proc (database query)](#/database/query/proc/NextRow)

[Reset proc (database query)](#/database/query/proc/Reset) 

[Reset proc (database query)](#/database/query/proc/Reset)


**Format:** 


 GetColumn(column)
 


**Format:** 

**Format:**

 GetColumn(column)



**Args:** 


 column: The column number whose value should be retrieved
 


**Args:** 

**Args:**

 column: The column number whose value should be retrieved


 Gets the value from the Nth column in this row of results. If you haven't
already called Execute() and NextRow(), you should do that first.




 To get the name of the column, not the value for this row, call
Columns(column) instead.




 The value returned depends on what type the database table thinks it is.
For instance if you defined a column as INTEGER or FLOAT, the value should
be a number. TEXT is still text, and null values are returned as null. If an
icon was saved into a BLOB field, the result is an icon file.





---





 Import proc (client)
----------------------




**See also:** 


[Export proc (client)](#/client/proc/Export) 

[New proc (client)](#/client/proc/New) 

[savefile](#/savefile) 





**See also:** 

**See also:**

[Export proc (client)](#/client/proc/Export) 

[New proc (client)](#/client/proc/New) 

[savefile](#/savefile) 



[Export proc (client)](#/client/proc/Export)

[New proc (client)](#/client/proc/New) 

[savefile](#/savefile) 


[New proc (client)](#/client/proc/New)

[savefile](#/savefile) 

[savefile](#/savefile)


**Format:** 


 client.Import(Query)
 


**Format:** 

**Format:**

 client.Import(Query)



**Args:** 


 Query: optional query parameters
 


**Args:** 

**Args:**

 Query: optional query parameters


 When no query parameters are given, this returns the client-side file last
exported with
 `client.Export()` 
 . This comes as an entry in the
resource cache, which can be opened as a savefile among other things. If
there is no file, null is returned. For an example, see
 [client.Export](#/client/proc/Export) 
 .



`client.Export()`
[client.Export](#/client/proc/Export)

 When there are query parameters, these may be used to import a file from
some alternate source. Currently this is not supported.





---



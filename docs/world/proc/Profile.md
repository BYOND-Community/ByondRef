

 Profile proc (world)
----------------------




**Format:** 


 Profile(command, format)
 
 Profile(command, type, format)
 



**Format:** 

**Format:**

 Profile(command, format)
 
 Profile(command, type, format)
 


 Profile(command, type, format)



**Returns:** 


 Profilng data or null
 


**Returns:** 

**Returns:**

 Profilng data or null



**Args:** 


 command: A numerical value that says whether to start, stop, refresh, etc.
 
 type: A type of profile to use, other than proc profiling.
 
 format: Optional format for output data
 




**Args:** 

**Args:**

 command: A numerical value that says whether to start, stop, refresh, etc.
 
 type: A type of profile to use, other than proc profiling.
 
 format: Optional format for output data
 



 type: A type of profile to use, other than proc profiling.
 
 format: Optional format for output data
 


 format: Optional format for output data


 Interacts with the built-in server profiler without requiring the host to do
so via Dream Daemon, or an authorized player via Dream Seeker.




 The
 
 command
 
 value is built from bitflags, so it can combine any of
these three values via the
 
 |
 
 operator:




 command


 |



 PROFILE\_STOP
 

 Stop profiling. Not using this flag will start/continue profiling.
 

 PROFILE\_CLEAR
 

 Clear all profile data. This will also cause the proc to return null.
 

 PROFILE\_AVERAGE
 

 Any output data should use average times instead of total times.
 


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
 


 PROFILE\_START


 Start/continue profiling but don't clear any existing data.


 PROFILE\_REFRESH


 Currently this is the same as
 
 PROFILE\_START
 
 .


 PROFILE\_START


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




 "name"


 "self"


 "total"


 "real"


 "over"


 "calls"


 The optional
 
 format
 
 argument however can be used to return the
data in other formats. Currently the only accepted value is
 
 "json"
 
 ,
which will output the same data in JSON format.




 format


 "json"

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




 "sendmaps"


 type


 "name"


 "value"


 "calls"


 The JSON format will include a
 
 unit
 
 property data that is not a
raw number, such as a time value.




 unit



---



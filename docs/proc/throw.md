

 throw statement
-----------------




**See also:** 


[try statement](#/proc/try) 

[Error proc (world)](#/world/proc/Error) 

[EXCEPTION proc](#/proc/EXCEPTION) 

[exception](#/exception) 






**See also:** 

**See also:**

[try statement](#/proc/try) 

[Error proc (world)](#/world/proc/Error) 

[EXCEPTION proc](#/proc/EXCEPTION) 

[exception](#/exception) 




[try statement](#/proc/try)

[Error proc (world)](#/world/proc/Error) 

[EXCEPTION proc](#/proc/EXCEPTION) 

[exception](#/exception) 



[Error proc (world)](#/world/proc/Error)

[EXCEPTION proc](#/proc/EXCEPTION) 

[exception](#/exception) 


[EXCEPTION proc](#/proc/EXCEPTION)

[exception](#/exception) 

[exception](#/exception)


**Format:** 


 throw Value
 


**Format:** 

**Format:**

 throw Value



**Args:** 


 Value: Any value, which will be sent to catch() if present.
 


**Args:** 

**Args:**

 Value: Any value, which will be sent to catch() if present.


 This keyword throws an exception, which will stop executing the current
proc and go to the most recent catch block if one is present. The catch block
will receive the thrown value. If there is no try/catch in use, the exception
will be passed to
 
 world.Error()
 
 (if present), then the current proc
will end and control will return to the caller.




 world.Error()

### 
 Example:



 try
 if(!src.ready) throw EXCEPTION("Not ready")
 DoSomething()
catch(var/e)
 world.log << "Exception: [e]"


 You can use the
 
 EXCEPTION
 
 macro to create a new
 
 /exception
 
 datum, which contains a value or message as well as the file and line number
where the exception was created. The thrown value does not have to be an
 
 /exception
 
 datum; you can throw anything, even null.




 EXCEPTION


 /exception


 /exception



---



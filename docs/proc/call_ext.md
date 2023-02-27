

 call\_ext proc
----------------




**See also:** 


[arglist proc](#/proc/arglist) 

[call proc](#/proc/call) 

[path operators](#/operator/path) 





**See also:** 

**See also:**

[arglist proc](#/proc/arglist) 

[call proc](#/proc/call) 

[path operators](#/operator/path) 



[arglist proc](#/proc/arglist)

[call proc](#/proc/call) 

[path operators](#/operator/path) 


[call proc](#/proc/call)

[path operators](#/operator/path) 

[path operators](#/operator/path)


**Format:** 


 call\_ext(LibName,FuncName)(Arguments)
 


**Format:** 

**Format:**

 call\_ext(LibName,FuncName)(Arguments)



**Args:** 


 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 



**Args:** 

**Args:**

 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 


 FuncName: name of function in external library ("func")



**Returns:** 


 The return value of the external library function.
 


**Returns:** 

**Returns:**

 The return value of the external library function.


 This instruction exists in order to access third-party libraries (.DLL
files on Windows, .SO files on Unix), as long as the one or more of the
following conditions is met:



* The library is located in the BYOND user
 
 bin/
 
 folder
(
 
 ~/.byond/bin
 
 on Unix, typically
 
 %APPDATA%/Documents/BYOND/bin/
 
 on Windows). This is intended to
allow the user to install permanently "trusted" libraries.
 ***OR***
* The server is run in
 
 -trusted
 
 mode.
 ***OR***
* The server grants permission to access the library at runtime, through a
prompt query.


- The library is located in the BYOND user
 
 bin/
 
 folder
(
 
 ~/.byond/bin
 
 on Unix, typically
 
 %APPDATA%/Documents/BYOND/bin/
 
 on Windows). This is intended to
allow the user to install permanently "trusted" libraries.
 ***OR***


 bin/


 ~/.byond/bin


 %APPDATA%/Documents/BYOND/bin/

***OR***
*OR*
- The server is run in
 
 -trusted
 
 mode.
 ***OR***


 -trusted

***OR***
*OR*
- The server grants permission to access the library at runtime, through a
prompt query.


 These functions must be prototyped in the DLL as:




```
extern "C" char *func(int argc, char *argv[]);
// argc = #arguments, argv[] = array of arguments

```

### 
 Example:



```
// test.dll, a win32 C++ library compiled in VC++:
#include <string.h>
// This is an example of an exported function.
// windows requires __declspec(dllexport) to be used to 
// declare public symbols
// the name of the function from within the dll may be compiler-dependent
// (in this case it will usually be "merge" or "_merge)
// Google "name decoration" for more information on this exciting topic.
extern "C" __declspec(dllexport) char *merge(int n, char *v[]) 
{
   static char buf[500]; 
   *buf=0;
   for(int i=0;i<n;i++) {
      strcat(buf,v[i]); // we should bounds-check but it's a stupid example!
   }
   return buf;
}

```


 // DM code to use test.dll
mob/verb/test()
 usr << call\_ext("test.dll","merge")("fee","fi","fo") // returns "feefifo"

// As with the other call() versions, arglist() may be used to do runtime arguments:
mob/verb/argtest()
 var/L = list("fee","fi","fo")
 usr << call\_ext("test.dll","func")(arglist(L)) // returns "feefifo"


 As the library prototype is
 
 char\*\*
 
 , the
 
 call\_ext()
 
 arguments must be strings. Other types (like numbers) will be passed as the
empty string (
 
 ""
 
 ) into the library function.




 char\*\*


 call\_ext()


 ""


 Note for advanced users: on Windows,
 
 call\_ext()
 
 uses the
 
 \_\_cdecl
 
 convention by default. If you are designing or linking to a
DLL that uses the
 
 \_\_stdcall
 
 convention instead, you can inform
 
 call\_ext()
 
 by prefacing the function name with the
 
 "@"
 
 symbol. E.g.,
 
 call\_ext("test.dll","@merge")
 
 would call a version of
 
 merge
 
 declared with the
 
 \_\_stdcall
 
 convention. Typically
these names are further decorated by the linker (in VC++,
 
 "merge"
 
 would be
 
 "
 
 [email protected]
 
 "
 
 , so it'd be accessed with
 
 call\_ext("test.dll",@
 
 [email protected]
 
 "))
 
 .




 call\_ext()


 \_\_cdecl


 \_\_stdcall


 call\_ext()


 "@"


 call\_ext("test.dll","@merge")


 merge


 \_\_stdcall


 "merge"


 "
 
 [email protected]
 
 "


 [email protected]


 call\_ext("test.dll",@
 
 [email protected]
 
 "))


 [email protected]



---



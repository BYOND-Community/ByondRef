

 call proc
-----------




**See also:** 


[arglist proc](#/proc/arglist) 

[call\_ext proc](#/proc/call_ext) 

[hascall proc](#/proc/hascall) 

[path operators](#/operator/path) 






**See also:** 

**See also:**

[arglist proc](#/proc/arglist) 

[call\_ext proc](#/proc/call_ext) 

[hascall proc](#/proc/hascall) 

[path operators](#/operator/path) 




[arglist proc](#/proc/arglist)

[call\_ext proc](#/proc/call_ext) 

[hascall proc](#/proc/hascall) 

[path operators](#/operator/path) 



[call\_ext proc](#/proc/call_ext)

[hascall proc](#/proc/hascall) 

[path operators](#/operator/path) 


[hascall proc](#/proc/hascall)

[path operators](#/operator/path) 

[path operators](#/operator/path)


**Format:** 


 call(ProcRef)(Arguments)
 
 call(Object,ProcName)(Arguments)
 
 call(LibName,FuncName)(Arguments) (use
 
 call\_ext()
 
 instead)
 




**Format:** 

**Format:**

 call(ProcRef)(Arguments)
 
 call(Object,ProcName)(Arguments)
 
 call(LibName,FuncName)(Arguments) (use
 
 call\_ext()
 
 instead)
 



 call(Object,ProcName)(Arguments)
 
 call(LibName,FuncName)(Arguments) (use
 
 call\_ext()
 
 instead)
 


 call(LibName,FuncName)(Arguments) (use
 
 call\_ext()
 
 instead)


 call\_ext()



**Args:** 


 ProcRef: path of proc (/proc/MyProc)
 
 Object: source of proc or verb
 
 ProcName: name of proc or verb ("MyProc")
 
 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 






**Args:** 

**Args:**

 ProcRef: path of proc (/proc/MyProc)
 
 Object: source of proc or verb
 
 ProcName: name of proc or verb ("MyProc")
 
 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 





 Object: source of proc or verb
 
 ProcName: name of proc or verb ("MyProc")
 
 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 




 ProcName: name of proc or verb ("MyProc")
 
 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 



 LibName: name of external library ("test.DLL")
 
 FuncName: name of function in external library ("func")
 


 FuncName: name of function in external library ("func")



**Returns:** 


 The return value of the proc being called.
 


**Returns:** 

**Returns:**

 The return value of the proc being called.


 This instruction exists in order to call procs dynamically, since the proc
reference or name may be an expression rather than a hard-coded value. This
may serve the same purpose as a "function pointer" in C programs.




 The following examples do not demonstrate why you would want to do this,
but the syntax is illustrated. The first one calls a specific procedure by
using a path reference to that procedure.



### 
 Example:



 /proc/MyProc(Arg)
 usr << "MyProc([Arg])"
mob
 var
 MyProc = /proc/MyProc
 verb
 call\_myproc()
 call(MyProc)("Hello, world!")


 The next example calls an object procedure (or verb) by name, rather than
by path.



### 
 Example:



 mob
 proc
 Proc1(Arg)
 usr << "Proc1([Arg])"
 Proc2(Arg)
 usr << "Proc2([Arg])"
 verb
 call\_proc(Proc in list("Proc1","Proc2"))
 call(src,Proc)("Hello, world!")


 In prior versions,
 
 call()
 
 was also used to access third-party
libraries (.DLL files on Windows, .SO files on Unix), but this has been moved
to
 
 call\_ext()
 
 for clarity.




 call()


 call\_ext()



---



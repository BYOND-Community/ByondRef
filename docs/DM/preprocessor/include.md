

 #include directive
--------------------




**Format:** 


 #include "Filename"
 
 #include <Filename>
 



**Format:** 

**Format:**

 #include "Filename"
 
 #include <Filename>
 


 #include <Filename>



**Args:** 


 "Filename": The path to the filename to include, from the current
 directory.
 
 <Filename>: The path inside the BYOND lib directory.
 



**Args:** 

**Args:**

 "Filename": The path to the filename to include, from the current
 directory.
 
 <Filename>: The path inside the BYOND lib directory.
 


 <Filename>: The path inside the BYOND lib directory.


 The
 `#include` 
 statement causes the compiler to process another
file before continuing in the current source file.



`#include`

 If a file is included multiple times, only the first occurrence will be
processed. That is a convenient addition to the standard C preprocessor,
which DM otherwise emulates quite closely.




 The file
 `<stddef.dm>` 
 is automatically included before
all other source code.



`<stddef.dm>`
### 
 Example:



 #include "test.dm" // checks ./test.dm
#include
 
 // checks lib-path/test.dm
 


 // checks lib-path/test.dm


 The BYOND lib directory is called
 `"lib"` 
 and is located in the
BYOND system directory (typically
 `"\Program Files\Byond\lib"` 
 ).
If the file is not found there, it also looks in the user lib directory, which
would typically be
 `"...\Byond\user\
 *login-name* 
 \lib"` 
 .



`"lib"`
`"\Program Files\Byond\lib"`
`"...\Byond\user\
 *login-name* 
 \lib"`
*login-name*

 Note that the compiler interface allows you to include files graphically by
simply clicking the checkbox next to the file. This creates an include
statement for you in the
 `.dme` 
 project environment file. The only
time you would still want to manually include files is when you need to ensure
a certain order of processing. For example, if file
 `"MyCode.dm"` 
 overrides procedure definitions of an object defined in
 `"LibCode.dm"` 
 , you should include
 `"LibCode.dm"` 
 at the
top of
 `"MyCode.dm"` 
 . Most other DM code is independent of order,
but overriding procedure definitions is not. The compiler will warn you in
such cases if you forget.



`.dme`
`"MyCode.dm"`
`"LibCode.dm"`
`"LibCode.dm"`
`"MyCode.dm"`

 Another case in which you should manually include files is if you are
writing a library to be used by other programmers. Since the
 `.dme` 
 file is not distributed with a library, all necessary
inclusions must be made in the
 `.dm` 
 files.



`.dme`
`.dm`


---



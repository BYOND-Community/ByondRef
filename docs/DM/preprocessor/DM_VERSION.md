

 DM\_VERSION macro
-------------------




**See also:** 


[byond\_version var (world)](#/world/var/byond_version) 

[byond\_version var (client)](#/client/var/byond_version) 

[DM\_BUILD macro](#/DM/preprocessor/DM_BUILD) 

[preprocessor](#/DM/preprocessor) 






**See also:** 

**See also:**

[byond\_version var (world)](#/world/var/byond_version) 

[byond\_version var (client)](#/client/var/byond_version) 

[DM\_BUILD macro](#/DM/preprocessor/DM_BUILD) 

[preprocessor](#/DM/preprocessor) 




[byond\_version var (world)](#/world/var/byond_version)

[byond\_version var (client)](#/client/var/byond_version) 

[DM\_BUILD macro](#/DM/preprocessor/DM_BUILD) 

[preprocessor](#/DM/preprocessor) 



[byond\_version var (client)](#/client/var/byond_version)

[DM\_BUILD macro](#/DM/preprocessor/DM_BUILD) 

[preprocessor](#/DM/preprocessor) 


[DM\_BUILD macro](#/DM/preprocessor/DM_BUILD)

[preprocessor](#/DM/preprocessor) 

[preprocessor](#/DM/preprocessor)

 This macro indicates the version of the compiler. This could be useful when
distributing code that uses new language features that would not compile in
older compilers.



### 
 Example:



 #if DM\_VERSION < 230
#error This compiler is too far out of date!
#endif



---





 #warn directive
-----------------




**See also:** 


[preprocessor](#/DM/preprocessor) 

[#error directive](#/DM/preprocessor/error) 




**See also:** 

**See also:**

[preprocessor](#/DM/preprocessor) 

[#error directive](#/DM/preprocessor/error) 


[preprocessor](#/DM/preprocessor)

[#error directive](#/DM/preprocessor/error) 

[#error directive](#/DM/preprocessor/error)


**Format:** 


 #warn Text
 


**Format:** 

**Format:**

 #warn Text



**Args:** 


 Text: a warning message to display
 


**Args:** 

**Args:**

 Text: a warning message to display


 The #warn directive displays the specified message as a warning, but does
not prevent the project from compiling.



### 
 Example:



 #ifdef USE\_LIGHTING
#warn The lighting feature in MyLibrary is experimental.
#endif



---



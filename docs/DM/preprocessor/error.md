

 #error directive
------------------




**See also:** 


[preprocessor](#/DM/preprocessor) 

[#warn directive](#/DM/preprocessor/warn) 




**See also:** 

**See also:**

[preprocessor](#/DM/preprocessor) 

[#warn directive](#/DM/preprocessor/warn) 


[preprocessor](#/DM/preprocessor)

[#warn directive](#/DM/preprocessor/warn) 

[#warn directive](#/DM/preprocessor/warn)


**Format:** 


 #error Text
 


**Format:** 

**Format:**

 #error Text



**Args:** 


 Text: an error message to display
 


**Args:** 

**Args:**

 Text: an error message to display


 The #error directive halts compilation and displays the specified message.



### 
 Example:



 #if DM\_VERSION < 4
#error This compiler is too far out of date!
#endif



---



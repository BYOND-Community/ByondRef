

 initial proc
--------------




**See also:** 


[:: operator](#/operator/::) 

[issaved proc](#/proc/issaved) 

[vars list var (datum)](#/datum/var/vars) 





**See also:** 

**See also:**

[:: operator](#/operator/::) 

[issaved proc](#/proc/issaved) 

[vars list var (datum)](#/datum/var/vars) 



[:: operator](#/operator/::)

[issaved proc](#/proc/issaved) 

[vars list var (datum)](#/datum/var/vars) 


[issaved proc](#/proc/issaved)

[vars list var (datum)](#/datum/var/vars) 

[vars list var (datum)](#/datum/var/vars)


**Format:** 


 initial(Var)
 


**Format:** 

**Format:**

 initial(Var)



**Args:** 


 Var: A variable to find the initial value of.
 


**Args:** 

**Args:**

 Var: A variable to find the initial value of.


 This returns the original compile-time value of a variable. It could
be used to reset a variable to its default value or to check if a variable
has changed.



### 
 Example:



 obj/verb/set\_icon(I as null|icon)
 if(!I) I = initial(icon)
 icon = I



---



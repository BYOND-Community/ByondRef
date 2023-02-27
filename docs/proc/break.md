

 break statement
-----------------




**See also:** 


[continue statement](#/proc/continue) 

[do proc](#/proc/do) 

[for loop proc](#/proc/for/loop) 

[while proc](#/proc/while) 






**See also:** 

**See also:**

[continue statement](#/proc/continue) 

[do proc](#/proc/do) 

[for loop proc](#/proc/for/loop) 

[while proc](#/proc/while) 




[continue statement](#/proc/continue)

[do proc](#/proc/do) 

[for loop proc](#/proc/for/loop) 

[while proc](#/proc/while) 



[do proc](#/proc/do)

[for loop proc](#/proc/for/loop) 

[while proc](#/proc/while) 


[for loop proc](#/proc/for/loop)

[while proc](#/proc/while) 

[while proc](#/proc/while)


**Format:** 


 break
 
 break Label
 



**Format:** 

**Format:**

 break
 
 break Label
 


 break Label


 Terminate the loop with the given label. If no label is specified, the
innermost loop containing the
 `break` 
 statement is assumed.



`break`
### 
 Example:



 obj/zapper
 verb/use()
 var/mob/M

 for(M in view())
 if(!M.key) break

 if(!M) M = usr
 M << "ZAP!"
 del(M)


 The zapper object kills the first mob it finds that doesn't belong to a
player. If none can be found, it kills the user. Be careful! Note how
this code takes advantage of the fact that the loop variable
 
 M
 
 will be
 `null` 
 if the loop terminates normally.




 M

`null`

 For an example of how to use labeled loops, see the reference section for
the
 `continue` 
 statement.



`continue`


---





 for loop proc
---------------




**See also:** 


[break statement](#/proc/break) 

[continue statement](#/proc/continue) 

[do proc](#/proc/do) 

[for list proc](#/proc/for/list) 

[while proc](#/proc/while) 







**See also:** 

**See also:**

[break statement](#/proc/break) 

[continue statement](#/proc/continue) 

[do proc](#/proc/do) 

[for list proc](#/proc/for/list) 

[while proc](#/proc/while) 





[break statement](#/proc/break)

[continue statement](#/proc/continue) 

[do proc](#/proc/do) 

[for list proc](#/proc/for/list) 

[while proc](#/proc/while) 




[continue statement](#/proc/continue)

[do proc](#/proc/do) 

[for list proc](#/proc/for/list) 

[while proc](#/proc/while) 



[do proc](#/proc/do)

[for list proc](#/proc/for/list) 

[while proc](#/proc/while) 


[for list proc](#/proc/for/list)

[while proc](#/proc/while) 

[while proc](#/proc/while)


**Format:** 


 for(Init, Test, Inc) Statement
 


**Format:** 

**Format:**

 for(Init, Test, Inc) Statement


 First execute Init. Then if Test is true (non-zero), execute Statement.
After this execute Inc. Continue checking Test, doing Statement, and
performing Inc until Test turns out to be false (zero).




 Statement may be a code block or a single statement. Semicolons may be
substituted for commas inside the parentheses as a convenience to C/C++
programmers.




 Init and Inc may be omitted. If Test is omitted, the loop will continue
forever (unless a break, goto, or return instruction is used to get out of
the loop).



### 
 Example:



 var/i
for(i=0, i<3, i++)
 world << i


 This outputs:




 0
1
2


 Note: An Inc statement like
 
 i += 0.1
 
 is perfectly valid, but
you should keep in mind that numerical accuracy is not exact. See
 [Numbers](#/{notes}/numbers) 
 for more information.




 i += 0.1

[Numbers](#/{notes}/numbers)


---



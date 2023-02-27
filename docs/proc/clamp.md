

 clamp proc
------------




**See also:** 


[min proc](#/proc/min) 

[max proc](#/proc/max) 




**See also:** 

**See also:**

[min proc](#/proc/min) 

[max proc](#/proc/max) 


[min proc](#/proc/min)

[max proc](#/proc/max) 

[max proc](#/proc/max)


**Format:** 


 clamp(Number, Low, High)
 
 clamp(List, Low, High)
 



**Format:** 

**Format:**

 clamp(Number, Low, High)
 
 clamp(List, Low, High)
 


 clamp(List, Low, High)



**Args:** 


 Number: A number (or null, treated as 0).
 
 List: A list of numbers.
 
 Low: The lowest value that can be returned.
 
 High: The highest value that can be returned.
 





**Args:** 

**Args:**

 Number: A number (or null, treated as 0).
 
 List: A list of numbers.
 
 Low: The lowest value that can be returned.
 
 High: The highest value that can be returned.
 




 List: A list of numbers.
 
 Low: The lowest value that can be returned.
 
 High: The highest value that can be returned.
 



 Low: The lowest value that can be returned.
 
 High: The highest value that can be returned.
 


 High: The highest value that can be returned.



**Returns:** 


 The original Number, constrained between Low and High.
 
 The original List, whose contents have all been clamped.
 



**Returns:** 

**Returns:**

 The original Number, constrained between Low and High.
 
 The original List, whose contents have all been clamped.
 


 The original List, whose contents have all been clamped.


 "Clamps" a number to a given allowable range from
 
 Low
 
 to
 
 High
 
 . If the number is already in that range, it is unchanged.
Otherwise, the closer of
 
 Low
 
 or
 
 High
 
 is returned.




 Low


 High


 Low


 High


 This is effectively equivalent to
 
 min(max(Number, Low), High)
 
 , but
with some slight differences. For one thing,
 
 clamp()
 
 is forgiving if
you accidentally swap
 
 Low
 
 and
 
 High
 
 ; it will just swap them
back so
 
 Low
 
 is always lower. Also, because this is a single proc call
it's slightly faster.




 min(max(Number, Low), High)


 clamp()


 Low


 High


 Low

### 
 Example:



 usr << clamp(5, 0, 10) // 5; it falls between 0 and 10
usr << clamp(-1, 0, 10) // 0; it is less than 0
usr << clamp(20, 0, 10) // 10; it is more than 10


 The list format will accept a list in place of a number as the first
argument, and it behaves as if you looped through the entire list and ran
 
 clamp()
 
 on each number or null value. Please note the original
list will be modified. If you want to leave the original list alone,
use the
 [Copy()
 
 proc](#/list/proc/Copy) 
 to pass a copy to
 
 clamp()
 
 instead.




 clamp()

[Copy()
 
 proc](#/list/proc/Copy)

 Copy()


 clamp()



---



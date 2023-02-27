

 noise\_hash proc
------------------




**See also:** 


[rand proc](#/proc/rand) 

[rand\_seed proc](#/proc/rand_seed) 




**See also:** 

**See also:**

[rand proc](#/proc/rand) 

[rand\_seed proc](#/proc/rand_seed) 


[rand proc](#/proc/rand)

[rand\_seed proc](#/proc/rand_seed) 

[rand\_seed proc](#/proc/rand_seed)


**Format:** 


 noise\_hash(num1, num2, num3...)
 
 noise\_hash(list\_of\_nums)
 
 noise\_hash(hash\_name, num1, num2, num3...)
 
 noise\_hash(hash\_name, list\_of\_nums)
 





**Format:** 

**Format:**

 noise\_hash(num1, num2, num3...)
 
 noise\_hash(list\_of\_nums)
 
 noise\_hash(hash\_name, num1, num2, num3...)
 
 noise\_hash(hash\_name, list\_of\_nums)
 




 noise\_hash(list\_of\_nums)
 
 noise\_hash(hash\_name, num1, num2, num3...)
 
 noise\_hash(hash\_name, list\_of\_nums)
 



 noise\_hash(hash\_name, num1, num2, num3...)
 
 noise\_hash(hash\_name, list\_of\_nums)
 


 noise\_hash(hash\_name, list\_of\_nums)



**Returns:** 


 A number between 0 and 1 (excluding 1 itself)
 


**Returns:** 

**Returns:**

 A number between 0 and 1 (excluding 1 itself)



**Args:** 


 num1, num2, num3...: Numbers to be hashed (at least one)
 
 list\_of\_nums: A list containing the numbers to hash
 
 hash\_name: A text string indicating the hash type (reserved for future use)
 




**Args:** 

**Args:**

 num1, num2, num3...: Numbers to be hashed (at least one)
 
 list\_of\_nums: A list containing the numbers to hash
 
 hash\_name: A text string indicating the hash type (reserved for future use)
 



 list\_of\_nums: A list containing the numbers to hash
 
 hash\_name: A text string indicating the hash type (reserved for future use)
 


 hash\_name: A text string indicating the hash type (reserved for future use)


 For some games using concepts of procedural generation, it's nice to be
able to reliably create pseudo-random numbers in a repeatable, reliable way.
This proc takes all the numbers put into it and hashes them together to get
a value from 0 to 1. That output value will be the same for any given set of
input numbers. This can be used on its own or as part of a more in-depth
noise algorithm.




 If the first argument is a string, that may be used in future versions to
specify the type of hash to use. For now it is not used.




 Non-numbers provided to the proc will be interpreted arbitrarily. Don't do
that.





---





 rand\_seed proc
-----------------




**See also:** 


[pick proc](#/proc/pick) 

[prob proc](#/proc/prob) 

[rand proc](#/proc/rand) 

[roll proc](#/proc/roll) 






**See also:** 

**See also:**

[pick proc](#/proc/pick) 

[prob proc](#/proc/prob) 

[rand proc](#/proc/rand) 

[roll proc](#/proc/roll) 




[pick proc](#/proc/pick)

[prob proc](#/proc/prob) 

[rand proc](#/proc/rand) 

[roll proc](#/proc/roll) 



[prob proc](#/proc/prob)

[rand proc](#/proc/rand) 

[roll proc](#/proc/roll) 


[rand proc](#/proc/rand)

[roll proc](#/proc/roll) 

[roll proc](#/proc/roll)


**Format:** 


 rand\_seed(Seed)
 


**Format:** 

**Format:**

 rand\_seed(Seed)



**Args:** 


 Seed: An integer used to initialize the random number generator.
 


**Args:** 

**Args:**

 Seed: An integer used to initialize the random number generator.


 Many DM procedures make use of a pseudo-random number generator. You can
use rand\_seed() to initialize the generator. The sequence returned by the
generator is identical each time it is initialized with the same seed, so you
could use this to reproduce the same output from an algorithm that uses the
random number generator. If you never call rand\_seed(), the generator is
initialized with a seed from the system clock, so it is effectively random.




 Note that with multiple realtime algorithms making calls to the generator
at unpredictable times, you are likely not to get the same result even when
using the same seed. The overall sequence will be the same, but individual
sub-components of your world might call it in a different order.




 The pseudo-random number generator is system dependent, so do not expect
the sequence generated from a particular seed to be identical on two different
machines or operating systems.





---



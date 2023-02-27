

 Multiply proc (matrix)
------------------------




**See also:** 


[matrix](#/matrix) 

[matrix operators](#/matrix/operators) 

[matrix procs](#/matrix/proc) 

[\*= operator](#/operator/*) 






**See also:** 

**See also:**

[matrix](#/matrix) 

[matrix operators](#/matrix/operators) 

[matrix procs](#/matrix/proc) 

[\*= operator](#/operator/*) 




[matrix](#/matrix)

[matrix operators](#/matrix/operators) 

[matrix procs](#/matrix/proc) 

[\*= operator](#/operator/*) 



[matrix operators](#/matrix/operators)

[matrix procs](#/matrix/proc) 

[\*= operator](#/operator/*) 


[matrix procs](#/matrix/proc)

[\*= operator](#/operator/*) 

[\*= operator](#/operator/*)


**Format:** 


 Multiply(Matrix2)
   

*or* 

 Multiply(n)
 



**Format:** 

**Format:**

 Multiply(Matrix2)
   

*or* 

 Multiply(n)
 

  

*or*

 Multiply(n)



**Args:** 


 Matrix2: another matrix
 
 n: a number
 



**Args:** 

**Args:**

 Matrix2: another matrix
 
 n: a number
 


 n: a number



**Returns:** 


 src
 


**Returns:** 

**Returns:**

 src


 This multiplies the current matrix by Matrix2 or n. If the n format is
used, this is just like scaling the whole matrix. If another matrix is
multiplied, then it is like doing the two transformations in order: src,
then Matrix2.




 Multiplication of one matrix by another depends on the order. You may
get a different result multiplying A \* B vs. B \* A.





---



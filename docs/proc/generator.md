

 generator proc
----------------




**See also:** 


[Generators](#/{notes}/generators) 

[Particle effects](#/{notes}/particles) 

[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 







**See also:** 

**See also:**

[Generators](#/{notes}/generators) 

[Particle effects](#/{notes}/particles) 

[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 





[Generators](#/{notes}/generators)

[Particle effects](#/{notes}/particles) 

[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 




[Particle effects](#/{notes}/particles)

[color var (atom)](#/atom/var/color) 

[Color matrix](#/{notes}/color-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 



[color var (atom)](#/atom/var/color)

[Color matrix](#/{notes}/color-matrix) 

[stddef.dm file](#/{{appendix}}/stddef%2edm) 


[Color matrix](#/{notes}/color-matrix)

[stddef.dm file](#/{{appendix}}/stddef%2edm) 

[stddef.dm file](#/{{appendix}}/stddef%2edm)


**Format:** 


 generator(type, A, B, rand)
 


**Format:** 

**Format:**

 generator(type, A, B, rand)



**Args:** 


 type: The type of generator object, which determines what kind of results it produces
 
 A: One extreme of the generator results
 
 B: The other extreme
 
 rand: Type of random distribution used
 





**Args:** 

**Args:**

 type: The type of generator object, which determines what kind of results it produces
 
 A: One extreme of the generator results
 
 B: The other extreme
 
 rand: Type of random distribution used
 




 A: One extreme of the generator results
 
 B: The other extreme
 
 rand: Type of random distribution used
 



 B: The other extreme
 
 rand: Type of random distribution used
 


 rand: Type of random distribution used


 Creates a generator that can be used to produce a random value. This generator can be used in client-side particle effects, or it can be used in proc code. The types of values it can produce are numbers, 3D vectors (list of 3 numbers), or colors (a text string like "#rrggbb" or a color matrix).





| 
 Generator type
  | 
 Result type
  | 
 Description
  |
| --- | --- | --- |
| 
 num
  | 
 num
  | 
 A random number between A and B.
  |
| 
 vector
  | 
 vector
  | 
 A random vector on a line between A and B.
  |
| 
 box
  | 
 vector
  | 
 A random vector within a box whose corners are at A and B.
  |
| 
 color
  | 
 color (string) or color matrix
  | 
 Result type depends on whether A or B are matrices or not. The result is interpolated between A and B; components are not randomized separately.
  |
| 
 circle
  | 
 vector
  | 
 A random XY-only vector in a ring between radius A and B, centered at 0,0.
  |
| 
 sphere
  | 
 vector
  | 
 A random vector in a spherical shell between radius A and B, centered at 0,0,0.
  |
| 
 square
  | 
 vector
  | 
 A random XY-only vector between squares of sizes A and B. (The length of the square is between A\*2 and B\*2, centered at 0,0.)
  |
| 
 cube
  | 
 vector
  | 
 A random vector between cubes of sizes A and B. (The length of the cube is between A\*2 and B\*2, centered at 0,0,0.)
  |


| 
 Generator type
  | 
 Result type
  | 
 Description
  |

 
 Generator type
 |
 
 Result type
 |
 
 Description
 |
| 
 num
  | 
 num
  | 
 A random number between A and B.
  |

 
 num
 |
 
 num
 |
 
 A random number between A and B.
 |
| 
 vector
  | 
 vector
  | 
 A random vector on a line between A and B.
  |

 
 vector
 |
 
 vector
 |
 
 A random vector on a line between A and B.
 |
| 
 box
  | 
 vector
  | 
 A random vector within a box whose corners are at A and B.
  |

 
 box
 |
 
 vector
 |
 
 A random vector within a box whose corners are at A and B.
 |
| 
 color
  | 
 color (string) or color matrix
  | 
 Result type depends on whether A or B are matrices or not. The result is interpolated between A and B; components are not randomized separately.
  |

 
 color
 |
 
 color (string) or color matrix
 |
 
 Result type depends on whether A or B are matrices or not. The result is interpolated between A and B; components are not randomized separately.
 |
| 
 circle
  | 
 vector
  | 
 A random XY-only vector in a ring between radius A and B, centered at 0,0.
  |

 
 circle
 |
 
 vector
 |
 
 A random XY-only vector in a ring between radius A and B, centered at 0,0.
 |
| 
 sphere
  | 
 vector
  | 
 A random vector in a spherical shell between radius A and B, centered at 0,0,0.
  |

 
 sphere
 |
 
 vector
 |
 
 A random vector in a spherical shell between radius A and B, centered at 0,0,0.
 |
| 
 square
  | 
 vector
  | 
 A random XY-only vector between squares of sizes A and B. (The length of the square is between A\*2 and B\*2, centered at 0,0.)
  |

 
 square
 |
 
 vector
 |
 
 A random XY-only vector between squares of sizes A and B. (The length of the square is between A\*2 and B\*2, centered at 0,0.)
 |
| 
 cube
  | 
 vector
  | 
 A random vector between cubes of sizes A and B. (The length of the cube is between A\*2 and B\*2, centered at 0,0,0.)
  |

 
 cube
 |
 
 vector
 |
 
 A random vector between cubes of sizes A and B. (The length of the cube is between A\*2 and B\*2, centered at 0,0,0.)
 |

 The optional
 
 rand
 
 argument determines the type of random distribution.




 rand



|  |  |
| --- | --- |
| 
 UNIFORM\_RAND
  | 
 Default. Random values are uniformly likely to be chosen.
  |
| 
 NORMAL\_RAND
  | 
 Approximates a Gaussian normal distribution, but on a finite interval. Values closest to the mean are more likely to be chosen, while the extremes are much less likely.
  |
| 
 LINEAR\_RAND
  | 
 The probabiliy of choosing a number is proportional to its absolute value.
  |
| 
 SQUARE\_RAND
  | 
 The probabiliy of choosing a number is proportional to its square.
  |


| 
 UNIFORM\_RAND
  | 
 Default. Random values are uniformly likely to be chosen.
  |

 
 UNIFORM\_RAND
 |
 
 Default. Random values are uniformly likely to be chosen.
 |
| 
 NORMAL\_RAND
  | 
 Approximates a Gaussian normal distribution, but on a finite interval. Values closest to the mean are more likely to be chosen, while the extremes are much less likely.
  |

 
 NORMAL\_RAND
 |
 
 Approximates a Gaussian normal distribution, but on a finite interval. Values closest to the mean are more likely to be chosen, while the extremes are much less likely.
 |
| 
 LINEAR\_RAND
  | 
 The probabiliy of choosing a number is proportional to its absolute value.
  |

 
 LINEAR\_RAND
 |
 
 The probabiliy of choosing a number is proportional to its absolute value.
 |
| 
 SQUARE\_RAND
  | 
 The probabiliy of choosing a number is proportional to its square.
  |

 
 SQUARE\_RAND
 |
 
 The probabiliy of choosing a number is proportional to its square.
 |

 The result of calling
 
 generator()
 
 is a datum of type
 
 /generator
 
 and you can get a random value from it by calling its
 
 Rand()
 
 proc.




 generator()


 /generator


 Rand()

### 
 Example:



 var/generator/G = generator("num", -1, 1) // generates a random number between -1 and 1
world << G.Rand() // generate a number and output it to world



---



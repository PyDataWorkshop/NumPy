

```python

NumPy - Array Attributes


In this chapter, we will discuss the various array attributes of NumPy.
ndarray.shape
This array attribute returns a tuple consisting of array dimensions. It can also be used to resize the array.

#### Example 1
 Live Demo
import numpy as np 
a = np.array([[1,2,3],[4,5,6]]) 
print a.shape
The output is as follows −
(2, 3)
Example 2
 Live Demo
# this resizes the ndarray 
import numpy as np 

a = np.array([[1,2,3],[4,5,6]]) 
a.shape = (3,2) 
print a 
The output is as follows −
[[1, 2] 
 [3, 4] 
 [5, 6]]
Example 3
NumPy also provides a reshape function to resize an array.
 Live Demo
import numpy as np 
a = np.array([[1,2,3],[4,5,6]]) 
b = a.reshape(3,2) 
print b
The output is as follows −
[[1, 2] 
 [3, 4] 
 [5, 6]]
ndarray.ndim
This array attribute returns the number of array dimensions.
Example 1
 Live Demo
# an array of evenly spaced numbers 
import numpy as np 
a = np.arange(24) 
print a
The output is as follows −
[0 1  2  3  4  5  6  7  8  9  10  11  12  13  14  15  16 17 18 19 20 21 22 23] 
Example 2
 Live Demo
# this is one dimensional array 
import numpy as np 
a = np.arange(24) 
a.ndim  

# now reshape it 
b = a.reshape(2,4,3) 
print b 
# b is having three dimensions
The output is as follows −
[[[ 0,  1,  2] 
  [ 3,  4,  5] 
  [ 6,  7,  8] 
  [ 9, 10, 11]]  
  [[12, 13, 14] 
   [15, 16, 17]
   [18, 19, 20] 
   [21, 22, 23]]] 
numpy.itemsize
This array attribute returns the length of each element of array in bytes.

#### Example 1
 Live Demo
# dtype of array is int8 (1 byte) 
import numpy as np 
x = np.array([1,2,3,4,5], dtype = np.int8) 
print x.itemsize
The output is as follows −
1

#### Example 2
 Live Demo
# dtype of array is now float32 (4 bytes) 
import numpy as np 
x = np.array([1,2,3,4,5], dtype = np.float32) 
print x.itemsize
The output is as follows −

4 numpy.flags
The ndarray object has the following attributes. Its current values are returned by this function.
Sr.No.
Attribute & Description
1
C_CONTIGUOUS (C)
The data is in a single, C-style contiguous segment
2
F_CONTIGUOUS (F)
The data is in a single, Fortran-style contiguous segment
3
OWNDATA (O)
The array owns the memory it uses or borrows it from another object
4
WRITEABLE (W)
The data area can be written to. Setting this to False locks the data, making it read-only
5
ALIGNED (A)
The data and all elements are aligned appropriately for the hardware
6
UPDATEIFCOPY (U)
This array is a copy of some other array. When this array is deallocated, the base array will be updated with the contents of this array
Example
The following example shows the current values of flags.
 Live Demo
import numpy as np 
x = np.array([1,2,3,4,5]) 
print x.flags
The output is as follows −
C_CONTIGUOUS : True 
F_CONTIGUOUS : True 
OWNDATA : True 
WRITEABLE : True 
ALIGNED : True 
UPDATEIFCOPY : False



```

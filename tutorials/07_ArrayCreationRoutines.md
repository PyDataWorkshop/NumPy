
NumPy - Array Creation Routines



A new ndarray object can be constructed by any of the following array creation routines or using a low-level ndarray constructor.
numpy.empty
It creates an uninitialized array of specified shape and dtype. It uses the following constructor −
numpy.empty(shape, dtype = float, order = 'C')
The constructor takes the following parameters.
Sr.No.
Parameter & Description
1
Shape
Shape of an empty array in int or tuple of int
2
Dtype
Desired output data type. Optional
3
Order
'C' for C-style row-major array, 'F' for FORTRAN style column-major array
Example
The following code shows an example of an empty array.
 Live Demo
import numpy as np 
x = np.empty([3,2], dtype = int) 
print x
The output is as follows −
[[22649312    1701344351] 
 [1818321759  1885959276] 
 [16779776    156368896]]
Note − The elements in an array show random values as they are not initialized.
numpy.zeros
Returns a new array of specified size, filled with zeros.
numpy.zeros(shape, dtype = float, order = 'C')
The constructor takes the following parameters.
Sr.No.
Parameter & Description
1
Shape
Shape of an empty array in int or sequence of int
2
Dtype
Desired output data type. Optional
3
Order
'C' for C-style row-major array, 'F' for FORTRAN style column-major array
Example 1
 Live Demo
# array of five zeros. Default dtype is float 
import numpy as np 
x = np.zeros(5) 
print x
The output is as follows −
[ 0.  0.  0.  0.  0.]
Example 2
 Live Demo
import numpy as np 
x = np.zeros((5,), dtype = np.int) 
print x
Now, the output would be as follows −
[0  0  0  0  0]
Example 3
 Live Demo
# custom type 
import numpy as np 
x = np.zeros((2,2), dtype = [('x', 'i4'), ('y', 'i4')])  
print x
It should produce the following output −
[[(0,0)(0,0)]
 [(0,0)(0,0)]]         
numpy.ones
Returns a new array of specified size and type, filled with ones.
numpy.ones(shape, dtype = None, order = 'C')
The constructor takes the following parameters.
Sr.No.
Parameter & Description
1
Shape
Shape of an empty array in int or tuple of int
2
Dtype
Desired output data type. Optional
3
Order
'C' for C-style row-major array, 'F' for FORTRAN style column-major array
Example 1
 Live Demo
# array of five ones. Default dtype is float 
import numpy as np 
x = np.ones(5) 
print x
The output is as follows −
[ 1.  1.  1.  1.  1.]
Example 2
 Live Demo
import numpy as np 
x = np.ones([2,2], dtype = int) 
print x
Now, the output would be as follows −
[[1  1] 
 [1  1]]


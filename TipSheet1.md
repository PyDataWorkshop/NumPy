Constructing arrays

scipy.array(alist): construct an n-dimensional array from a Python list (all elements of list must be of same length)
a = scipy.array([[1,2,3],[4,5,6]])
b = scipy.array([i*i for i in range(100) if i%2==1])
c = b.tolist()                            # convert array back to Python list
scipy.zeros(shape, dtype=float): construct an n-dimensional array of the specified shape, filled with zeros of the specified dtype; e.g.,
a = scipy.zeros(100)                      # a 100-element array of float zeros
b = scipy.zeros((2,8), int)               # a 2x8 array of int zeros
c = scipy.zeros((N,M,L), complex)         # a NxMxL array of complex zeros
scipy.ones(shape, dtype=float): construct an n-dimensional array of the specified shape, filled with ones of the specified dtype; e.g.,
a = scipy.ones(10, int)                   # a 10-element array of int ones
b = scipy.pi * scipy.ones((5,5))          # a useful way to fill up an array with a specified value
scipy.eye(shape, dtype=float)
id = scipy.eye(10,10, int)                           # 10x10 identity matrix (1's on diagonal)
offdiag = scipy.eye(10,10,1)+scipy.eye(10,10,-1)     # off diagonal elements = 1
scipy.transpose(a)
b = scipy.transpose(a)                    # reverse dimensions of a (even for dim > 2)
b = a.T                                   # equivalent to scipy.transpose(a)
c = scipy.swapaxes(a, axis1, axis2)       # swap specified axes
scipy.arange and scipy.linspace
a = scipy.arange(start, stop, increment)      # like Python range, but with (potentially) real-valued arrays
b = scipy.linspace(start, stop, num_elements) # create array of equally-spaced points based on specifed number of points
Random array constructors in scipy.random
a = scipy.random.random((100,100))        # 100x100 array of floats uniform on [0.,1.)
b = scipy.random.randint(0,10, (100,))    # 100 random ints uniform on [0, 10), i.e., not including the upper bound 10
c = scipy.random.standard_normal((5,5,5)) # zero-mean, unit-variance Gaussian random numbers in a 5x5x5 array
Indexing arrays

Multidimensional indexing
elem = a[i,j,k]       # equiv. to a[i][j][k] but presumably more efficient
"Negative" indexing (wrap around the end of the array)
last_elem = a[-1]     # the last element of the array
Arrays as indices
i = scipy.array([0,1,2,1])                     # array of indices for the first axis
j = scipy.array([1,2,3,4])                     # array of indices for the second axis
a[i,j]                                         # return array([a[0,1], a[1,2], a[2,3], a[1,4]])
b = scipy.array([True, False, True, False])
a[b]                                           # return array([a[0], a[2]]) since only b[0] and b[2] are True

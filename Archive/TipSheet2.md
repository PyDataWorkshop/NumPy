### Slicing arrays (extracting subsections)

Slice a defined subblock:
section = a[10:20, 30:40]         # 10x10 subblock starting at [10,30]
Grab everything up to the beginning/end of the array:
asection = a[10:, 30:]            # missing stop index implies until end of array
bsection = b[:10, :30]            # missing start index implies until start of array
Grab an entire column(s)
x = a[:, 0]                       # get everything in the 0th column (missing start and stop)
y = a[:, 1]                       # get everything in the 1st column
Slice off the tail end of an array
tail = a[-10:]                    # grab the last 10 elements of the array
slab = b[:, -10:]                 # grab a slab of width 10 off the "side" of the array
interior = c[1:-1, 1:-1, 1:-1]    # slice out everything but the outer shell
Element-wise functions on arrays

<hr>
### Arithmetic operations

c = a + b      # add a and b element-wise (must be same shape)
d = e * f      # multiply e and f element-wise (NOT matrix multiplication)
g = -h         # negate every element of h
y = (x+1)%2    # swap 0's and 1's in binary array x
z = w > 0.0    # return boolean array indicating which elements are > 0.0
logspace = 10.**scipy.linspace(-6.0, -1.0, 50)   # 50 equally-spaced-in-log points between 1.e-06 and 1.0e-01
Trigonometric operations
y = scipy.sin(x)                                    # sin of every element of x
w = scipy.sin([i*i for i in range(100) if i%2==1])  # conversion from list to array as part of function application
z = scipy.exp((0.+1.j) * theta)                     # exp(i * theta) where i = sqrt(-1) = 0.+1.j

<hr>
### Summation of arrays

Simple sums
s  = scipy.sum(a)             # sum all elements in a, returning a scalar
s0 = scipy.sum(a, axis=0)     # sum elements along specified axis (=0), returning an array of remaining shape, e.g.,
a  = scipy.ones((10,20,30))
s0 = scipy.sum(a, axis=0)     # s0 has shape (20,30)
Averaging, etc.
m = scipy.mean(a, axis)       # compute mean along the specified axis (over entire array if axis=None)
s = scipy.std(a, axis)        # compute standard deviation along the specified axis (over entire array if axis=None)
Cumulative sums
s0 = scipy.cumsum(a, axis=0)  # cumulatively sum over 0 axis, returning array with same shape as a
s0 = scipy.cumsum(a)          # cumulatively sum over 0 axis, returning 1D array of length shape[0]*shape[1]*...*shape[dim-1]

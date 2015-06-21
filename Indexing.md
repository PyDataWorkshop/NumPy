#### Indexing: Comparing Matrices and 2D Arrays
Note that there are some important differences between NumPy arrays and matrices. 
 - NumPy provides two fundamental objects: an N-dimensional array object and a universal function object. 
 - Other objects are built on top of these. In particular, matrices are 2-dimensional array objects that inherit from the NumPy array object. 
 - For both arrays and matrices, indices must consist of a proper combination of one or more of the following: integer scalars, ellipses, a list of integers or boolean values, a tuple of integers or boolean values, and a 1-dimensional array of integer or boolean values. 
 - A matrix can be used as an index for matrices, but commonly an array, list, or other form is needed to accomplish a given task.
<hr>
As usual in Python, indexing is zero-based. Traditionally we represent a 2D array or matrix as a rectangular array of rows and columns, where movement along axis 0 is movement across rows, while movement along axis 1 is movement across columns.
Let's make an array and matrix to slice:

<pre><code>
>>> A = arange(12)
>>> A
array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])
>>> A.shape = (3,4)
>>> M = mat(A.copy())
>>> print type(A),"  ",type(M)
<type 'numpy.ndarray'>    <class 'numpy.core.defmatrix.matrix'>
>>>
>>> print A
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
>>>
>>> print M
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
</code></pre>

<hr>
Now, let's take some simple slices. Basic slicing uses slice objects or integers. For example, the evaluation of A[:] and M[:] will appear familiar from Python indexing, however it is important to note that slicing NumPy arrays does *not* make a copy of the data; slicing provides a new view of the same data.

<pre><code>
>>> print A[:]; print A[:].shape
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
(3, 4)
>>>
>>> print M[:]; print M[:].shape
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
(3, 4)
</code></pre>

Now for something that differs from Python indexing: you may use comma-separated indices to index along multiple axes at the same time.

<pre><code>
>>> print A[:,1]; print A[:,1].shape
[1 5 9]
(3,)
>>> print M[:,1]; print M[:,1].shape
[[1]
 [5]
 [9]]
(3, 1)
</code></pre>

Notice the difference in the last two results. Use of a single colon for the 2D array produces a 1-dimensional array, while for a matrix it produces a 2-dimensional matrix. 
A slice of a matrix will always produce a matrix. For example, a slice M[2,:] produces a matrix of shape (1,4). In contrast, a slice of an array will always produce an array of the lowest possible dimension. For example, if C were a 3-dimensional array, C[...,1] produces a 2D array while C[1,:,1] produces a 1-dimensional array. From this point on, we will show results only for the array slice if the results for the corresponding matrix slice are identical.

Lets say that we wanted the 1st and 3rd column of an array. One way is to slice using a list:
<pre><code>
>>> A[:,[1,3]]
array([[ 1,  3],
       [ 5,  7],
       [ 9, 11]])
</code></pre>
A slightly more complicated way is to use the take() method:
<pre><code>
>>> A[:,].take([1,3],axis=1)
array([[ 1,  3],
       [ 5,  7],
       [ 9, 11]])
<code><pre>       
If we wanted to skip the first row, we could use:
>>> A[1:,].take([1,3],axis=1)
array([[ 5,  7],
       [ 9, 11]])
Or we could simply use A[1:,[1,3]]. Yet another way to slice the above is to use a cross product:
>>> A[ix_((1,2),(1,3))]
array([[ 5,  7],
       [ 9, 11]])
For the reader's convenience, here is our array again:
<pre><code>
>>> print A
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
</code></pre>
<hr>
Now let's do something a bit more complicated. Lets say that we want to retain all columns where the first row is greater than 1. One way is to create a boolean index:
<pre><code>
>>> A[0,:]>1
array([False, False, True, True], dtype=bool)
>>> A[:,A[0,:]>1]
array([[ 2,  3],
       [ 6,  7],
       [10, 11]])
</code></pre>
Indexing the matrix is not so convenient.
<pre><code>
>>> M[0,:]>1
matrix([[False, False, True, True]], dtype=bool)
>>> M[:,M[0,:]>1]
matrix([[2, 3]])
</code></pre>
The problem of course is that slicing the matrix slice produced a matrix. But matrices have a convenient 'A' attribute whose value is the array representation, so we can just do this instead:
>>> M[:,M.A[0,:]>1]
matrix([[ 2,  3],
        [ 6,  7],
        [10, 11]])
</code></pre>
If we wanted to conditionally slice the matrix in two directions, we must adjust our strategy slightly. Instead of
>>> A[A[:,0]>2,A[0,:]>1]
array([ 6, 11])
>>> M[M.A[:,0]>2,M.A[0,:]>1]
matrix([[ 6, 11]])
</code></pre>
we need to use the cross product `ix_`
<pre><code>
>>> A[numpy.ix_(A[:,0]>2,A[0,:]>1)]
array([[ 6,  7],
       [10, 11]])
>>> M[numpy.ix_(M.A[:,0]>2,M.A[0,:]>1)]
matrix([[ 6,  7],
        [10, 11]])
</code></pre>
#### Tricks and Tips
Here we give a list of short and useful tips.

<hr?>
#### "Automatic" Reshaping
To change the dimensions of an array, you can omit one of the sizes which will then be deduced automatically:
<pre></code>
>>> a = arange(30)
>>> a.shape = 2,-1,3  # -1 means "whatever is needed"
>>> a.shape
(2, 5, 3)
>>> a
array([[[ 0,  1,  2],
        [ 3,  4,  5],
        [ 6,  7,  8],
        [ 9, 10, 11],
        [12, 13, 14]],
       [[15, 16, 17],
        [18, 19, 20],
        [21, 22, 23],
        [24, 25, 26],
        [27, 28, 29]]])
</code></pre>


#### `cumprod` functions
<pre><code>
>>> from numpy import *
>>> a = array([1,2,3])
>>> a.cumprod() # total product 1*2*3 = 6, and intermediate results 1, 1*2
array([1, 2, 6])
>>> cumprod(a) # also exists
array([1, 2, 6])
>>> a = array([[1,2,3],[4,5,6]])
>>> a.cumprod(dtype=float) # specify type of output
array([1., 2., 6., 24., 120., 720.])
>>> a.cumprod(axis=0) # for each of the 3 columns: product and intermediate results
array([[ 1, 2, 3],
       [ 4, 10, 18]])
>>> a.cumprod(axis=1) # for each of the two rows: product and intermediate results
array([[ 1, 2, 6],
       [ 4, 20, 120]])
</code></pre>       

#### `cumsum` function
<pre><code>
>>> from numpy import *
>>> a = array([1,2,3]) # cumulative sum = intermediate summing results & total sum
>>> a.cumsum()
array([1, 3, 6])
>>> cumsum(a) # also exists
array([1, 3, 6])
>>> a = array([[1,2,3],[4,5,6]])
>>> a.cumsum(dtype=float) # specifies type of output value(s)
array([ 1., 3., 6., 10., 15., 21.])
>>> a.cumsum(axis=0) # sum over rows for each of the 3 columns
array([[1, 2, 3],
       [5, 7, 9]])
>>> a.cumsum(axis=1) # sum over columns for each of the 2 rows
array([[ 1, 3, 6],
       [ 4, 9, 15]])

</code></pre>

#### `diff`` function
<pre><code>
>>> from numpy import *
>>> x = array([0,1,3,9,5,10])
>>> diff(x) # 1st-order differences between the elements of x
array([ 1, 2, 6, -4, 5])
>>> diff(x,n=2) # 2nd-order differences, equivalent to diff(diff(x))
array([ 1, 4, -10, 9])
>>> x = array([[1,3,6,10],[0,5,6,8]])
>>> diff(x) # 1st-order differences between the columns (default: axis=-1)
array([[2, 3, 4],
       [5, 1, 2]])
>>> diff(x,axis=0) # 1st-order difference between the rows
array([[-1, 2, 0, -2]])
</code></pre>


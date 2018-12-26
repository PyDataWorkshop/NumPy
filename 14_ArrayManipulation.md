
NumPy - Array Manipulation
================================================


Several routines are available in NumPy package for manipulation of elements in ndarray object. They can be classified into the following types −


#### Changing Shape


||Shape | Description|
|--|---|----|
|1 |  reshape | Gives a new shape to an array without changing its data|
|2 |  flat |  A 1-D iterator over the array|
|3 | flatten |  Returns a copy of the array collapsed into one dimension|
|4 |  ravel |  Returns a contiguous flattened array|

### Transpose Operations


| | Operation | Description|
|--|--|--|
|1|transpose | Permutes the dimensions of an array |
|2|ndarray.T | Same as self.transpose() |
|3|rollaxis | Rolls the specified axis backwards |
|4|swapaxes | Interchanges the two axes of an array| 

### Changing Dimensions

| | Array | Description|
|--|--|--|
| 1 | broadcast | Produces an object that mimics broadcasting |
| 2 | broadcast_to | Broadcasts an array to a new shape |
| 3 | expand_dims | Expands the shape of an array |
| 4 | squeeze | Removes single-dimensional entries from the shape of an array |

###  Joining Arrays



| | Array | Description|
|--|--|--|
| 1 | concatenate | Joins a sequence of arrays along an existing axis |
| 2 | stack  | Joins a sequence of arrays along a new axis |
| 3 | hstack | Stacks arrays in sequence horizontally (column wise) |
| 4 | vstack | Stacks arrays in sequence vertically (row wise) |


### Splitting Arrays


| | Array | Description|
|--|--|--|
|1 |split   |Splits an array into multiple sub-arrays|
|2 |hsplit  |Splits an array into multiple sub-arrays horizontally (column-wise)|
|3 |vsplit  |Splits an array into multiple sub-arrays vertically (row-wise)|




```python
Adding / Removing Elements
Sr.No.

Element & Description
1 resize  Returns a new array with the specified shape
2 append  Appends the values to the end of an array
3 insert Inserts the values along the given axis before the given indices
4 delete Returns a new array with sub-arrays along an axis deleted
5 unique Finds the unique elements of an array


```


      File "<ipython-input-1-49fbd3ea9e89>", line 1
        Adding / Removing Elements
                                 ^
    SyntaxError: invalid syntax



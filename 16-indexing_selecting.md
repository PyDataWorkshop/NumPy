
Python Pandas - Indexing and Selecting Data
==================================================


In this chapter, we will discuss how to slice and dice the date and generally get the subset of pandas object.
The Python and NumPy indexing operators "[ ]" and attribute operator "." provide quick and easy access to Pandas data structures across a wide range of use cases. However, since the type of the data to be accessed isn’t known in advance, directly using standard operators has some optimization limits. For production code, we recommend that you take advantage of the optimized pandas data access methods explained in this chapter.
Pandas now supports three types of Multi-axes indexing; the three types are mentioned in the following table −



#### Indexing
* ``.loc()``: Label based
* ``.iloc()``: Integer based
* ``.ix()``: Both Label and Integer based

### ``.loc()``

Pandas provide various methods to have purely label based indexing. When slicing, the start bound is also included. Integers are valid labels, but they refer to the label and not the position.
``.loc()`` has multiple access methods like −
* A single scalar label
* A list of labels
*  A slice object
* A Boolean array
l
oc takes two single/list/range operator separated by ','. The first one indicates the row and the second one indicates columns.

#### Example 1


```python
#import the pandas library and aliasing as pd

import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4),
index = ['a','b','c','d','e','f','g','h'], columns = ['A', 'B', 'C', 'D'])

#select all rows for a specific column
print(df.loc[:,'A'])
```

    a    1.551026
    b    0.281038
    c    0.116974
    d    0.109972
    e    0.502636
    f   -0.894577
    g   -1.841751
    h   -1.166839
    Name: A, dtype: float64


#### Example 2


```python
# import the pandas library and aliasing as pd
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4),
index = ['a','b','c','d','e','f','g','h'], columns = ['A', 'B', 'C', 'D'])

```


```python



# Select all rows for multiple columns, say list[]
print(df.loc[:,['A','C']])

```

              A         C
    a  0.924991 -1.687593
    b  0.716964  1.403685
    c -0.258965  0.683530
    d -0.537149  0.513119
    e  1.051740 -1.936683
    f  0.251938  1.820420
    g -0.000178 -0.588688
    h  0.387250 -0.699250


#### Example 3


```python

# import the pandas library and aliasing as pd
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4),
index = ['a','b','c','d','e','f','g','h'], columns = ['A', 'B', 'C', 'D'])

# Select few rows for multiple columns, say list[]
print(df.loc[['a','b','f','h'],['A','C']])
```

              A         C
    a  0.263231  1.577000
    b  1.307732  1.490180
    f  0.040466 -1.096467
    h  1.843551 -0.937235


#### Example 4



```python
# import the pandas library and aliasing as pd
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4),
index = ['a','b','c','d','e','f','g','h'], columns = ['A', 'B', 'C', 'D'])

# Select range of rows for all columns
print(df.loc['a':'h'])
```

              A         B         C         D
    a  0.039688  0.992148  0.810180  0.408712
    b -0.733156  0.137439  0.327461  0.020296
    c  0.301710 -0.043887  1.072658 -1.875967
    d  0.129714  1.775020  0.635591  0.834983
    e -0.956590 -1.923039 -0.255347 -1.868094
    f -0.548138 -0.276310 -0.391201 -0.430545
    g -0.841305 -1.301838  2.073024 -0.305999
    h  0.873295  1.176141 -0.233416  1.871664


#### Example 5


```python


# import the pandas library and aliasing as pd
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4),
index = ['a','b','c','d','e','f','g','h'], columns = ['A', 'B', 'C', 'D'])

# for getting values with a boolean array
print df.loc['a']>0
Its output is as follows −
A  False
B  True
C  False
D  False
Name: a, dtype: bool


```


```python
.iloc()
Pandas provide various methods in order to get purely integer based indexing. Like python and numpy, these are 0-based indexing.
The various access methods are as follows −
An Integer
A list of integers
A range of values
```

#### Example 1


```python

# import the pandas library and aliasing as pd
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])

# select all rows for a specific column
print df.iloc[:4]
Its output is as follows −
           A          B           C           D
0   0.699435   0.256239   -1.270702   -0.645195
1  -0.685354   0.890791   -0.813012    0.631615
2  -0.783192  -0.531378    0.025070    0.230806
3   0.539042  -1.284314    0.826977   -0.026251
```


```python
Example 2
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])

# Integer slicing
print df.iloc[:4]
print df.iloc[1:5, 2:4]
Its output is as follows −
           A          B           C           D
0   0.699435   0.256239   -1.270702   -0.645195
1  -0.685354   0.890791   -0.813012    0.631615
2  -0.783192  -0.531378    0.025070    0.230806
3   0.539042  -1.284314    0.826977   -0.026251

           C          D
1  -0.813012   0.631615
2   0.025070   0.230806
3   0.826977  -0.026251
4   1.423332   1.130568
```

#### Example 3


```python



import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])

# Slicing through list of values
print( df.iloc[[1, 3, 5], [1, 3]])
print( df.iloc[1:3, :])

```

              B         D
    1  0.292027 -1.508219
    3 -0.254849 -0.904246
    5  0.818295  2.591965
              A         B        C         D
    1  0.683640  0.292027  0.65577 -1.508219
    2  0.473568  0.897978  0.39003  0.544072
              B         C
    0 -0.128454 -0.280424
    1  0.292027  0.655770
    2  0.897978  0.390030
    3 -0.254849 -0.286877
    4  1.053455  0.520787
    5  0.818295  0.610940
    6 -0.409100 -0.211414
    7  0.296536  0.450408



```python
print( df.iloc[:,1:3])

```

              B         C
    0 -0.128454 -0.280424
    1  0.292027  0.655770
    2  0.897978  0.390030
    3 -0.254849 -0.286877
    4  1.053455  0.520787
    5  0.818295  0.610940
    6 -0.409100 -0.211414
    7  0.296536  0.450408



```python
.ix()
Besides pure label based and integer based, Pandas provides a hybrid method for selections and subsetting the object using the .ix() operator.
Example 1
```


```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])

# Integer slicing
print(df.ix[:4])
```

#### Example 2


```python

import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])
# Index slicing
print df.ix[:,'A']
Its output is as follows −
0   0.699435
1  -0.685354
2  -0.783192
3   0.539042
4  -1.044209
5  -1.415411
6   1.062095
7   0.994204
Name: A, dtype: float64
```


```python

Use of Notations
Getting values from the Pandas object with Multi-axes indexing uses the following notation −
Object
Indexers
Return Type
Series
s.loc[indexer]
Scalar value
DataFrame
df.loc[row_index,col_index]
Series object
Panel
p.loc[item_index,major_index, minor_index]
p.loc[item_index,major_index, minor_index]
Note − .iloc() & .ix() applies the same indexing options and Return value.
Let us now see how each operation can be performed on the DataFrame object. We will use the basic indexing operator '[ ]' −

```


```python
Example 1
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])
print df['A']
Its output is as follows −
0  -0.478893
1   0.391931
2   0.336825
3  -1.055102
4  -0.165218
5  -0.328641
6   0.567721
7  -0.759399
Name: A, dtype: float64
Note − We can pass a list of values to [ ] to select those columns.
```


```python
Example 2
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])

print df[['A','B']]
Its output is as follows −
           A           B
0  -0.478893   -0.606311
1   0.391931   -0.949025
2   0.336825    0.093717
3  -1.055102   -0.012944
4  -0.165218    1.550310
5  -0.328641   -0.226363
6   0.567721   -0.312585
7  -0.759399   -0.372696
```


```python



Example 3
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])
print df[2:2]
Its output is as follows −
Columns: [A, B, C, D]
Index: []
Attribute Access
Columns can be selected using the attribute operator '.'.


```

#### Example


```python

import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(8, 4), columns = ['A', 'B', 'C', 'D'])

print(df.A)

```

    0    0.408685
    1   -0.087811
    2   -0.275869
    3   -1.006965
    4    0.004095
    5   -0.487216
    6   -0.297863
    7    0.153044
    Name: A, dtype: float64


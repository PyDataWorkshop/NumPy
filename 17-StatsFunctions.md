

```python
Python Pandas - Statistical Functions



Statistical methods help in the understanding and analyzing the behavior of data. We will now learn a few statistical functions, which we can apply on Pandas objects.

#### Percent_change
Series, DatFrames and Panel, all have the function ``pct_change()``. This function compares every element with 
its prior element and computes the change percentage.


```


```python




import pandas as pd
import numpy as np
s = pd.Series([1,2,3,4,5,4])
print(s.pct_change())


```

    0         NaN
    1    1.000000
    2    0.500000
    3    0.333333
    4    0.250000
    5   -0.200000
    dtype: float64



```python
df = pd.DataFrame(np.random.randn(5, 2))
print(df.pct_change())
```

               0          1
    0        NaN        NaN
    1  -0.983019  -1.415582
    2 -67.747426  -1.009710
    3  -1.678494 -99.139727
    4   0.204784  -1.350842



By default, the pct_change() operates on columns; if you want to apply the same row wise, then use axis=1() argument.

#### Covariance
Covariance is applied on series data. The Series object has a method cov to compute covariance between series objects. NA will be excluded automatically.
Cov Series


```python

import pandas as pd
import numpy as np
s1 = pd.Series(np.random.randn(10))
s2 = pd.Series(np.random.randn(10))
print(s1.cov(s2))

```

    -0.28324403932323955


Covariance method when applied on a DataFrame, computes cov between all the columns.



```python
import pandas as pd
import numpy as np
frame = pd.DataFrame(np.random.randn(10, 5), columns=['a', 'b', 'c', 'd', 'e'])
print frame['a'].cov(frame['b'])


```


```python
print frame.cov()
```


```python

Its output is as follows −
-0.58312921152741437

           a           b           c           d            e
a   1.780628   -0.583129   -0.185575    0.003679    -0.136558
b  -0.583129    1.297011    0.136530   -0.523719     0.251064
c  -0.185575    0.136530    0.915227   -0.053881    -0.058926
d   0.003679   -0.523719   -0.053881    1.521426    -0.487694
e  -0.136558    0.251064   -0.058926   -0.487694     0.960761
Note − Observe the cov between a and b column in the first statement and the same is the value returned by cov on DataFrame.

```

#### Correlation
Correlation shows the linear relationship between any two array of values (series). There are multiple methods to compute the correlation like pearson(default), spearman and kendall.



```python

import pandas as pd
import numpy as np
frame = pd.DataFrame(np.random.randn(10, 5), columns=['a', 'b', 'c', 'd', 'e'])

print frame['a'].corr(frame['b'])

print frame.corr()
</code></pre>
```


If any non-numeric column is present in the DataFrame, it is excluded automatically.
Data Ranking
Data Ranking produces ranking for each element in the array of elements. In case of ties, assigns the mean rank.


```python

import pandas as pd
import numpy as np
s = pd.Series(np.random.np.random.randn(5), index=list('abcde'))

s['d'] = s['b'] # so there's a tie

print s.rank()
```


```python

Its output is as follows −
a  1.0
b  3.5
c  2.0
d  3.5
e  5.0
dtype: float64


```

Rank optionally takes a parameter ascending which by default is true; when false, data is reverse-ranked, with larger values assigned a smaller rank.
Rank supports different tie-breaking methods, specified with the method parameter −
average − average rank of tied group
min − lowest rank in the group
max − highest rank in the group
first − ranks assigned in the order they appear in the array



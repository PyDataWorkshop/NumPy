
Python Pandas - Window Functions
================================

For working on numerical data, Pandas provide few variants like rolling, expanding and exponentially moving weights for window statistics. Among these are sum, mean, median, variance, covariance, correlation, etc.
We will now learn how each of these can be applied on DataFrame objects.

## ``.rolling()`` Function
This function can be applied on a series of data. Specify the ``window=n`` argument and apply the appropriate statistical function on top of it.



```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(10, 4),
index = pd.date_range('1/1/2000', periods=10),
columns = ['A', 'B', 'C', 'D'])

print(df.rolling(window=3).mean())
```

                       A         B         C         D
    2000-01-01       NaN       NaN       NaN       NaN
    2000-01-02       NaN       NaN       NaN       NaN
    2000-01-03 -0.835984  0.653793  0.421525 -0.449814
    2000-01-04 -0.808987  1.091138 -0.274936 -0.241400
    2000-01-05 -1.362102 -0.278756 -0.026007 -0.115439
    2000-01-06 -0.855376 -0.120782 -0.297392  0.562546
    2000-01-07 -0.321334 -0.269166 -0.273217  0.624160
    2000-01-08  0.419682 -0.112354  0.020031  0.618951
    2000-01-09  0.813700 -0.476130  0.043974  0.505536
    2000-01-10  0.236943 -0.562603 -0.167739  0.652211



```python

Note − Since the window size is 3, for first two elements there are nulls and from third the value will be the average of the n, n-1 and n-2 elements. Thus we can also apply various functions as mentioned above.

### ``.expanding()`` Function
This function can be applied on a series of data. Specify the ``min_periods=n`` argument and apply the appropriate statistical function on top of it.

```


```python

import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(10, 4),
      index = pd.date_range('1/1/2000', periods=10),
      columns = ['A', 'B', 'C', 'D'])
print(df.expanding(min_periods=3).mean())
```

                       A         B         C         D
    2000-01-01       NaN       NaN       NaN       NaN
    2000-01-02       NaN       NaN       NaN       NaN
    2000-01-03  1.377366 -0.261913  0.748050 -0.629585
    2000-01-04  0.671504 -0.198749  0.678917 -0.120680
    2000-01-05  0.542723 -0.150288  0.901705 -0.176641
    2000-01-06  0.575561 -0.449954  0.853816 -0.025822
    2000-01-07  0.277210 -0.354598  0.668450  0.091431
    2000-01-08  0.294540 -0.315285  0.628950  0.114517
    2000-01-09  0.274787 -0.115794  0.633288  0.027935
    2000-01-10  0.175606 -0.096365  0.663282  0.067387



### ``.ewm()`` Function
``ewm ``is applied on a series of data. Specify any of the com, span, halflife argument and apply the appropriate statistical 
function on top of it. It assigns the weights exponentially.



```python
import pandas as pd
import numpy as np
 
df = pd.DataFrame(np.random.randn(10, 4),
   index = pd.date_range('1/1/2000', periods=10),
   columns = ['A', 'B', 'C', 'D'])
print(df.ewm(com=0.5).mean())


```

                       A         B         C         D
    2000-01-01  2.080223  0.197858 -1.098332  1.392633
    2000-01-02  0.462096 -0.213338 -1.787626  0.667741
    2000-01-03  0.505875  1.986343  0.062038  0.568433
    2000-01-04 -1.026548  0.839727  0.294930 -0.217225
    2000-01-05  0.214398  0.756409 -0.642794 -0.116982
    2000-01-06 -0.431547 -0.865646  0.272495 -0.909195
    2000-01-07  0.543948  0.074216  0.315750 -0.619783
    2000-01-08  0.453162  0.172752 -0.709768 -0.251372
    2000-01-09  0.524983 -0.883013 -0.186313 -0.512235
    2000-01-10  0.027156  0.247839 -0.747707 -0.319966


Window functions are majorly used in finding the trends within the data graphically by smoothing the curve. If there is lot of variation in the everyday data and a lot of data points are available, then taking the samples and plotting is one method and applying the window computations and plotting the graph on the results is another method. By these methods, we can smooth the curve or the trend.



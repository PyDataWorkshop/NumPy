Vector Stacking
================
How do we construct a 2D array from a list of equally-sized row vectors? In MATLAB this is quite easy: if x and y are two vectors of the same length you only need do m=[x;y]. In NumPy this works via the functions column_stack, dstack, hstack and vstack, depending on the dimension in which the stacking is to be done. For example:
<pre><code>
x = arange(0,10,2)                     # x=([0,2,4,6,8])
y = arange(5)                          # y=([0,1,2,3,4])
m = vstack([x,y])                      # m=([[0,2,4,6,8],
                                       #     [0,1,2,3,4]])
xy = hstack([x,y])                     # xy =([0,2,4,6,8,0,1,2,3,4])
</code></pre>
The logic behind those functions in more than two dimensions can be strange.
<hr>

### Histograms
The NumPy histogram function applied to an array returns a pair of vectors: the histogram of the array and the vector of bins. Beware: matplotlib also has a function to build histograms (called hist, as in Matlab) that differs from the one in NumPy. The main difference is that pylab.hist plots the histogram automatically, while numpy.histogram only generates the data.
<pre><code>
import numpy
import pylab
# Build a vector of 10000 normal deviates with variance 0.5^2 and mean 2
mu, sigma = 2, 0.5
v = numpy.random.normal(mu,sigma,10000)
# Plot a normalized histogram with 50 bins
pylab.hist(v, bins=50, normed=1)       # matplotlib version (plot)
pylab.show()
# Compute the histogram with numpy and then plot it
(n, bins) = numpy.histogram(v, bins=50, normed=True)  # NumPy version (no plot)
pylab.plot(.5*(bins[1:]+bins[:-1]), n)
pylab.show()
</code></pre>

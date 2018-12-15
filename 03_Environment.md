

```python

NumPy - Environment




Standard Python distribution doesn't come bundled with NumPy module. A lightweight alternative is to install NumPy using popular Python package installer, pip.
pip install numpy
The best way to enable NumPy is to use an installable binary package specific to your operating system. These binaries contain full SciPy stack (inclusive of NumPy, SciPy, matplotlib, IPython, SymPy and nose packages along with core Python).


```


```python
Windows
Anaconda (from https://www.continuum.io) is a free Python distribution for SciPy stack. It is also available for Linux and Mac.
Canopy (https://www.enthought.com/products/canopy/) is available as free as well as commercial distribution with full SciPy stack for Windows, Linux and Mac.
Python (x,y): It is a free Python distribution with SciPy stack and Spyder IDE for Windows OS. (Downloadable from https://www.python-xy.github.io/)


```


```python
Linux
Package managers of respective Linux distributions are used to install one or more packages in SciPy stack.
```


```python
For Ubuntu
sudo apt-get install python-numpy 
python-scipy python-matplotlibipythonipythonnotebook python-pandas 
python-sympy python-nose

```


```python
For Fedora
sudo yum install numpyscipy python-matplotlibipython 
python-pandas sympy python-nose atlas-devel
Building from Source
Core Python (2.6.x, 2.7.x and 3.2.x onwards) must be installed with distutils and zlib module should be enabled.
GNU gcc (4.2 and above) C compiler must be available.
To install NumPy, run the following command.
Python setup.py install
To test whether NumPy module is properly installed, try to import it from Python prompt.
import numpy
If it is not installed, the following error message will be displayed.
Traceback (most recent call last): 
   File "<pyshell#0>", line 1, in <module> 
      import numpy 
ImportError: No module named 'numpy'
Alternatively, NumPy package is imported using the following syntax −
import numpy as np


```

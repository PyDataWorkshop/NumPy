Introduction To Numpy
======================
- NumPy is an extension to the Python programming language, adding support for large, multi-dimensional arrays and
matrices, along with a large library of high-level mathematical functions to operate on these arrays. 
- The ancestor of NumPy, Numeric, was originally created by Jim Hugunin with contributions from several other developers. 
- In 2005, Travis Oliphant created NumPy by incorporating features of Numarray into Numeric with extensive modifications. 
- NumPy is open source and has many contributors.

<hr>

### The `ndarray` data structure
- The core functionality of NumPy is its `ndarray`, for n-dimensional array, data structure. 
- These arrays are strided views on memory. In contrast to Python's built-in list data structure (which, despite the name, is a dynamic array), these arrays are homogeneously typed: all elements of a single array must be of the same type.
- Such arrays can also be views into memory buffers allocated by C, C++. Cython and Fortran extensions to the CPython interpreter without the need to copy data around, giving a degree of compatibility with existing numerical libraries. This functionality is exploited by the SciPy package, which wraps a number of such libraries (notably BLAS and LAPACK). 
- NumPy has built-in support for memory-mapped `ndarrays`

<hr>

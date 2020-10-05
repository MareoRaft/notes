Numpy notes, mostly from
https://numpy.org/doc/stable/user/quickstart.html
===========================================================


Axes
-----
The FIRST axis is vertical.  The second is horizontal.

numpy.ndarray == numpy.array

a = numpy.array()

a.ndim --> # of dim.s (axes) of the array
a.shape --> the dim.s of the array (an integer for each axis)
a.size --> total # of elements
a.dtype --> the type of the elements
a.itemsize --> the size in bytes of each element
a.data --> direct access to element data, but typically don't use

Array Methods
-----------------
a.sum()
a.sum(axis=1)
a.min()
a.min(axis=0)
a.max()
a.argmax() --> index of the max
a.cumsum()
a.mean()
a.std()



a = np.arange(15).reshape(3, 5)
a
array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14]])

Note that the NUMBERS go LEFT to RIGHT even though 3 is the FIRST dimension listed.  Because the numbers follow the LAST dimension and work BACKWARDS along the dimensions!


complex --> A BUILTIN python type!
1j --> BUILTIN value of i = sqrt(-1)




Ways to init arrays
------------------------
np.array([type, elements, in])
np.arange([start,] stop[, step]) --> returns an array w/ dtype int64
np.linspace(start, stop, num_els) --> stop is INCLUDED
np.logspace(start, stop, num_els) --> same as above, but numbers increase exponentially
np.zeros((3,4)) --> create a "null vector" w/ data type float64
np.zeros_like(m) --> zeros, but same shape as m.  ALSO uses the DATA TYPE of m into the result.
np.ones((3,4))
np.ones_like(m)
np.empty((3,4)) --> uninitialized vals, vals appear random.  Use this when you will systematically overwrite the values later.  (because this is more performant than np.zeros())
np.fromfunction(f,(5,4),dtype=int)
np.fromiter()
rng.random((3,4)) --> see rng / random number generator below
np.copy(my_array)
np.where() --> like an if-else statement in a list comprehension!.  Constructs NEW array.




x = linspace(0,5,10)
f = np.sin(x) --> ELEMENTWISE application.

  * Almost ALL operators apply ELEMENTWISE.


@ - matrix mult (NOT elementwise)
A.dot(B) - matrix mult - " - this is MATRIX MULTIPLICATION.  Hence two 1-dim vectors of shapes (4,) and (4,) will give a "dot product", but two 2-dim of shapes (4,1) and (1,4) will give an outer product.
A.outer(B) - outer product - the result is `A.ndim + B.ndim` dimensional
np.allclose(A, B) - check for equality


a[:6:2] = 1000 --> sets elements at indices 0, 2, and 4 to 1000.
a[::-1]






>>> def f(x,y):
...     return 10*x+y
...
>>> b = np.fromfunction(f,(5,4),dtype=int)
>>> b
array([[ 0,  1,  2,  3],
       [10, 11, 12, 13],
       [20, 21, 22, 23],
       [30, 31, 32, 33],
       [40, 41, 42, 43]])

The INDICES (x,y) are fed into f.

b[0:5, 1]
b[ : ,1]
b[1:3, : ]

There is a slice PER DIMENSION (shown above).

x[1,2,...]
x[...,3]
x[4,...,5,:]

You can use DOTS to fill in colons automatically (shown above).



for el in b:
   # iterates over 1st dimension of b

for el in b.flat:
   # iterates over all elements of b




Random stuff
----------------------

### random number generator
np.version.version (make sure you have 1.19 or newer)
rng = np.random.default_rng(1)
rng.random((2,5))
>>> a = np.floor(10*rg.random((3,4)))
>>> a
array([[3., 7., 3., 4.],
       [1., 4., 2., 2.],
       [7., 2., 4., 9.]])

### random normal distribution (Gaussian)
rng.standard_normal(10) --> (size=, dtype=, out=)
rng.normal() --> (loc=<<mean>>, scale=<<std dev>>, size=<<output shape>>)





Shape Manipulation
-----------------------
These return NEW arrays.
a.ravel()  --> unravels into 1-dim array
a.reshape(3, 5) --> unravels then reshapes into new dims --> remember, this is STILL a pointer to the SAME underlying data!
a.T --> the transpose








went up to beginning of Shape Manipulation and stopped.




Exercises
see http://sanjaymeena.io/tech/100-Numpy-Exercises/
----------------
np.nonzero(arrayvarhere)
np.identity(3)
D = 4
b = np.ones((D, D))
a = np.zeros((D+2, D+2))
a[1:-1, 1:-1] = b
np.pad(b, pad_width=3[, mode='constant'][, constant_values=0])
np.nan
np.inf
In [75]: np.nan == np.nan
Out[75]: False
In [78]: np.nan in set([np.nan])
Out[78]: True
In [79]: 0.3 == 3 * 0.1
Out[79]: False





Unorganized
-----------------
np.all()
np.any()

np.matrix --> THESE are 2-dimentional np.ndarray's with a WRAPPER around them to make it easier to treat them as matrices.

np.maximum(x, y)
np.minimum(x, y)

np.linalg.solve --> use for matrix inversion, bc more efficient than np.linalg.inv
np.linalg.svd ----> the SVD decomposition

np.save('/tmp/x.npy', x) --> to save an array to a file
np.load('/tmp/x.npy')



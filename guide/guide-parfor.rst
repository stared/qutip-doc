.. QuTiP 
   Copyright (C) 2011-2012, Paul D. Nation & Robert J. Johansson

.. _parfor:

******************************************
Running Problems in Parallel
******************************************

QuTiP's Built-in Parallel for-loop
----------------------------------

.. ipython::
   :suppress:

   In [1]: from qutip import *

Often one is interested in the output of a given function as a single-parameter is varied.  For instance, we can calculate the steady-state response of our system as the driving frequency is varied.  In cases such as this, where each iteration is independent of the others, we can speedup the calculation by performing the iterations in parallel.  In QuTiP, parallel computations may be performed using the :func:`qutip.parfor` (parallel-for-loop) function.

To use the parfor function we need to define a function of one or more variables, and the range over which these variable are to be iterated.  For example:


.. ipython::

   In [1]: def func1(x): return x, x**2, x**3
   
   In [2]: [a,b,c] = parfor(func1, range(10))
   
   In [3]: print(a)
   
   In [4]: print(b)
   
   In [5]: print(c)

One can also use a single output variable as:

.. ipython::

   In [1]: x = parfor(func1, range(10))
   
   In [2]: print(x[0])
   
   In [3]: print(x[1])
   
   In [4]: print(x[2])

The :func:`qutip.parfor` function is not limited to just numbers, but also works for a variety of outputs:

.. ipython::

   In [1]: def func2(x): return x, Qobj(x), 'a' * x
   
   In [2]: [a, b, c] = parfor(func2, range(5))
   
   In [3]: print(a)
   
   In [4]: print(b)
   
   In [5]: print(c)


.. note::

    New in QuTiP 3.

One can also define functions with **multiple** input arguments and even keyword arguments:

.. ipython::
    
    In [1]: def sum_diff(x,y,hello=0): return x+y,x-y,hello
    
    In [2]: parfor(sum_diff,[1,2,3],[4,5,6],hello=5)
    
Note that the keyword arguments can be anything you like, but the keyword values are **not** iterated over. The keyword argument *num_cpus* is reserved as it sets the number of CPU's used by parfor. By default, this value is set to the total number of physical processors on your system. You can change this number to a lower value, however setting it higher than the number of CPU's will cause a drop in performance.

Parfor is also useful for repeated tasks such as generating plots corresponding to the dynamical evolution of your system, or simultaneously simulating different parameter configurations.


IPython-Based parfor
--------------------

.. note::

    New in QuTiP 3.

When QuTiP is used with IPython interpreter, there is an alternative parallel for-loop implementation in the QuTiP  module :func:`qutip.ipynbtools`, see :func:`qutip.ipynbtools.parfor`. The advantage of this parfor implementation is based on IPythons powerful framework for parallelization, so the compute processes are not confined to run on the same host as the main process. 

Parallel picloud Computations
-----------------------------

.. note::

    New in QuTiP 3.

New to QuTiP version 3 is the option to run computations in parallel on the cloud computing platform provided by PiCloud. You must have their software installed on your machine, and an active account, for this function to work. Note that, at present, the picloud software is **only available for Python version 2.7**. Using the picloud function is very similar to using parfor, however the picloud function does not accept any keyword arguments:

.. ipython::
    
    In [1]: def add(x,y): return x+y
    
    In [2]: picloud(add,[10,20,30],[5,6,7])


 

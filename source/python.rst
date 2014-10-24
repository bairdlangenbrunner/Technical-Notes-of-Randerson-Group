Python
****************************************************************************************************

Installation, Package Manager and Interactive Tools
====================================================================================================

Anaconda
----------------------------------------------------------------------------------------------------

Canopy
----------------------------------------------------------------------------------------------------

IPython
----------------------------------------------------------------------------------------------------

Auto-load Modules on Startup
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
.. highlight:: bash

To create the blank config files, run::

    ipython profile create [profilename]

If you leave out the profile name, the files will be created for the ``default`` profile. These will typically be located in :file:`~/.ipython/profile_default/`, and will be named :file:`ipython_config.py`, :file:`ipython_notebook_config.py`, etc. The settings in :file:`ipython_config.py` apply to all IPython commands.

Add something like the following lines to :file:`ipython_config.py`::

    c.InteractiveShellApp.exec_lines = [
        'import numpy',
        'import scipy'

Useful Packages
====================================================================================================

Math
----------------------------------------------------------------------------------------------------

Scipy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Numpy
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



Visualization
----------------------------------------------------------------------------------------------------

Matplotlib
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Seaborn
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++




GIS
----------------------------------------------------------------------------------------------------

Basemap
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

GDAL/OGR
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


Python Gotchas
====================================================================================================

Shallow and Deep Copy
----------------------------------------------------------------------------------------------------
Relevant for compound objects, i.e. objects containing other objects, like lists or class instances. For example::

    colours1 = ["red", "green"]
    colours2 = colours1
    colours2[1] = "blue"
    print colours1

Results in::
    
    ['red', 'blue']

This is because no new memory location had been allocated for ``colours2`` when ``colours2 = colours1``, only a pointer is created (shallow copy). However, if you do::

    colours1 = ["red", "green"]
    colours2 = colours1
    colours2 = ["rouge", "vert"]
    print colours1

The result will be::

    ['red', 'green']

This is becase a new memory location was allocated for ``colours2`` when you assigned a complete new list. The same thing goes with Numpy arrays::

    a = numpy.array( [[1,2,3], [4,5,6]] ) 
    b = a 
    b[0,0] = 99 
    a

Results in::

    array([[99,  2,  3], 
           [ 4,  5,  6]]) 

This can be avoided by using method ``deepcopy`` from the standard module **copy**, or method ``.copy`` in Numpy::

    b = a.copy()

However, shallow copy and related ``.view`` method in Numpy can be used to save memory in many cases.

Matplotlib crash with X11 forward 
----------------------------------------------------------------------------------------------------
Crashes with ``-X``. Use ``-Y`` instead.

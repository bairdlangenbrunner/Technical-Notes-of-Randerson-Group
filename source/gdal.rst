GDAL Utilities and Python Binding
****************************************************************************************************
.. highlight:: bash
Installation
====================================================================================================

Mac
----------------------------------------------------------------------------------------------------
The essiest way of isntalling gdal library on Mac is using `MacPorts <https://www.macports.org/>`_. Install gdal with hdf4, hdf5 and netCDF support::

    sudo port install gdal +hdf4 +hdf5 +netcdf

Linux
----------------------------------------------------------------------------------------------------


APT
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++


YUM
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Mannual
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Unfortiunately we don't have root access on Greeplanet, and many of the packages are out of date. Therefore we need to build gdal and all its dependencies. Use ``--prefix=path`` flag to avaid the need of root access. The fallowing is and example of installing *GDAL* with hdf4, hdf5, netcdf and proj4 support. Everything will be installed at ``$HOME/local``, you can change the location according to your need. 

.. note:: Install on login nodes instead of computation nodes. Some library cannot be found under computation nodes.

First download zlib, and install by::

    ./configure --prefix=$HOME/zlib
    make
    make install


hdf5::

    ./configure --prefix=$HOME/local/hdf5 --enable-shared --enable-static --enable-cxx=yes
    make & make check
    make install


jpeg::

    ./configure --prefix=$HOME/local/jpeg --enable-shared --enable-static
    make
    make install


hdf4. First you have to set the ``LD_LIBRARY_PATH`` variable by::
    
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/local/jpeg/lib
Then you can install by::

    ./configure --prefix=$HOME/local/hdf4 --with-jpeg=$HOME/local/jpeg --with-zlib=$HOME/local/zlib --enable-shared --enable-static --disable-fortran --disable-netcdf
    make
    make install
You need to disable netcdf to avoid possible conflict with netCDF linbrary.

netCDF. Set varibles first::

    export CPPFLAGS=-I$HOME/local/hdf5/include
    export LDFLAGS=-L$HOME/local/hdf5/lib
    export LD_LIBRARY_PATH=$HOME/local/hdf5/lib
Then install::
    
    ./configure --prefix=$HOME/local/netcdf
    make
    make install


proj4::

    ./configure --prefix=$HOME/local/proj4
    make & make check
    make install


Finally GDAL. You might need to logout and login again before this step (reason unclear). You can try ``--with-libz=$HOME/local/zlib`` instead of ``--with-libz=internal``; the later will use the internal version of libz with GDAL, with might cause problem when working with hdf4::

    ./configure --prefix=$HOME/local/gdal --with-hdf4=$HOME/local/hdf4 --with-hdf5=$HOME/local/hdf5 --with-netcdf=$HOME/local/netcdf --with-libz=internal --with-static-proj4=$HOME/local/proj4 --with-python
    make
    make install

Then add your gdal path to your ``.bashrc`` file. You can check dynamic dependencies by::

    ldd `which gdalinfo`

.. note:: Do a ``ldd`` and you might find libz linked to a local(old) version, even if you did ``--with-libz=$HOME/local/zlib`` in the configuration file. This might cause problem. Reason unclear. 


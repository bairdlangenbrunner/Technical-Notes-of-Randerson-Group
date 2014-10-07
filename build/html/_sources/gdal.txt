GDAL Utilities and Python Binding
****************************************************************************************************
.. highlight:: bash
Installation::
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
Unfortiunately we don't have root access on Greeplanet, and many of the packages are out of date. Therefore we need to build gdal and all its dependencies. Use ``--prefix=path`` flag to avaid the need of root access::

    ./configure --prefix=$HOME/local --with-hdf5=$HOME/local/hdf5km --with-hdf4=$HOME/local/hdf4 --with-netcdf=$HOME/local/netcdf --witlih-static-proj4=$HOME/local/proj4 --with-libkml=$HOME/local/libkml --with-static-zlib=$HOME/local/zlib 


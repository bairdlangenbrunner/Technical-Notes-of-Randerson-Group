.. highlight:: bash

Resource for Randerson Group
****************************************************************************************************

Computation
====================================================================================================

Yellowstone
----------------------------------------------------------------------------------------------------

Greenplanet
----------------------------------------------------------------------------------------------------
Randerson group has nodes from ``-10-251`` to ``-10-254``, and  reservation for 48 cores on ``-2-9``. Name of queue is ``randerson_f``.

Data
====================================================================================================
Due to the space limit on hard drives, datasets are stored in different places. Generally it might not be a good idea to store your data in your home directory, as there are smaller space allocated for the drive home directory. You can make symbolic link in your data directory to keep organized; see :ref:`symb-ln`.

==============================    =================  ======================  ==================================================
Data Name                         Resolution         Coverage                Path 
==============================    =================  ======================  ==================================================
MCD12Q1 (land cover)              500m/year          2001-2010/global        /gdata/randerson2/group/MODIS/MCD12Q1
MOD13A1 (vegetation index)        500m/16day         2000-2013/global        /gdata/randerson2/group/MODIS/MOD13A1
MOD44B (tree cover)               500m/year          2000-2010/global        /gdata/randerson3/group/MODIS/MOD44B
MCD64A1 (burn area)               500m/month         2000.10-2013/global     /gdata/randerson2/giglio/MCD64A1
GLEAM ET                          /                  /                       /gdata/randerson3/mmu/ILAMB/DATA/et/GLEAM/original
GLC (land cover)                  30s/year           2000, 2009/global       /data8/data/guol3/GEM/GLC
gROADS (road)                     -/-                -/global                /data8/data/guol3/CIESIN/gROADS
GLoElev (elevation)               30s,5min/-         -/global                /data8/data/guol3/FAO/GloElev
GLW-cattle (cattle)               0.05d/year         2005/global             /data8/data/guol3/FAO/GLW/cattle/totcor
TRMM-3B43 (precip)                0.25d/month        2000-2014.05/tropics    /data8/data/guol3/TRMM/3B43
WorldClim (mean temp/precip)      30s,10min/month    -/global                /data8/data/guol3/WorldClim
LandScan (population)             1km/year           2013/global             /data8/data/guol3/LandScan/
==============================    =================  ======================  ==================================================

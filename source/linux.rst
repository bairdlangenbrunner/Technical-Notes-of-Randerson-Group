.. highlight:: bash

Linux System and Bash
****************************************************************************************************
Here is a useful `introduction on Linux systen <http://ryanstutorials.net/linuxtutorial/>`_, including information on `vi <http://ryanstutorials.net/linuxtutorial/vi.php>`_ and `Grep and Regular Expressions <http://ryanstutorials.net/linuxtutorial/grep.php>`_. Greenplanet uses `Scientific Linux <http://en.wikipedia.org/wiki/Scientific_Linux>`_, with `Bash <http://en.wikipedia.org/wiki/Bash_(Unix_shell)>`_ as default system language. For example you can navigate system with ``cd path``, execute a file with ``. /someExecutable``, make new directory with ``mkdir directoryName``. 

Connecting to Linux Server
====================================================================================================
Tips on connecting/downloading to/from a server, especially `Green Planet <https://greenplanet.ps.uci.edu/help.html>`_.

Login Nodes
----------------------------------------------------------------------------------------------------

First login to **login nodes**. With X11 forwarding enabled::

    ssh -X userName@gplogin1.ps.uci.edu
Or with trusted X11 forwarding enabled::

    ssh -Y userName@gplogin1.ps.uci.edu
Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls. Then enter password.

Using public key authentication with SSH avoids typing password every time. Instructions can be found `here <http://crashmag.net/public-key-authentication-awith-ssh-both-with-and-without-a-password>`_.

Computing Nodes
----------------------------------------------------------------------------------------------------
Computation should be done on computing nodes. Simply ``ssh`` to an computing node by ``ssh compute-2-6 -Y``. Randerson group has nodes from ``-10-251`` to ``-10-254``, and  reservation for 48 cores on ``-2-9``.

You could also use ``qsub`` to request memory and CPU for current session. For example::

    qsub -q randerson_f -X -I -l walltime=24:00:00,mem=16g,nodes=1:ppn=30

Job Submission to Cluster
----------------------------------------------------------------------------------------------------
**Green Planet** uses the open-source PBS torque system:: 

    qsub -q randerson_f -l nodes=1:ppn=12 test.py
Show all queues::
    
    qstat -Q
Delete a job:: 
    
    qdel jobID
Report the status of a job::

    checkjob jobID

Download/Upload from/to a Server::

    scp userName@gplogin1.ps.uci.edu:fileSourcePath fileTargetPath

For path in Linux system, space should be proceeded by ``\``. For exampe ``./Google Drive`` should be ``./Google\ Drive``.

System Tools
====================================================================================================
Softwares can be found under ``/sopt``.

Download
----------------------------------------------------------------------------------------------------    
wget::

    wget -r -np -A.nc http://dust.ess.uci.edu/Yi essgcm15/
    wget -r --follow-ftp http://e4ftl01.cr.usgs.gov/MOLT/MOD15A2.005/ -nd -A hdf 
    wget -r http://e4ftl01.cr.usgs.gov/MOLT/MOD15A2.005/2001.11.09/ *h20v10*.hdf
    wget -r --no-parent --reject "index.html*" http://e4ftl01.cr.usgs.gov/MOLT/MOD15A2.005/*

**Matlab** is located at ``/sopt/rc/matlab_float_2012b.sh``. First execute the ``.sh`` file, and then start Matlab with ``matlab``, ``matlab -nodesktop`` or ``matlab -nodisplay``

Get **processes** snapshot with ``ps``, or user-oriented output format with ``ps u``. Kill a process with ``kill -9 processID``.


``screen -a`` starts a new **screen**, *Ctrl-a-d* detachs from it, and ``screen -r screenID`` reattachs. *screenID* will showup after ``screen -r`` when you have multi-screens. Terminate a screen with ``screen -X -S screenID quit``. If your network connection fails, screen will automatically detach your session.

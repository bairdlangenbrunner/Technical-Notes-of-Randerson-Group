.. highlight:: bash

Linux System and Bash
****************************************************************************************************

Here is a useful `introduction on Linux systen <http://ryanstutorials.net/linuxtutorial/>`_, including `introduction on vi <http://ryanstutorials.net/linuxtutorial/vi.php>`_ and `grep and regular expressions <http://ryanstutorials.net/linuxtutorial/grep.php>`_. 

Greenplanet uses `Scientific Linux <http://en.wikipedia.org/wiki/Scientific_Linux>`_, with `Bash <http://en.wikipedia.org/wiki/Bash_(Unix_shell)>`_ as default system language. More infomation can be found at `Greenplanet help page <https://greenplanet.ps.uci.edu/help.html>`_.

Connecting to Linux Server
====================================================================================================

Login Nodes
----------------------------------------------------------------------------------------------------

First login to **login nodes**. With X11 forwarding enabled::

    ssh -X userName@gplogin1.ps.uci.edu

Or with trusted X11 forwarding enabled::

    ssh -Y userName@gplogin1.ps.uci.edu

Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls. Then enter password. After you login for the first time, you can type ``passwd`` to change your password.

Public Key Authentication with SSH
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
SSH can use the RSA cryptosystem to generate a key pair (public key and private key), and could be used to avoid typing password every time. Math behind this interesting asymmetric cryptography algorithms can be found `here <http://mathworld.wolfram.com/RSAEncryption.html>`_.

First ``cd`` to your local home directory, and run::
    
    ssh-keygen -t rsa

You can leave ``passphrase`` empty when been asked. If you don't have directory ``.ssh`` on your server, you might need to create one by ``mkdir .ssh`` in your home directory. Then upload the public key to the server::
    
    cat ~/.ssh/id_rsa.pub | ssh user:password@hostname 'cat >> .ssh/authorized_keys'

 And you are all set. 

.. warning::
    Be sure to ``cat`` the public key instead of ``scp`` it; copying the key will overwrite your previous authorized keys.

SSHFS (Linux, Mac and Windows)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
This will mount remote files and allows you to manipulate them as local files. Install SSHFS, for example ``sudo apt-get install sshfs`` on Ubuntu/Debian, `download SSHFS and OSXFUSE <http://osxfuse.github.io/>`_ or ``brew install sshfs`` on Mac. Then create your mount point by ``mkdir /home/NameForMyPoint``, and mount it by ``sshfs UserName@RemoteServer:/RemotePath /home/NameForMyPoint``.

Macfusion (Mac)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Similar to SSHFS, but uses graphic interface. Less stable. Instruction and download from `here <http://macfusionapp.org/>`_. Depends on `OSXFUSE <http://osxfuse.github.io/>`_. 

Computing Nodes
----------------------------------------------------------------------------------------------------
Computation should be done on computing nodes. Simply ``ssh`` to an computing node by ``ssh compute-2-6 -Y``.
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

Bash Basic Commands
====================================================================================================
Change Directory::

    cd path

Make new directory::
    
    mkdir DirectoryName 

Execute a file with (you may need to do ``chmod +x SomeExecutable`` first)::
    
    ./SomeExecutable

Get **processes** snapshot with ``ps``, or user-oriented output format with ``ps u``. Kill a process with ``kill -9 processID``.

``screen -a`` starts a new **screen**, *Ctrl-a-d* detachs from it, and ``screen -r screenID`` reattachs. *screenID* will showup after ``screen -r`` when you have multi-screens. Terminate a screen with ``screen -X -S screenID quit``. If your network connection fails, screen will automatically detach your session. You can't scroll up/down in Linux Screen with your mouse; instead you can type ``Ctrl + a`` and then press ``esc`` to enter scroll mode for Linux Screen. Then you can press ``Ctrl + u`` and ``Ctrl + d`` to scroll the display up/down half screen-full, or ``Ctrl + b`` and ``C-f`` scroll the display up/down a full screen.

.. _symb-ln:

Symbolic Link
----------------------------------------------------------------------------------------------------
Symbolic links are useful to organize files scattered on different disks. Create a symbolic link with::

    ln -s $oldfnm $newfnm

For example, here is a Bash script to create symbolic links from MCD12Q1 ``/gdata/randerson2/group/MODIS/MCD12Q1/V051/`` to current directory, rename them, and put them into different folders according to tile::

    #!/bin/bash
    dir1=/gdata/randerson2/group/MODIS/MCD12Q1/V051/
    dir2=$PWD
    echo $dir1
    echo $dir2
    cd $dir1
    for file in */*.hdf
    do
      if [ -e "$file" ]
      then 
        vyear=${file:20:4}  
        vdoy=${file:24:3}
        vh=${file:29:2}
        vv=${file:32:2} 
        newdir="$dir2/h"$vh"v"$vv""
        oldfnm="$dir1/$file"
        newfnm="$newdir/MCD12Q1.A"$vyear""$vdoy".h"$vh"v"$vv".hdf"
        echo $newfnm
        if [ -d $newdir ]
        then
          echo "Dir exist" 
        else 
          mkdir $newdir
        fi
        ln -s $oldfnm $newfnm
      fi
    done
    
    cd $dirc

Bash Gotchas
----------------------------------------------------------------------------------------------------

Space In File Name
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
For path in Linux system, space should be proceeded by ``\``. For exampe ``./Google Drive`` should be ``./Google\ Drive``.

System Tools
====================================================================================================
Softwares can be found under ``/sopt``.


Matlab
----------------------------------------------------------------------------------------------------
**Matlab** is located at ``/sopt/rc/matlab_float_2012b.sh``. First execute the ``.sh`` file, and then start Matlab with ``matlab``, ``matlab -nodesktop`` or ``matlab -nodisplay``

Download
----------------------------------------------------------------------------------------------------    

wget
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

With user name and password::
    
    wget ftp://ftp.cartographic.com/09_22_14/LandScan2013.zip --user=ucs4nd --password="s4ndi3g0"

Multiple files::
    
    wget -r --no-parent -A.nc --reject "index.html*" http://e4ftl01.cr.usgs.gov/MOLT/MOD15A2.005/*


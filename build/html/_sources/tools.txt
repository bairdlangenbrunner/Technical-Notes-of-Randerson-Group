.. highlight:: bash

Useful Tools
****************************************************************************************************

vi
====================================================================================================
# at beginning of 14-20 line::

    14,20s/^/#/


git
====================================================================================================
Add and commit in one line. Set global alias for the first time::

    git config --global alias.add-commit '!git add -A && git commit'
and then::
    
    git add-commit -m 'Stable version'

Delete remote branch::
    
    git push origin --delete <branchName>

Delete local::
    
    git branch -d local_branch

Overwrite local change::

    git fetch --all
    git reset --hard origin/master

Decompilers
====================================================================================================

Python
----------------------------------------------------------------------------------------------------
::
    
    uncompyle2 <pyc file>

Source code at https://github.com/wibiti/uncompyle2
 

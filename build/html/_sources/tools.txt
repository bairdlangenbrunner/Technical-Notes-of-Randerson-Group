.. highlight:: bash

Useful Tools
****************************************************************************************************

vi
====================================================================================================
# at beginning of 14-20 line::

    14,20s/^/#/


git
====================================================================================================
Powerful tool for verson control and cooperation. A nice introduction can be found here: `git-the simple guide <http://rogerdudler.github.io/git-guide/>`_ (in whatever language you prefer!).

Different ways of doing ``git add``
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
::

    git add .
Looks at the working tree and adds all those paths to the staged changes if they are either changed or are new and not ignored, it does not stage any 'rm' actions.


::

    git add -u 
Looks at all the currently tracked files and stages the changes to those files if they are different or if they have been removed. It does not add any new files, it only stages changes to already tracked files.


::

    git add -A
Equivalent to ``git add .; git add -u``.

Delete a branch
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Remote::

    git push origin --delete <branchName>

Local::
    
    git branch -d local_branch

Overwrite local change
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
::

    git fetch --all
    git reset --hard origin/master


Set global alias
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Add and commit in one line. Set global alias for the first time::

    git config --global alias.add-commit '!git add -A && git commit'
and then::
    
    git add-commit -m 'Whatever you want to say'

Transfer repository between different version control system
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
For example, transfer your repository from `Bitbucket <https://bitbucket.org/>`_ to `GitHub <https://github.com/>`_ (Sorry Bitbucket!). First import your repository to GitHub using importer provided by GitHub: https://porter.github.com/new. Then in your local up-to-date repository::

    git remote rename origin bitbucket
    git remote add origin https://github.com/IAmJustAnExamplePerson/AndIAmJustAnExampleRepository.git
    git push origin master

Decompilers
====================================================================================================
Save you source code from byte-code.

Python
----------------------------------------------------------------------------------------------------
Get back your **.py** file from **.pyc** file.

uncompyle2
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
For Python2.7. Source code at https://github.com/wibiti/uncompyle2. Usage::
 
    uncompyle2 <pyc file>

unpyc3
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
For Python3.2. Source code at https://code.google.com/p/unpyc3/. Usage (in Python):

.. code-block:: python

    from unpyc3 import decompile
    import foo
    print(decompile(foo))

.. highlight:: bash

Useful Tools
****************************************************************************************************

vi (vim)
====================================================================================================
A nice introduction on vi can be found `here <http://ryanstutorials.net/linuxtutorial/vi.php>`_. 

Configurations for Python
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Greenplanet has already installed vim. You can check the version of vim installed by typing in version in vim’s command mode. The vim is only the basic version and does not have python setting, such as automatic indenting. Users can improve their experience with vim by editing the .vimrc file and .vim folder. If the file and folder do not exist, create them.

1. Download pydiction
    #. download the newest version of pydiction from `here <http://www.vim.org/scripts/script.php?script_id=850>`_.
    #. copy ``python_pydiction.vim`` to ``~/.vim/after/ftplugin``; also copy ``complete-dict`` and ``pydiction.py`` to ``~/.vim``.
    #. edit the ``.vimrc`` file and put the following codes in it::

        let Tlist_Auto_Hightlight_Tag=1
        let Tlist_Auto_Open=1
        let Tlist_Auto_Update=1
        let Tlist_Display_Tag_Scope=1
        let Tlist_Exit_OnlyWindow=1
        let Tlist_Enable_Dold_Column=1
        let Tlist_File_Fold_Auto_Close=1
        let Tlist_Show_One_File=1
        let Tlist_Use_Right_Window=1
        let Tlist_Use_SingleClick=1
        nnoremap<silent><F8> :TlistToggle<CR>
    
        filetypepluginon
        autocmdFileType python setomnifunc=pythoncomplete#Complete
        autocmdFileType javascrīpt setomnifunc=javascriptcomplete#CompleteJS
        autocmdFileType html setomnifunc=htmlcomplete#CompleteTags
        autocmdFileType css setomnifunc=csscomplete#CompleteCSS
        autocmdFileType xml setomnifunc=xmlcomplete#CompleteTags
        autocmdFileType php setomnifunc=phpcomplete#CompletePHP
        autocmdFileType c setomnifunc=ccomplete#Complete
        
        
        let g:pydiction_location='~/.vim/complete-dict'
        setautoindent
        settabstop=4
        setshiftwidth=4
        setexpandtab
        settextwidth=0
        syntax on
        filetypeindentpluginon
    
Now you can type ``retab`` in vim to change tab into spaces.

2. If you want highlight your code, copy the ``highlight.vim`` from `here <http://www.vim.org/scripts/script.php?script_id=1599>`_ to ~/.vim/plugin.

3. You can also download python syntax to make the highlighting better. Copy ``python.vim`` from `here <http://www.vim.org/scripts/script.php?script_id=790>`_ to ``~/.vim/syntax/``. 

Find and Replace/Add
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
For example, adding ``#`` at beginning of line 14-20::

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

Set global igore files
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
It's convenient to make certain system-generated files ignored by git. Create a file called ``.gitignore``, add the type of file you want to ignore, and do::

    git config --global core.excludesfile ~/.gitignore

Here's `an example <https://gist.github.com/octocat/9257657>`_ of the ``.gitignore`` file.

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

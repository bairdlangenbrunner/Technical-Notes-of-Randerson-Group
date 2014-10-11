.. Technical Notes of Randerson Group master file, created by
   sphinx-quickstart on Tue Sep 30 16:27:01 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. highlight:: bash

Welcome to Technical Notes of Randerson Group!
=================================================

How to contribute
----------------------------------------------------------------------------------------------------
This documentation is build with `Sphinx <http://sphinx-doc.org/>`_, using **reStructuredText**. The syntax is straight forward and the source files are self-explanatory. Therefore, you don't need much knowledge on either **Sphinx** nor **reStructuredText** to contribute to it.

Login to ``zea.ess.uci.edu``, and find this repository here::

    /var/www/html/group/Technical-Notes-of-Randerson-Group

Or clone this repository to your local mechine by::

    git clone https://github.com/uci-randerson-lab/Technical-Notes-of-Randerson-Group.git 

Source file is inside directory ``source`` and you can edit the ``.rst`` files directly. Each of the ``.rst`` files correspond to a page in the ``.html`` file. If you add a page, don't forget to add the name of the source file in ``index.rst``. 

After you finish your editing, run ``make html`` in the top directory, and you will find your newly built html file in ``build/html``. Then add changes to git by::

    git add -A

Commit and comment your changes by::

    git commit -m 'Your message'

Finally, push your changes to git hosted on `UCI Randerson Lab GitHub Group <https://github.com/uci-randerson-lab>`_::

    git push

Contents:
====================================================================================================
.. toctree::
   :maxdepth: 2

   linux
   python
   gdal
   tools
   group

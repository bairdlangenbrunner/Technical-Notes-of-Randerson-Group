The html file can be viewed here: http://technical-notes-of-randerson-group.readthedocs.org/en/latest/


How to contribute
----------------------------------------------------------------------------------------------------
This documentation is build with Sphinx <http://sphinx-doc.org/>, using **reStructuredText**. The syntax is straight forward and the source files are self-explanatory. Therefore, you don't need much knowledge on either **Sphinx** nor **reStructuredText** to contribute.

Here's how. Click the ``Edit on GitHub`` link on the upper right corner of the page, and it will take you to the source on GitHub. Just edit the source here. You will have to be a member of ``UCI Randerson Lab`` group on GitHub.

Or clone this repository to your local machine by::

    git clone https://github.com/uci-randerson-lab/Technical-Notes-of-Randerson-Group.git 

Source file is inside directory ``source`` and you can edit the ``.rst`` files directly. Each ``.rst`` file corresponds to one page in the ``.html`` file. If you add one ``.rst`` file, don't forget to add the name of the source file in ``index.rst``. 

After you finish your editing, run ``make html`` in the top directory, and you will find your newly built html file inside ``build/html``. Then add changes to git by::

    git add -A

Commit and comment your changes by::

    git commit -m 'Your message'

Finally, push your changes to git hosted on `UCI Randerson Lab GitHub Group <https://github.com/uci-randerson-lab>`_::

    git push

Or if that's to complicated, you can send your notes to Guo <guol3@uci.edu> and ask him to add it for you.

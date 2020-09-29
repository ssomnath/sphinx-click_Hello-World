sphinx-click_Hello-World
========================
Minimal repository to demonstrate how to set up `sphinx-click <https://sphinx-click.readthedocs.io/en/latest/usage/#example>`_

Generating documentation
------------------------
.. code:: bash

   $ cd docs
   $ make html
   
Open ``index.html`` under ``docs/build/index.html`` in a web browser.

Notes and tips
--------------
Documenting a click group
~~~~~~~~~~~~~~~~~~~~~~~~~
Here's the recipe for documenting a single group 

In ``index.rst``
^^^^^^^^^^^^^^^^
```rst
  .. click:: python_package_name:click_group_name
    :prog: command-name
    :nested: full
```

The ``command-name`` could be any string. One only needs to make sure that ``python_package_name`` and ``click_group_name`` are entered correctly. The name of the python file containing the click code does **not** figure into the index.rst file.

In the example, I renamed the ``hello_world.py`` to bye_world.py and updated ``__init__.py`` within the package accordingly to make sure that nothing was broken. The fact that I had renamed the file seemed to make no difference at all. 

Within the source code
^^^^^^^^^^^^^^^^^^^^^^
The ``__init__.py`` for the package must apparently contain:

```python
From .python_file_name import *
```

The rest of the things as shown below are unnecessary
```python
from . Import python_file_name 
```

or

```python
__all__ = [‘python_file_name’]
```

Documenting other click groups
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Need to add one block (as shown above) for **each** click group, even if the subsequent click groups are contained within the same python file. There does not appear to be any recursion capability as such to automatically pick up all click groups.

Bizarre behavior or human error
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Deleting files (either source or docs) causes ``sphinx-click`` (or Mac's ``Terminal`` app) to freak out. It starts to look into ``Trash`` and tires to build from there. Instead, start a new terminal, navigate to the docs folder and then try generating documentation again.

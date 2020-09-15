.. hello_world documentation master file, created by
   sphinx-quickstart on Tue Sep 15 16:44:11 2020.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to hello_world's documentation!
=======================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

Click part
----------

.. click:: hello_world:greet
  :prog: hello-world
  :nested: full

.. The :program:`hello` command accepts a :option:`user` argument. If this is
   not provided, the :envvar:`USER` environment variable will be used.

Indices and tables
------------------
* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
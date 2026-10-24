Camltac documentation
=====================

The documentation is built with `Sphinx <https://www.sphinx-doc.org>`_ and `Alectryon <https://github.com/cpitclaudel/alectryon>`_.

Dependencies
------------

OCaml packages:
  ``opam install odoc vsrocq-language-server`` 

Camltac, installed in the current opam switch:
  ``dune build @install``

Python packages:
  ``pip install -r requirements.txt``

Build
-----

.. code:: bash

   opam exec -- make html

The result is in `_build/html`.

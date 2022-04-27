.gitignore tricks
=========================

1. How to ignore any file without extensions?

.. code::

    # ignore everything.
    *
    # unignores anything that is a directory.
    !*/
    # unignores all files with an extension.
    !*.*


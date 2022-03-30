Unix / Linux commands
=======================

grep
*****
* The grep command expects either a file (or, in the case of -r, directory) name or input from the standard input stream.


1. Search for files by extensions

    .. code-block:: bash

        ls | grep .[ext]

        # recursively
        ls | grep -r .[ext]

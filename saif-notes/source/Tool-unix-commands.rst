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


apt
****
* ``apt update`` - update the package metadata (this is necessary to see latest packages and **should be done before installing**)

* ``apt install $pkg`` - install a package

* ``apt purge $x`` - remove a package **and** its configuration (by default the configuration is left behind)

* ``apt autoremove --purge`` - remove any packages which are no longer depended on (usually useful after apt purge)

* ``dpkg -l`` - list all currently installed packages

* ``dpkg -L $pkg`` - list the files installed by a particular package

* ``dpkg -S path/to/file`` - find which package provides this file (for instance dpkg -S "$(which dc)")

* ``aptitude why $pkg`` - **tell me why a particular package is installed**

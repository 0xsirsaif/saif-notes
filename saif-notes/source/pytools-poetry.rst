Poetry Notes
===================

Poetry is a tool for dependency management and packaging in Python. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.

Installation
-------------

.. code:: bash

    curl -sSL https://install.python-poetry.org | POETRY_HOME=[/the/path/you/want] python3 -


* if you want to invoke Poetry with simply ``poetry`` in the command line, you have to add ``export PATH="/media/data/linuxthings/poetry/bin:$PATH"`` to ``.bashrc`` file. 


Virtual environments
---------------------

* it will first check if it’s currently running inside a virtual environment. If it is, it will use it directly without creating a new one. But if it’s not, it will use one that it has already created or create a brand new one for you.

* The default Path that ``poetry`` locate its envs is ``.cache/pypoetry/``

* You can change it by

.. code:: bash

    poetry config virtualenvs.path /media/data/linuxthings/poetryenvs/


Poetry Install
----------------

The install command reads the poetry.lock file from the current directory, processes it, and downloads and installs all the
libraries and dependencies outlined in that file. If the file does not exist it will look for pyproject.toml and do the same.

.. code:: bash

    poetry install

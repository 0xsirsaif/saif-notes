Poetry Notes
===================

Poetry is a tool for dependency management and packaging in Python.

Commands
-------------

1. **Installation**

.. code:: bash

    curl -sSL https://install.python-poetry.org | POETRY_HOME=[/the/path/you/want] python3 -


* then, add ``export PATH="/the/path/you/want/poetry/bin:$PATH"`` to ``.bashrc`` file. 


2. **Virtualenvs**

* It will first check if it’s currently running inside a virtual environment.

* The default Path that ``poetry`` locate its envs is ``.cache/pypoetry/``

* You can change it by

.. code:: bash

    poetry config virtualenvs.path /the/path/you/want


3. **Install Packages**

* The install command reads the ``poetry.lock`` file or ``pyproject.toml``

.. code:: bash

    poetry install

Pyenv Notes
============

* `python_environment_setup cool Gist <https://gist.github.com/wronk/a902185f5f8ed018263d828e1027009b>`_
* `realpython Guide to setup/install/use pyenv <https://realpython.com/intro-to-pyenv/>`_
* config:

    .. code-block:: bash

        export PYENV_ROOT="$HOME/.pyenv"
        command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
        eval "$(pyenv init -)"
        eval "$(pyenv virtualenv-init -)"

    
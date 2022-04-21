Bench Commads
===================

1. **Clone an app from the internet or filesystem and set it up in your bench**

.. code:: bash

    bench get-app [OPTIONS: --branch] [NAME] GIT_URL

2. **Create a new site**

.. code:: bash

    bench  new-site [OPTIONS: --db-name] SITE

3. **Use site**

.. code:: bash

    bench use SITE

4. **Install a new app to site, supports multiple apps**

.. code:: bash

    bench  install-app [APP1 APP2 ..]

5. **List apps in site**

.. code:: bash

    bench  list-apps [OPTIONS: --format:[text|json]]

6. ``bench src`` Prints bench source folder path, which can be used to cd into the bench installation repository by ``cd $(bench src)``.
7. 
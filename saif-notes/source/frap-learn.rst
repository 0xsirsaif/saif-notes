Guide to master frappe framework
=================================

* .. toggle-header::
    :header: **Different docs**

    * `Frappe Framework <https://frappeframework.com/>`_

* .. toggle-header::
    :header: **Frappe Technologies**

    * Python
    * JS
    * Redis: Redis is used for caching, maintaing job queues and realtime updates. 
    * MariaDB and PostgresSQL
    * Jinja: the templating engine for Web Views and Print formats.
    * Git: for version control and update management via Bench.
    * Nginx


* .. toggle-header::
    :header: **Sites/Tanent**

    * Frappe is a multitenant platform and each tenant is called a site.
    * Site Resolution: While responding to an HTTP request, a site is automatically selected based on ``Host`` and ``X-Frappe-Site-Name`` header
    * 
    * ``sites_dir`` env var and ``--sites_dir`` bench parameter
        * ``app.txt`` frappe apps, also should be in PYTHONPATH
        * ``common_site_config.json`` optional configuration applied to all sites
        * ``assets`` contain files that are required to be served for the browser client. Auto-generated using ``bench build``
        * .. toggle-header::
            :header: **Site Directory**

            * ``locks`` used by the scheduler to synchronize various jobs using the `File Locking concept <https://en.wikipedia.org/wiki/File_locking>`_
            * ``private`` files that require authentication to access. Like backups
            * ``public``  files that can directly served: ``http://site/files/[]``
            * ``site_config.json`` site specific configuration




* .. toggle-header::
    :header: **App**

    * ``frappe`` is a frappe app which acts as the framework for all apps.
    * .. toggle-header::
        :header: **Inside App**

        * ``requirements.txt`` app deps, get installed when app is being installed.
        * ``dev-requirements.txt``
        * ``package.json`` node dependencies.
        * ``App-Name``
             * ``App-Name``
             * ``hooks.py`` to hook into frappe events and extend or override standard behaviour by frappe.
             * ``modules.txt`` Every frappe app is organized into different modules. Every DocType is part of a module. These modules are listed in this file
             * ``patches.txt``
             * ``public`` Files put here can be accessed via the url ``/assets/custom_app/**/*.``
             * ``templates`` 
                 * to write and manage Jinja Templates.
                 * This directory is directly scanned when you use them in Jinja templates.
                 * ``{% include "" %}``
             * ``www`` files are mapped to portal pages and the URLs match the directory structure.
             * 

* .. toggle-header::
    :header: **APIs**

    * `Document APIs <https://frappeframework.com/docs/v13/user/en/api/document>`_
    * `DB APIs <https://frappeframework.com/docs/v13/user/en/api/database>`_
    * `Jinja APIs <https://frappeframework.com/docs/v13/user/en/api/jinja>`_ 

* .. toggle-header::
    :header: **Core/Under-the-hood**

    * Frappe attaches itself to the ``window`` object under the ``frappe`` namespace.
    * 
    * .. toggle-header::
        :header: **Request Cycle**

        * **Very Important** `Docs <https://frappeframework.com/docs/v13/user/en/python-api/routing-and-rendering>`_


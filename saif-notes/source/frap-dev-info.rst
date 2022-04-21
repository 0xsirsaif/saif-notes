Frappe framework plain informations
=====================================


* the ``assets folder``

    * static files served from ``bench/sites/assets``
    * nginx serves this folder directly
    * urls, ``assets/[any-file.(ext)]``

* the ``public`` folder
    
    * each app has its own public folder which can be used to serve static files 
    * symlinked to ``bench/sites/assets/[app-name]

* Backup and restore guide

    * got to ``home/settings/download-backups``, you got (db backup and file backup (via email))
    * neet to setup email ``(email domain - > email account -> )``

* Hooks

    * allow an app to override the standard implementation or extend it
    * if the hook is defined in multiple apps, the values will be collected from those apps.
    * the implementation of the hook is totally dependent on how the author of the feature intended it to be used.
    
    * JS/CSS assets to inject static JS and CSS assets
        * 


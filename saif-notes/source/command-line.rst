Command line
==============

1. How to kill a process?

    .. code-block:: bash 

        sudo kill -9 [PID]

    * ``kill(1)`` send signal to process
    * ``-9`` name: KILL, Action: exit, Discription: cannot be blocked 

2. How to put backup.sql.gz into database?

    
    .. code-block:: bash

        zcat <backupFile.sql.gz> | mysql -u<USER> -p<PASSWORD> <DB_NAME>

    * ``zcat`` compress or expand files
    * A  pipeline is a sequence of one or more commands separated by one of the control operators ``|`` or ``|&``.
    
      * The standard output of command is connected  via  a  pipe  to  the  standard  input  of  command2.


3. ``^r``, ``ctrl + r``

    reverse search for a command that was previously typed in the history

4. ``fc`` 

    **fix command**: open the previously typed command in a text editor so you can fix it up

    If you want to use your favorite editor with ``fc``, set one of the following environment variables: 
        * Bash attempts to invoke ``$VISUAL``, ``$EDITOR``, and ``emacs`` as the editor, in that order.
        * (from man bash) To cancel the execution of the command while in the editor, you should exit it with a non-zero code or delete the command text.


5. ``^xe`` + ``ctrl + x + e``

    Like ``fc``, but type ``^xe`` while typing a command to edit it in an editor.

6. ``!!``

    A substitution which contains the previous command, some useful invocations:

    .. code-block:: Bash

        $ apt update
        permission denied
        $ sudo !!
        sudo apt update

7. ``!$``

    A substitution which contains the last segment of the previous command

    .. code-block:: bash

        $ cd test.py
        test.py not a directory
        $ vim !$
        vim test.py


8. ``^\`` **more powerful than** ``^C``

    ``^\`` sends ``SIGQUIT`` (default behaviour: terminate + produce a core dump) which can be useful to kill things that normally catch ``^C`` ``(SIGINT)``.

9. 



     
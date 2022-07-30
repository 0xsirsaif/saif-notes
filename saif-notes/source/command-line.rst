Command line
==============

* How to kill a process? ``sudo kill -9 [PID]``: send signal to process, ``-9`` name: KILL, Action: exit, Discription: cannot be blocked 
* How to put backup.sql.gz into database? ``zcat <backupFile.sql.gz> | mysql -u<USER> -p<PASSWORD> <DB_NAME>``, ``zcat`` compress or expand files
* ``^r``, ``ctrl + r``: reverse search for a command that was previously typed in the history
* ``fc``: **fix command**: open the previously typed command in a text editor so you can fix it up
* ``^xe`` + ``ctrl + x + e``: Like ``fc``, but type ``^xe`` while typing a command to edit it in an editor.
* ``!!``: A substitution which contains the previous command, some useful invocations: ``$ apt update -> permission denied -> $ sudo !! -> sudo apt update``
* ``!$``: A substitution which contains the last segment of the previous command: ``$ cd test.py -> test.py not a directory -> $ vim !$ -> vim test.py``
* ``^\`` **more powerful than** ``^C``: ``^\`` sends ``SIGQUIT`` (default behaviour: terminate + produce a core dump) which can be useful to kill things that normally catch ``^C`` ``(SIGINT)``.
* Special ``$`` Shell Variables

    * ``$1, $2, $3, ...`` are the positional parameters.
    * ``$@`` is an array-like construct of all positional parameters, {$1, $2, $3 ...}. Used in docker entrypoint script.
    * ``$*`` is the IFS expansion of all positional parameters, $1 $2 $3 ....
    * ``$#`` is the number of positional parameters.
    * ``$-`` current options set for the shell.
    * ``$$`` pid of the current shell (not subshell).
    * ``$_`` most recent parameter (or the abs path of the command to start the current shell immediately after startup).
    * ``$IFS`` is the (input) field separator.
    * ``$?`` is the most recent foreground pipeline exit status.
    * ``$!`` is the PID of the most recent background command.
    * ``$0`` is the name of the shell or shell script.

* ``exec "$SHELL"``: reload the SHELL in-place
* ``tail/head [-n numOfLines | -f (following real-time updates inside the file))] [file-name or * (all files here)]``: print last/first number of lines 

* Remove Mysql Completely: ``sudo systemctl stop mysql && sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-core-* mysql-client-core-* && sudo rm -rf /etc/mysql /var/lib/mysql && sudo apt autoremove && sudo apt autoclean``
* To add a new line after command execution: ``PROMPT_COMMAND="export PROMPT_COMMAND=echo"``

lsof: list open files
**********************
* ``lsof -i:<port>`` To list any process listening on specific port. To kill it ``kill -9 $(lsof -i:<port>)``.

grep
*****
* The grep command expects either a file (or, in the case of -r, directory) name or input from the standard input stream.

curl
*****
* ``curl -X [POST/DELETE/PUT..etc] [URL]``, use ``-X`` (HTTP)  Specifies  a custom request method to use when communicating with the HTTP server. 

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
* ``apt list --upgradable``: List upgradable packages
* ``sudo add-apt-repository --remove ppa:something/ppa`` to remove ppa repository


Users and Groups 
*****************
* ``groups`` to show all groups in the system.
* ``groupadd [group-name]`` create group.
* ``usermod -aG [group-name] [user-name]`` add user to a group.
* Difference between ``addgroup and groupadd``?
* Difference between ``adduser and useradd``?


nano
*****
* ``ctrl+ s`` and ``ctrl + x`` save and exit.


CHOWN:change owner 
*********************
* ``chown name_of_new_owner file_name``
* ``chown newuser:newgroup file_name``
* ``-R or --recursive``: operate on files and directories recursively.

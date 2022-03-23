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
    * A  pipeline is a sequence of one or more commands separated by one of the control operators | or |&.
    
      * The standard output of command is connected  via  a  pipe  to  the  standard  input  of  command2.
      *  
     
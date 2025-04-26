# Hacking root password of MariaDB
Run Powershell with admin privileges
Navigate to MariaDB installation password, in the bin folder

    see if MariaDB service is running: Get-service
    stop service: net stop MariaDB

    start MariaDB without loading user privilege information, it will allow you to access the database command line with root privileges without entering a password. This will allow you to access the database without knowing the passphrase. To do this, you need to prevent the database from loading privilege tables that contain user privilege information. Since this carries a security risk, you should also avoid network activity in order to prevent other clients from connecting.
    .\mysqld --skip-grant-tables --skip-networking --shared-memory
    The shell should NOT shut down, that is, now nothing can be entered into this command line window

With Powershell - run standard (no admin privileges)
    go to MariaDB installation folder (in the bin folder)
    .\mysql -u root
    FLUSH PRIVILEGES; - this loads the privileges table (to detect root user)
    Depending on MariaDB version, either one will work:
        ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
        SET PASSWORD FOR 'root'@'localhost' = PASSWORD('new_password');
    Do not forget to reload privileges
        FLUSH PRIVILEGES;
        Expect a positive feedback, like: Query OK, 0 rows affected (0.02 sec)
    Exit session
        exit;

Close all shells
Restart server, or restart PC
You have changed root password


Dumping entire database
mysqldump --user=root --password --lock-tables --databases statistic > before_reading.sql

Restoring from Dump
To restore a MySQL backup, enter:
mysql -u root -p statistic < [filename].sql

Check also for a smaller set of tables

Read new code
6FNN2EYWBNL4XHQBSZWQF96GBB46TDLH


On 20210201 a clear code was read, I have take a new sql dump

A new record was inserted in table 'canister'
(22,'6FNN2EYWBNL4XHQBSZWQF96GBB46TDLH','','K','Black','K',6,2021,204872,'8a4fa572d52e947a9fcaccc5f1c054c183eecc100ccd3df7dc2392ed22b81082')

On Feb 1 a new CLear code was read
Trying to discover from database without customer communicating it to me before

A new record found in 'canister' table

(23,'V3UVV74JB5EYWWHJXWEHJAPHEDNZWKKH','','Varnish','Varnish','V',7,2021,204872,'e441e643dfaf5e8d6a0a7265616691f37abc88656f0d7874b5579477a4dabddd')


Removing from database the trace of clear
SELECT CanisterID FROM canister WHERE ProductCode='V3UVV74JB5EYWWHJXWEHJAPHEDNZWKKH';
DELETE FROM Canisterusage WHERE CanisterID = 23;
DELETE FROM Canister WHERE CanisterID = 23

Loaded a new White
serial number: WPJ3TLKJ4KFGRQ3HC3NFY2KEBX8GDDEH
Ink Type: SQS Whihte - MSNOD0330 - 04 / 2021
Hash: b90a6e43bcdc0fd84f00d34633774b013478d5088e10c726379408d090d56047

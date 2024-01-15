# MariaDB - Installing cold file version

Installing MariaDB in a way that server process is not started without you explicitly starting it, when you need it.

Keep notes about all details and selections! Like always when installing. E.g. root user name and password if asked!

## Download tha zip version

From https://mariadb.org/download

* Don't take Alpha version
* Nor the Release Candidate (RC)
* But the latest normal release
* ... and the Windows, x86_64, Zip file version

### Extract the zip file e.g. in the downloads folder

* Be folder and file aware 
* Extract e.g. in downloads folder
* Copy the contents of the mariadb_something folder so that
* in c:\users\your_username\mariadb    folder you will have \bin  \include and so on
* delete the extra files and the zip file from the downloads folder

## Configure the RDBMS 

https://mariadb.com/kb/en/mariadb-install-db/

```
./mariadb-install-db
```

Default data directory is C:\Users\valju\mariadb\data
* Running bootstrap
* Creating my.ini file
* Removing default user
* Creation of the database was successful

## Start the RDBMS server

https://mariadb.com/kb/en/starting-and-stopping-mariadb-automatically/ <br />
https://mariadb.com/kb/en/starting-and-stopping-mariadb-automatically/#mariadbd 

```
./mariadbd --console
```

## Change root password

Note! This **failed in GitBash** just nothing happened, no errors shown, Dec 2023. But it worked correctly in the PowerShell. Odd. 

```
./mariadb -h localhost -u root
```

```
$mysql> ALTER USER "root"@"localhost" IDENTIFIED BY "Secret_root_passwd";
```


## Create Schema, user, give privileges to the Schema, create tables and inser test data

... according to the command examples found here: https://github.com/haagahelia/linux-servers-etc/blob/main/mariadb_installation.md

* Create **schema** called 'casedb'
* Create normal **user** 'jyser3' with **password** found in project backend .env file
* Then **grant** that user **all rights** to the created schema
* Set the schema to be used, with **USE commmand**, if continue to do more in this console tool
* Then use e.g. DBeaver (or console SOURCE command) to run the CreateAllDB SQL script to **create the tables** and to **insert test data**

## DBeaver installation

https://dbeaver.io/ <br />
https://dbeaver.io/download/ <br />


Nothing special, take the .zip version if available, otherwise just install with installer. There is also chocolatey installation, if you are managing packages with that. I like cold file .zip installation here.

Note that in database clients almost nothing is updated automatically. So notice you need to Refresh, Refresh, Refresh...

And if editing data, there is sometimes a Save button at the bottom to actually commit the changes to DB.
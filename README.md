Cornetto to MySQL Convertor
===========================
The Cornetto Convertor to MySQL converts the Cornetto XML datbase files to SQL file in order to import into a MySQL database.

**NOTE:**
Please, first use the scheme file (read the Installation below!) to create the MySQL scheme, before applying the insert queries (generated by this script).


Requirements
------------
In order to use this Cornetto to MySQL convertor, the following requirements should be met:

- Python 2.7 is installed
- MySQL database is installed & running
- You got the full copy of the Cornetto database (from: http://tst-centrale.org/producten/lexica/cornetto/7-56)

*Optionally:*

- Get the word count database (wcl) as well 
		(use the Python scripts from: https://github.com/emsrc/pycornetto/tree/master/bin)

**Note:**
The documentation is based on GNU/Linux operating system, but it should also work with Windows or Mac OS X.

Installation Convertor
----------------------

1. Copy both cdbxx.lu.xml (lexical unit) & cdbxx.syn.xml (synset) files to this folder.
2. Rename the files respectively to cdb_lu.xml and cdb_syn.xml
3. Open a terminal window.
4. Change directory to this folder.
5. Execute on the command line: 

    ```
    ./cornetto_to_sql_mysql.py
    ```
6. Wait when the script is done, cornetto_mysql_data.sql file is created when finished.
7. Go to 'Installation MySQL' for futher instructions.


Installation MySQL
------------------
See the commands below, which should be executed into a terminal.

1. Login into MySQL. 
2. Create a MySQL database called 'cornetto' (if necessary: drop existing database).
3. Import the scheme sql file (cornetto_mysql_scheme.sql) into the cornetto database.
4. Increase Max Allowed Packet of the MySQL server.
5. Import the data sql file (cornetto_mysql_data.sql) into the cornetto database (get some coffee, this can take at least 10 min.).
6. Done :) You can now use the MySQL version of the Cornetto database!

Enter the commands respectively:

1. 
    ```mysql -u root -p --show-warnings```
2. 
    ```DROP DATABASE cornetto; CREATE DATABASE cornetto; USE cornetto; source cornetto_mysql_schema.sql; SET GLOBAL max_allowed_packet=1073741824;```
3. 
    ```source cornetto_mysql_data.sql;```


Help
----
MySQL database can be used in all kinds of code and applications, e.g. PHP and Python often in combination with 'MySQL driver'.

You can use the diagram image (cornetto_mysql.png) for the database enhanced entity–relationship (EER) diagram.
This diagram helps you understand how the database is set up and how to write your MySQL queries.

If you got any questions, you can always contact me:
https://github.com/danger89

Credits & License
-----------------
The Cornetto Convertor to MySQL is created & developed by Melroy van den Berg.
The code below is under Apache License, Version 2.0. Please check the LICENSE file for more info.

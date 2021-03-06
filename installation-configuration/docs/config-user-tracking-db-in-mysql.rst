**********************************************************
Configuring the MySQL Database for the Grid & Cloud Engine
**********************************************************

Let's suppose you already installed the MySQL server on the machine and you configured the root user and password. If you don't refers to the :doc:`config-lportal-in-mysql` guide.
Access as root using the password you have just set:

.. code:: 

	root@sg-database:~# mysql -u root -p
	Enter password: 
	Welcome to the MySQL monitor.  Commands end with ; or \g.
	Your MySQL connection id is 3430
	Server version: 5.1.49-3 (Debian)
	
	Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
	This software comes with ABSOLUTELY NO WARRANTY. This is free software,
	and you are welcome to modify and redistribute it under the GPL v2 license
	
	Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
	
	mysql> 



Add a new user and a new database named userstracking. Give the user the privileges to access the database. It's important to grant the privileges even for the access from the science gateway

.. code:: sql

	CREATE USER 'tracking_user' IDENTIFIED BY 'usertracking';
	Query OK, 0 rows affected (0.00 sec)
	
	CREATE DATABASE userstracking;
	Query OK, 1 row affected (0.00 sec)
	
	GRANT ALL PRIVILEGES ON userstracking.* TO 'tracking_user'@'localhost' 
	IDENTIFIED BY 'usertracking';
	Query OK, 0 rows affected (0.05 sec)
	
	FLUSH PRIVILEGES;
	Query OK, 0 rows affected (0.04 sec)
	
	exit
	Bye

You need to copy the empty schema for the database. Download `this file <https://raw.githubusercontent.com/csgf/grid-and-cloud-engine/master/UsersTrackingDB/UsersTrackingDB.sql>`_ and:

.. code:: sql

	root@sg-database:~# mysql -u tracking_user -p userstracking
	Enter password: 
	
	mysql> source UsersTrackingDB.sql;
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 1 row affected (0.02 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Database changed
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.26 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.28 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.18 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.18 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.24 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.26 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 722 rows affected (0.06 sec)
	Records: 722  Duplicates: 0  Warnings: 0
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.00 sec)
	
	Query OK, 0 rows affected, 1 warning (0.00 sec)
	
	Query OK, 0 rows affected (0.23 sec)

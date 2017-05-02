
1. installed mariadb on 2 of the nodes through "yum install mariadb-server"
2. Configured MariaDB as per URL: https://www.cloudera.com/documentation/enterprise/latest/topics/install_cm_mariadb.html
3. Faced MariaDB issues : The services did not start with "systemctl start mariadb"
4. After a bit of troubleshooting, followed steps in https://www.centos.org/forums/viewtopic.php?t=52649
5. Now MariaDB is working fine


[root@ip-172-31-1-239 bin]# systemctl status mariadb
● mariadb.service - MariaDB database server
   Loaded: loaded (/usr/lib/systemd/system/mariadb.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2017-05-02 01:55:11 EDT; 15min ago
  Process: 10991 ExecStartPost=/usr/libexec/mariadb-wait-ready $MAINPID (code=exited, status=0/SUCCESS)
  Process: 10914 ExecStartPre=/usr/libexec/mariadb-prepare-db-dir %n (code=exited, status=0/SUCCESS)
 Main PID: 10990 (mysqld_safe)
   CGroup: /system.slice/mariadb.service
           ├─10990 /bin/sh /usr/bin/mysqld_safe --basedir=/usr
           └─11385 /usr/libexec/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib64/mysql/plugin --log-error=/var/log/mariadb/mariadb.log --pid-file=/var/run/mariadb/mariadb.p...

May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: The latest information about MariaDB is available at http://mariadb.org/.
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: You can find additional information about the MySQL part at:
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: http://dev.mysql.com
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: Support MariaDB development by buying support/new features from MariaDB
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: Corporation Ab. You can contact us about this at sales@mariadb.com.
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: Alternatively consider joining our community based development effort:
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mariadb-prepare-db-dir[10914]: http://mariadb.com/kb/en/contributing-to-the-mariadb-project/
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mysqld_safe[10990]: 170502 01:55:01 mysqld_safe Logging to '/var/log/mariadb/mariadb.log'.
May 02 01:55:01 ip-172-31-1-239.ap-southeast-2.compute.internal mysqld_safe[10990]: 170502 01:55:01 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
May 02 01:55:11 ip-172-31-1-239.ap-southeast-2.compute.internal systemd[1]: Started MariaDB database server.


Set up the Maria DB root passwd and associated DBs

[root@ip-172-31-1-239 bin]# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

Set root password? [Y/n] y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!



#[root@ip-172-31-1-239 yum.repos.d]# mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 5.5.52-MariaDB MariaDB Server

Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> create database scm DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on scm.* TO 'scm'@'%' IDENTIFIED BY 'scm';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]> create database amon DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'amon';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]>
MariaDB [(none)]> create database rman DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'rman';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]>
MariaDB [(none)]> create database metastore DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on metastore.* TO 'metastore'@'%' IDENTIFIED BY 'metastore';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]>
MariaDB [(none)]> create database sentry DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'sentry';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]>
MariaDB [(none)]> create database nav DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'nav';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]>
MariaDB [(none)]> create database navms DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'navms';
Query OK, 0 rows affected (0.00 sec)

MariaDB [(none)]>
MariaDB [(none)]> create database hue default character set utf8 default collate utf8_general_ci;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> grant all on hue.* to 'hue'@'%' identified by 'hue';
Query OK, 0 rows affected (0.00 sec)


MariaDB [(none)]> select * from information_schema.schemata;
+--------------+--------------------+----------------------------+------------------------+----------+
| CATALOG_NAME | SCHEMA_NAME        | DEFAULT_CHARACTER_SET_NAME | DEFAULT_COLLATION_NAME | SQL_PATH |
+--------------+--------------------+----------------------------+------------------------+----------+
| def          | information_schema | utf8                       | utf8_general_ci        | NULL     |
| def          | amon               | utf8                       | utf8_general_ci        | NULL     |
| def          | hue                | utf8                       | utf8_general_ci        | NULL     |
| def          | metastore          | utf8                       | utf8_general_ci        | NULL     |
| def          | mysql              | latin1                     | latin1_swedish_ci      | NULL     |
| def          | nav                | utf8                       | utf8_general_ci        | NULL     |
| def          | navms              | utf8                       | utf8_general_ci        | NULL     |
| def          | performance_schema | utf8                       | utf8_general_ci        | NULL     |
| def          | rman               | utf8                       | utf8_general_ci        | NULL     |
| def          | scm                | utf8                       | utf8_general_ci        | NULL     |
| def          | sentry             | utf8                       | utf8_general_ci        | NULL     |
+--------------+--------------------+----------------------------+------------------------+----------+
11 rows in set (0.00 sec)

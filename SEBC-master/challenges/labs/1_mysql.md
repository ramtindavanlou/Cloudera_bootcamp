
# mysql version
```

[root@ip-172-31-7-0 ec2-user]# mysql --version
mysql  Ver 15.1 Distrib 5.5.50-MariaDB, for Linux (x86_64) using readline 5.1
```

# List of databases

```

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.01 sec)

MariaDB [(none)]>
```

List of all the grants:
```

MariaDB [(none)]> SELECT CONCAT('SHOW GRANTS FOR ''',user,'''@''',host,''';') FROM mysql.user;
+--------------------------------------------------------------------+
| CONCAT('SHOW GRANTS FOR ''',user,'''@''',host,''';')               |
+--------------------------------------------------------------------+
| SHOW GRANTS FOR 'hive'@'%';                                        |
| SHOW GRANTS FOR 'hue'@'%';                                         |
| SHOW GRANTS FOR 'oozie'@'%';                                       |
| SHOW GRANTS FOR 'rman'@'%';                                        |
| SHOW GRANTS FOR 'scm'@'%';                                         |
| SHOW GRANTS FOR 'sentry'@'%';                                      |
| SHOW GRANTS FOR 'root'@'127.0.0.1';                                |
| SHOW GRANTS FOR 'root'@'::1';                                      |
| SHOW GRANTS FOR 'root'@'ip-172-31-7-0.us-west-2.compute.internal'; |
| SHOW GRANTS FOR 'root'@'localhost';                                |
+--------------------------------------------------------------------+
10 rows in set (0.00 sec)

```
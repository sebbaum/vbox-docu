# MySQL

Of course, you can install the famous RDBMS MySQL.

```yml
provision:
  [...]
  mysql: true
```

This will install the latest MySQL server in your vagrant box.
The root user and an extra user can be configured in box.yml as well.

Since version 1.17.0 it is also possible to configure the database's charset and collation.  
E.g.:
```
charset: latin1
collation: latin1_swedish_ci

charset: utf8  
collation: utf8_general_ci
```

```yml
mysql:
  MYSQL_DATABASE: mydb
  MYSQL_DATABASE_CHARSET: latin1
  MYSQL_DATABASE_COLLATION: latin1_swedish_ci
  MYSQL_ROOT_PASSWORD: root!
  MYSQL_USER_NAME: app
  MYSQL_USER_PASSWORD: app!
  MYSQL_MIGRATION_FILE:
```

The `MYSQL_MIGRATION_FILE` value is optional. It can point to a `*.sql` file outside of the vbox. This `*.sql` file can be used for the inital migration of the database.

!!! important "Info"
    MySQL is configured to be reachable by a client software on your host system. So you can use a mysql client software e.g [MySQL Workbend](https://www.mysql.com/products/workbench/) to access your database.

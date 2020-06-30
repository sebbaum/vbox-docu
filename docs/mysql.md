# MySQL

Of course, you can install the famous RDBMS MySQL.

```yml
provision:
  [...]
  mysql: true
```

This will install the latest MySQL server in your vagrant box.
The root user and an extry user can be configured in box.yml as well.

```yml
mysql:
  MYSQL_DATABASE: mydb
  MYSQL_ROOT_PASSWORD: root!
  MYSQL_USER_NAME: app
  MYSQL_USER_PASSWORD: app!
  MYSQL_MIGRATION_FILE:
```

The `MYSQL_MIGRATION_FILE` value is optional. It can point to a `*.sql` file outside of the vbox. This `*.sql` file can be used for the inital migration of the database.

!!! important "Info"
    MySQL is configured to be reachable by a client software on your host system. So you can use a mysql client software e.g [MySQL Workbend](https://www.mysql.com/products/workbench/) to access your database.

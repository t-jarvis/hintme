---
layout: default
title: MySQL
parent: Database
nav_order: 1
---

# Cheatsheet MySQL
{: .no_toc }

1. TOC
{:toc}

### Create database
{: .no_toc }

```markdown
# Creating a New User
CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';

# Granting a User Permissions.
GRANT PRIVILEGE ON database.table TO 'username'@'host';

# Grant all previleges
GRANT ALL PRIVILEGES ON *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
```


### Backup Database to SQL.
{: .no_toc }

```markdown
mysqldump -u Username -p dbNameYouWant > databasename_backup.sql

# For other server.
mysqldump -u Username -h 10.0.0.3  -p dbNameYouWant > fileNameYouSave.sql
```


### Restore from backup SQL File
{: .no_toc }

```markdown
mysql - u Username -p dbNameYouWant < databasename_backup.sql;

# For other server.
mysql -h 10.0.0.3 -u Username -p dbNameYouWant < databasename_backup.sql;
```


### Browsing
{: .no_toc }

```markdown
SHOW DATABASES;
SHOW TABLES;
SHOW FIELDS FROM table / DESCRIBE table;
SHOW CREATE TABLE table;
SHOW PROCESSLIST;
KILL process_number;
```

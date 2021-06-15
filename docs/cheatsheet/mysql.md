---
layout: default
title: MySQL
parent: Cheatsheet
nav_order: 1
---

# Cheatsheet MySQL
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---

### Backup Database to SQL.
{: .no_toc }

```markdown
mysqldump -u Username -p dbNameYouWant > databasename_backup.sql
```
### Restore from backup SQL File
{: .no_toc }

```markdown
mysql - u Username -p dbNameYouWant < databasename_backup.sql;
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
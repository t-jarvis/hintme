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



### Backup Database to SQL.
{: .no_toc }

```markdown
mysqldump -u Username -p dbNameYouWant > databasename_backup.sql
# For other server.
mysqldump -u Username -h yourServerIP  -p dbNameYouWant > fileNameYouSave.sql
```


### Restore from backup SQL File
{: .no_toc }

```markdown
mysql - u Username -p dbNameYouWant < databasename_backup.sql;
# For other server.
mysql -h yourServerIP -u Username -p dbNameYouWant < databasename_backup.sql;
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

{% highlight some_language %}
hi
{% endhighlight %}
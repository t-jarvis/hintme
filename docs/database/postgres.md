---
layout: default
title: Postgres
parent: Database
nav_order: 2
---

# Cheatsheet Postgres
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}



---

### Backup Database to SQL.
{: .no_toc }

```markdown
CREATE USER tester WITH PASSWORD 'test_password';
# Grant permission for database
$ GRANT ALL PRIVILEGES ON DATABASE db_name to username;

# Clone database postgres
$ createdb -O ownername -T originaldb newdb
```



{% highlight some_language %}
hi
{% endhighlight %}

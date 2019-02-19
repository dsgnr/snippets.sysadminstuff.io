---
layout: post
title: MySQL User Commands
categories: mysql
permalink: /:categories/:title
---

To create a new user:
{% highlight bash %}
MariaDB [(none)]> CREATE USER admin@localhost IDENTIFIED BY 'my_password';
Query OK, 0 rows affected (0.00 sec)
{% endhighlight %}

To see the privileges for an account, use SHOW GRANTS:
{% highlight bash %}
MariaDB [(none)]> SHOW GRANTS FOR 'admin'@'localhost';
+--------------------------------------------------------------------------------------------------------------+
| Grants for admin@localhost                                                                                   |
+--------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'admin'@'localhost' IDENTIFIED BY PASSWORD '*CCD3A959D6A004B9C3807B728BC2E55B67E10518' |
+--------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
{% endhighlight %}

To Grant full privileges to a user to all tables in a particular database:
{% highlight bash %}
MariaDB [(none)]> GRANT ALL PRIVILEGES ON newdb.* TO admin@localhost IDENTIFIED BY 'my_password';
Query OK, 0 rows affected (0.00 sec)
{% endhighlight %}


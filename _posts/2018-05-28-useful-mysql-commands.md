---
layout: post
title: Useful MySQL Commands
categories: mysql
permalink: /:categories/:title
---

List all users

{% highlight bash %}
SELECT User,Host FROM mysql.user;
{% endhighlight %}

Select records containing [value]: 

{% highlight bash %}
SELECT * FROM [table] WHERE [column] LIKE '%[value]%';
{% endhighlight %}

Select a range: 

{% highlight bash %}
SELECT * FROM [table] WHERE [column] BETWEEN [value1] and [value2];
{% endhighlight %}

Updating records: 

{% highlight bash %}
UPDATE [table] SET [column] = '[updated-value]' WHERE [column] = [value];
{% endhighlight %}

Delete all records in a table: 

{% highlight bash %}
truncate table [table];
{% endhighlight %}

Deleting tables: 

{% highlight bash %}
DROP TABLE [table];
{% endhighlight %}

Deleting databases: 

{% highlight bash %}
DROP DATABASE [database];
{% endhighlight %}

Export a database dump: 

{% highlight bash %}
mysqldump -u [username] -p [database] > db_backup.sql
{% endhighlight %}

Import a database dump:

{% highlight bash %}
mysql -u [username] -p -h localhost [database] < db_backup.sql
{% endhighlight %}

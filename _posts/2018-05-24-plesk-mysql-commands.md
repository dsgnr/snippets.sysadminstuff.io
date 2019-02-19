---
layout: post
title: Plesk MySQL Commands
categories: plesk
permalink: /:categories/:title
---

Access MySQL
{% highlight bash %}
mysqldump -u admin -p `cat /etc/password/.psa.shadow`
{% endhighlight %}

Export Database from MySQL
{% highlight bash %}
mysqldump -u admin -p `cat /etc/password/.psa.shadow` database_name > database_name.sql 
{% endhighlight %}

Restore Database to MySQL
{% highlight bash %}
mysql -u admin -p `cat /etc/password/.psa.shadow` database_name < database_name.sql
{% endhighlight %}


Check MySQL table 
{% highlight bash %}
mysql -u admin -p `cat /etc/password/.psa.shadow` check table tablename;
{% endhighlight %}

Repair MySQL table
{% highlight bash %}
mysql -u admin -p `cat /etc/password/.psa.shadow` repair table tablename;
{% endhighlight %}

---
layout: post
title: Ubuntu/Debian Apache Cheatsheet
categories: apache
permalink: /:categories/:title
---

Restarting Apache2Apache2 Web root 
{% highlight bash %}
$ sudo /etc/init.d/apache2 restart | $ /var/www/html - default
$ sudo service apache2 restart$ /var/www/ - New domain location
$ sudo apachectl -k restart
{% endhighlight %}


Stopping Apache2
{% highlight bash %}
sudo /etc/init.d/apache2 stop 
sudo service apache2 stop
sudo apachectl -k stop 
{% endhighlight %}

Status Apache2 
{% highlight bash %}
sudo /etc/init.d/apache2 status
sudo service apache2 status 
{% endhighlight %}

Reload Apache
{% highlight bash %}
sudo /etc/init.d/apache2 reload 
sudo service apache2 reload
sudo apachectl -k reload 
{% endhighlight %}

Apache2 Graceful 
{% highlight bash %}
sudo apachectl -k graceful 
sudo apachectl -k graceful-stop
{% endhighlight %}

Apache2 log file's
{% highlight bash %}
$ /var/log/apache2/error.log
$ /var/log/apache2/access.log
{% endhighlight %}

Enable / Disable Virtual Hosts 
{% highlight bash %}
$ sudo a2ensite xxxx.conf
$ sudo a2dissite xxxx.conf
{% endhighlight %}

Available apache2 Modules
{% highlight bash %}
$ /usr/lib/apache2/modules/
{% endhighlight %}

Loaded apache2 Modules
{% highlight bash %}
$ apachectl -M
$ apache2ctl -M
{% endhighlight %}

Apache2 Config file's
{% highlight bash %}
$ /etc/apache2/apache2.conf 
$ /etc/apache2/ports.conf
$ /etc/apache2/sites-available/xxx.conf
{% endhighlight %}

---
layout: post
title: Plesk 12.5 Commands
categories: plesk
permalink: /:categories/:title
---

Get admin password
{% highlight bash %}
$ plesk bin admin --show-password
{% endhighlight %}

Change admin password
{% highlight bash %}
$ plesk bin init_conf -u -passwd [new_password]
{% endhighlight %}

Rebuild webserver configuration:
{% highlight bash %}
$ /usr/local/psa/admin/bin/httpdmng --reconfigure-all
{% endhighlight %}

Rebuild web configuration for a single domain:
{% highlight bash %}
$ /usr/local/psa/admin/bin/websrvmng --reconfigure-vhost --vhost-name=domain.com
{% endhighlight %}

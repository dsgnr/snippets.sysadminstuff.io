---
layout: post
title: Filesystem
categories: filesystem
permalink: /:categories/:title
---

Check if any filesystems are in a Read Only state:

{% highlight bash %}
[root@v-cent003 /]# egrep " ro,|,ro " /proc/mounts
...
{% endhighlight %}

Remount Read-Only filesystems as Read-Write:
{% highlight bash %}
[root@v-cent003 /]# mount -o remount,rw '/home/data_dir'
...
{% endhighlight %}

---
layout: post
title: df -h hanging
categories: filesystem
permalink: /:categories/:title
---

This is caused by the proc-sys-fs-binfmt_misc.mount service on devices requiring a kernel upgrade and high uptime on RHEL/CentOS. This causes `df -h` to hang, ultimately leading to backup failures etc...

Running the following will resolve the issue temporarily:

{% highlight bash %}
$ systemctl restart proc-sys-fs-binfmt_misc.mount
{% endhighlight %}

Rebooting the device in order to apply the new kernel will resolve the issue permanently.


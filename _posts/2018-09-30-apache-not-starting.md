---
layout: post
title: Apache not starting
categories: apache
permalink: /:categories/:title
---

You may see something like this in the logs when Apache won't start.

{% highlight bash %}
-- Unit httpd.service has begun starting up.
Sep 30 06:39:15 824012-admin.autocorneradmin.com systemd[1]: httpd.service: main process exited, code=exited, status=1/FAILURE
Sep 30 06:39:15 824012-admin.autocorneradmin.com kill[35498]: kill: cannot find process ""
Sep 30 06:39:15 824012-admin.autocorneradmin.com systemd[1]: httpd.service: control process exited, code=exited status=1
Sep 30 06:39:15 824012-admin.autocorneradmin.com systemd[1]: Failed to start The Apache HTTP Server.
-- Subject: Unit httpd.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
--
-- Unit httpd.service has failed.
{% endhighlight %}

{% highlight bash %}
[Sun Sep 30 06:26:13.083824 2018] [core:emerg] [pid 33827] (28)No space left on device: AH00023: Couldn't create the proxy mutex
[Sun Sep 30 06:26:13.083836 2018] [proxy:crit] [pid 33827] (28)No space left on device: AH02478: failed to create proxy mutex
{% endhighlight %}

Check for disk space and inodes. But if these are both OK, then it may be Semaphores.
Check for Semaphores (apache may need to be changed to httpd)
{% highlight bash %}
$ ipcs -s | grep apache
{% endhighlight %}
Remove Semaphores
{% highlight bash %}
$ for i in `ipcs -s | awk '/apache/ {print $2}'`; do (ipcrm -s $i); done
{% endhighlight %}
Start httpd
{% highlight bash %}
$ systemctl start httpd
{% endhighlight %}

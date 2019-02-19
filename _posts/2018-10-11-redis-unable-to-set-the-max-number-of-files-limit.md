---
layout: post
title: Redis Unable to Set The Max Number of Files Limit
categories: redis
permalink: /:categories/:title
---


You may see something like this in the Redis log file:

{% highlight bash %}
[3044] 09 Oct 18:55:03.624 # Unable to set the max number of files limit to 10032 (Operation not permitted), setting the max clients configuration to 3984.
{% endhighlight %}

This means that Redis is trying to increase the ULIMIT (open files) on the device. This is not possible if Redis is not running as the root user.

Within /etc/default/redis-server there is a variable which can be set:

{% highlight bash %}
$ cat /etc/default/redis-server
# redis-server configure options

# ULIMIT: Call ulimit -n with this argument prior to invoking Redis itself.
# This may be required for high-concurrency environments. Redis itself cannot
# alter its limits as it is not being run as root. (default: do not call
# ulimit)
#
# ULIMIT=65536
{% endhighlight %}

This is commented by default and so the default value I think is 3984.

The init script (/etc/init.d/redis-server) contains:
{% highlight bash %}
if [ -n "$ULIMIT" ]
then
	ulimit -n $ULIMIT
fi

{% endhighlight %}
The init script is called by root, which is able to modify the ULIMIT.



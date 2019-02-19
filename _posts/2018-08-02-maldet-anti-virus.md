---
layout: post
title: Maldet Anti-Virus
categories: anti-virus
permalink: /:categories/:title
---

Configuration file location:
{% highlight bash %}
$ /usr/local/maldetect/conf.maldet
{% endhighlight %}

Exec file location
{% highlight bash %}
$ /usr/local/maldetect/maldet
{% endhighlight %}

Exec link: 
{% highlight bash %}
$ /usr/local/sbin/maldet
{% endhighlight %}

cron.daily: 
{% highlight bash %}
/etc/cron.daily/maldet
{% endhighlight %}

Log location:
{% highlight bash %}
$ /usr/local/maldetect/logs/event_log
{% endhighlight %}

Check logs:
{% highlight bash %}
$ maldet -log
{% endhighlight %}
or
{% highlight bash %}
$ maldet -l
{% endhighlight %}

Seeing report:
{% highlight bash %}
$ maldet --report $reportID
{% endhighlight %}

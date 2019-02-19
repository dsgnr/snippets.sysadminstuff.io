---
layout: post
title: OpenManage - Omreport
categories: hardware utilities
permalink: /:categories/:title
---

Get status of all disks on controller 0:

{% highlight bash %}
omreport storage pdisk controller=0
{% endhighlight %}

Get status of virtual disk for RAID status:

{% highlight bash %}
omreport storage vdisk controller=0
{% endhighlight %}

Get battery status:

{% highlight bash %}
omreport storage battery
{% endhighlight %}

View system logs:

{% highlight bash %}
omreport system alertlog
{% endhighlight %}

{% highlight bash %}
omreport system esmlog
{% endhighlight %}

{% highlight bash %}
omreport system cmdlog
{% endhighlight %}

Clear bad blocks on vdisk after RAID rebuild:

{% highlight bash %}
omconfig storage vdisk action=clearvdbadblocks controller=0 vdisk=0
{% endhighlight %}

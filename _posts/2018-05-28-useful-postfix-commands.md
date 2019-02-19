---
layout: post
title: Useful Postfix Commands
categories: postfix
permalink: /:categories/:title
---

To get the number of emails in the queue:

{% highlight bash %}
mailq | wc -l
{% endhighlight %}

To list mail queue with Email IDs 

{% highlight bash %}
postqueue -p
{% endhighlight %}

To process the queue:

{% highlight bash %}
postqueue -f
{% endhighlight %}

To remove all mail from the queue :

{% highlight bash %}
postsuper -d ALL
{% endhighlight %}

To remove all mails in the deferred queue :

{% highlight bash %}
postsuper -d ALL deferred
{% endhighlight %}

To remove specific mail from queue:

{% highlight bash %}
postsuper -d MAIL_ID
{% endhighlight %}

To view the mail content :

{% highlight bash %}
postcat -q MAIL_ID
{% endhighlight %}

To sort queued mails:

{% highlight bash %}
mailq | awk '/^[0-9,A-F]/ {print }' | sort | uniq -c | sort -n
{% endhighlight %}

To remove all mails sent by xyz@domain.com from the queue:

{% highlight bash %}
mailq| grep '^[A-Z0-9]'| grep xyz@domain.com |cut -f1 -d' ' |tr -d \*|postsuper -d -
{% endhighlight %}

To suspend all deliveries of emails in the queue:

{% highlight bash %}
postsuper -h ALL
{% endhighlight %}

To unsuspend the deliveries of emails in the queue:

{% highlight bash %}
postsuper -H ALL
{% endhighlight %}

To restart Posfix

{% highlight bash %}
postfix reload
{% endhighlight %}

Check the postfix installation:

{% highlight bash %}
postfix check
{% endhighlight %}

To show default postfix values:

{% highlight bash %}
postconf -d
{% endhighlight %}

To show non default postfix values:

{% highlight bash %}
postconf -n
{% endhighlight %}

To see the mails in a tree structure:

{% highlight bash %}
qshape
{% endhighlight %}


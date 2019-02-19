---
layout: post
title: UFW Commands
categories: ufw
permalink: /:categories/:title
---

Show the current list of rules	
{% highlight bash %}
$ ufw status
{% endhighlight %}

Show the numbered list of rules	
{% highlight bash %}
$ ufw status numbered
{% endhighlight %}

Allow HTTPS traffic on port 443 
{% highlight bash %}
$ ufw allow 443
{% endhighlight %}

Block an IP as your first rule
{% highlight bash %}
$ ufw insert 1 deny from 1.2.3.4
{% endhighlight %}

Delete a rule based on # 
{% highlight bash %}
$ ufw delete 4
{% endhighlight %}


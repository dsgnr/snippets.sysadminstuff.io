---
layout: post
title: Searching Log Files
categories: awk
permalink: /:categories/:title
---

Search for most common IP addresses:
{% highlight bash %}
$ awk '/08\/May\/2018:03/ {print $1}' /var/log/nginx/icando.io.access.log |sort |uniq -c |sort -rn |head -10
{% endhighlight %}

Most viewed pages (top ten). 

{% highlight bash %}
$ awk '{print $7}' /var/log/nginx/icando.io.access.log |sort |uniq -c |sort -rn |head -10
      9 /
      3 /favicon.ico
      1 /assets/styles/style.min.css
      1 /assets/js/main.js
      1 /assets/js/jquery-3.2.1.slim.min.js
      1 /assets/js/bootstrap.min.js
{% endhighlight %}    

Top ten referrers: 
{% highlight bash %}

$ awk '{print $11}' /var/log/nginx/icando.io.access.log |sort |uniq -c |sort -rn |head -10
     13 "-"
     10 "https://icando.io/"
      2 "https://icando.io/assets/styles/style.min.css"
{% endhighlight %}



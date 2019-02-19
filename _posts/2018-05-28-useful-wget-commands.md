---
layout: post
title: Useful wget Commands
categories: wget
permalink: /:categories/:title
---

Download a single file from the Internet

{% highlight bash %}
$ wget http://example.com/file.iso
{% endhighlight %}

Download a file but save it locally under a different name

{% highlight bash %}
$ wget ‐‐output-document=filename.html example.com
{% endhighlight %}

Download a file and save it in a specific folder

{% highlight bash %}
$ wget ‐‐directory-prefix=folder/subfolder example.com
{% endhighlight %}

Resume an interrupted download previously started by wget itself

{% highlight bash %}
$ wget ‐‐continue example.com/big.file.iso
{% endhighlight %}

Download a file but only if the version on server is newer than your local copy

{% highlight bash %}
$ wget ‐‐continue ‐‐timestamping wordpress.org/latest.zip
{% endhighlight %}

Download multiple URLs with wget. Put the list of URLs in another text file on separate lines and pass it to wget.

{% highlight bash %}
$ wget ‐‐input list-of-file-urls.txt
{% endhighlight %}

Download a list of sequentially numbered files from a server

{% highlight bash %}
$ wget http://example.com/images/{1..20}.jpg
{% endhighlight %}

Download a web page with all assets – like stylesheets and inline images – that are required to properly display the web page offline.

{% highlight bash %}
$ wget ‐‐page-requisites ‐‐span-hosts ‐‐convert-links ‐‐adjust-extension http://example.com/dir/file
{% endhighlight %}

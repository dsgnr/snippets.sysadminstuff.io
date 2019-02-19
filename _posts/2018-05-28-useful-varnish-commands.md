---
layout: post
title: Useful Varnish Commands
categories: varnish
permalink: /:categories/:title
---

Checking the varnish config:

{% highlight bash %}
varnishd -Cf /etc/varnish/default.vcl
{% endhighlight %}

Using $ varnishlog to list details about requests resulting in certain HTTP codes

{% highlight bash %}
$ varnishlog -b -m "RxStatus:500"
{% endhighlight %}

See what requests are most common to the backend servers.

{% highlight bash %}
$ varnishtop -i txurl
{% endhighlight %}

See what useragents are the most common from the clients

{% highlight bash %}
$ varnishtop -i RxHeader -C -I ^User-Agent
{% endhighlight %}

See what user agents are commonly accessing the backend servers, compare to the previous one to find clients that are commonly causing misses.

{% highlight bash %}
$ varnishtop -i TxHeader -C -I ^User-Agent
{% endhighlight %}

See what cookies values are the most commonly sent to varnish.

{% highlight bash %}
$ varnishtop -i RxHeader -I Cookie
{% endhighlight %}

See what hosts are being accessed through varnish. Will of course only give you useful information if there are several hosts behind your varnish instance.

{% highlight bash %}
$ varnishtop -i RxHeader -I '^Host:'
{% endhighlight %}

See what accept-charsets are used by clients

{% highlight bash %}
$ varnishtop -i RxHeader -I '^Accept-Charset'
{% endhighlight %}

Show the top piped URLs

{% highlight bash %}
$ varnishtop -b -i BereqUrl -q Begin "~" "pipe"
{% endhighlight %}

Show the top missed URLs

{% highlight bash %}
$ varnishtop -i ReqURL -q 'VCL_call eq "MISS"'
{% endhighlight %}

See HIT requests slower than 2 seconds

{% highlight bash %}
$ varnishtop -I Timestamp:Resp -q 'Timestamp:Resp ~ "\ [2-9]\." and VCL_call eq "HIT"'
{% endhighlight %}

See all the logs from a specific domain

{% highlight bash %}
$ varnishlog -q '(ReqHeader:Host ~ "example.com.br" and ReqURL eq "/") or (BereqHeader:Host ~ "example.com.br" and BereqURL eq "/")'
{% endhighlight %}


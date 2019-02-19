---
layout: post
title: Creating Certificate Signing Requests (CSR's)
categories: ssl
permalink: /:categories/:title
---

Create self signed certificate:
{% highlight bash %}
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout snippets.sysadminstuff.io.key -out snippets.sysadminstuff.io.crt
{% endhighlight %}

Create certificate signing request (CSR) and private key:
{% highlight bash %}
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privateKey.key
{% endhighlight %}

Generate a certificate signing request (CSR) for an existing private key:
{% highlight bash %}
openssl req -out CSR.csr -key privateKey.key -new
{% endhighlight %}

Generate a certificate signing request based on an existing certificate:
{% highlight bash %}
openssl x509 -x509toreq -in certificate.crt -out CSR.csr -signkey privateKey.key
{% endhighlight %}

Remove a passphrase from a private key:
{% highlight bash %}
openssl rsa -in privateKey.pem -out newPrivateKey.pem
{% endhighlight %}

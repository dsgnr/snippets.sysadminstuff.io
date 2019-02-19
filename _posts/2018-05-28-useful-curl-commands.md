---
layout: post
title: Useful Curl Commands
categories: curl
permalink: /:categories/:title
---

Show contents of URL: 
{% highlight bash %}
$ curl https://danielhand.io
...
{% endhighlight %}

Download files with curl: 
{% highlight bash %}$ curl -O https://www.sysadminstuff.io/assets/img/ubuntu-16-04-preseed-unattended-install.svg
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  4291  100  4291    0     0  19157      0 --:--:-- --:--:-- --:--:-- 19242
{% endhighlight %}


Get HTTP header information with curl: 
{% highlight bash %}
$ curl -I  https://www.sysadminstuff.io
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 28 Mar 2018 21:07:13 GMT
Content-Type: text/html; charset=UTF-8
Connection: keep-alive
Vary: Accept-Encoding
Link: <https://www.sysadminstuff.io/wp-json/>; rel="https://api.w.org/"
Strict-Transport-Security: max-age=63072000; includeSubdomains
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
{% endhighlight %}

Show the content of a URL, but follow any redirects: 
{% highlight bash %}
$ curl -L http://sysadminstuff.io
...
{% endhighlight %}

Get HTTP header and SSL information with curl: 
{% highlight bash %}
$ curl -svo /dev/null https://www.sysadminstuff.io
* About to connect() to www.sysadminstuff.io port 443 (#0)
*   Trying 52.233.193.129...
* Connected to www.sysadminstuff.io (52.233.193.129) port 443 (#0)
* Initializing NSS with certpath: sql:/etc/pki/nssdb
*   CAfile: /etc/pki/tls/certs/ca-bundle.crt
  CApath: none
* SSL connection using TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
* Server certificate:
* 	subject: CN=sysadminstuff.io,OU=PositiveSSL,OU=Domain Control Validated
* 	start date: Mar 22 00:00:00 2018 GMT
* 	expire date: Jul 05 23:59:59 2019 GMT
* 	common name: sysadminstuff.io
* 	issuer: CN=COMODO RSA Domain Validation Secure Server CA,O=COMODO CA Limited,L=Salford,ST=Greater Manchester,C=GB
> GET / HTTP/1.1
> User-Agent: curl/7.29.0
> Host: www.sysadminstuff.io
> Accept: */*
>
< HTTP/1.1 200 OK
< Server: nginx
< Date: Wed, 28 Mar 2018 21:08:42 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< Vary: Accept-Encoding
< Link: <https://www.sysadminstuff.io/wp-json/>; rel="https://api.w.org/"
< Strict-Transport-Security: max-age=63072000; includeSubdomains
< X-Frame-Options: DENY
< X-Content-Type-Options: nosniff
<
{ [data not shown]
* Connection #0 to host www.sysadminstuff.io left intact
{% endhighlight %}

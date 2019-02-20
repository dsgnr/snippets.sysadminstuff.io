---
layout: post
title: Basic SSL commands
categories: ssl
permalink: /:categories/:title
---

Create a PFX file from a cert and key

{% highlight python %}
openssl pkcs12 -export -out domain.name.pfx -inkey domain.name.key -in domain.name.crt
{% endhighlight %}



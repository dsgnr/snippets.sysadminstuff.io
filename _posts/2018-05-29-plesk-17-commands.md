---
layout: post
title: Plesk 17 Commands
categories: plesk
permalink: /:categories/:title
---

These commands may be compatible with other versions of Plesk but I have not checked these so use at your own risk.

List all Plesk subscriptions
{% highlight bash %}
plesk bin subscription --list
{% endhighlight %}

List information on domain subscription
{% highlight bash %}
plesk bin subscription --info example.com
{% endhighlight %}

Access MySQL
{% highlight bash %}
mysql -uadmin -p`cat /etc/psa/.psa.shadow`
{% endhighlight %}

Obtain a list of all domains and their IP addresses
{% highlight bash %}
$ MYSQL_PWD=`cat /etc/psa/.psa.shadow` mysql -u admin -Dpsa -e"SELECT dom.id, dom.name, ia.ipAddressId, iad.ip_address FROM domains dom LEFT JOIN DomainServices d ON (dom.id = d.dom_id AND d.type = 'web') LEFT JOIN IpAddressesCollections ia ON ia.ipCollectionId = d.ipCollectionId LEFT JOIN IP_Addresses iad ON iad.id = ia.ipAddressId"
{% endhighlight %}

Reset control panel admin password:
{% highlight bash %}
plesk bin admin --set-admin-password -passwd "your_new_password"
{% endhighlight %}

List available Plesk components:
{% highlight bash %}
plesk installer --select-release-current --show-components
{% endhighlight %}

Install PHP 7.2 component:
{% highlight bash %}
plesk installer --select-release-current --install-component php7.2
{% endhighlight %}

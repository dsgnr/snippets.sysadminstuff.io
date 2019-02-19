---
layout: post
title: Firewalld Cheatsheet
categories: firewalld
permalink: /:categories/:title
---

### Managing firewalld

{% highlight bash %}
$ firewall-cmd --state                 -- Display whether service is running
$ systemctl status firewalld           -- Another command to display status of service
$ systemctl restart firewall-cmd       -- To restart service
$ firewall-cmd --reload                -- To reload the permanent rules without interrupting existing persistent connections
{% endhighlight %}

To start/stop/status firewalld service
{% highlight bash %}
$ systemctl start firewalld.service
$ systemctl stop firewalld.service
$ systemctl status firewalld.service
{% endhighlight %}

To list details of default and active zones
{% highlight bash %}
$ firewall-cmd --get-default-zone
$ firewall-cmd --get-active-zones
$ firewall-cmd --list-all
{% endhighlight %}

To list/add/remove services to zones
To list available services :
{% highlight bash %}
$ firewall-cmd --get-services
{% endhighlight %}


To add “samba and samba-client” service to a specific zone. You may include, “permanent” flag to make this permanent change.
{% highlight bash %}
$ firewall-cmd --zone=public --add-service=samba --add-service=samba-client --permanent
{% endhighlight %}

To list services configured in a specific zone.
{% highlight bash %}
$ firewall-cmd --zone=public --list-service
{% endhighlight %}


To list and Add ports to firewall
{% highlight bash %}
$ firewall-cmd --list-ports
$ firewall-cmd --zone=public --add-port=5000/tcp
{% endhighlight %}


Note:
You may restart the Network service followed by Firewall server.
{% highlight bash %}
$ systemctl restart network.service
$ systemctl restart firewalld.service
{% endhighlight %}


Adding services
{% highlight bash %}
$ firewall-cmd --zone=public --add-service=http
{% endhighlight %}

or
{% highlight bash %}
$ firewall-cmd --zone=public --permanent --add-service=http
{% endhighlight %}


List services
{% highlight bash %}
$ firewall-cmd --get-services
{% endhighlight %}


Or add custom ports:
{% highlight bash %}
$ firewall-cmd --zone=public --add-port=1234/tcp
{% endhighlight %}

or
{% highlight bash %}
$ firewall-cmd --zone=public --add-port=1234-5678/tcp
{% endhighlight %}


Reload
{% highlight bash %}
$ firewall-cmd --reload
{% endhighlight %}







Start
{% highlight bash %}
$ systemctl start firewalld.service
{% endhighlight %}

Restart
{% highlight bash %}
{% endhighlight %}

$ systemctl restart firewalld.service

Reload
{% highlight bash %}
$ firewall-cmd --reload
{% endhighlight %}

Stop firewallD
{% highlight bash %}
$ systemctl stop firewalld
{% endhighlight %}

Get State / State
{% highlight bash %}
$ firewall-cmd --state
{% endhighlight %}

Get Default Zone
{% highlight bash %}
$ firewall-cmd --get-default-zone
{% endhighlight %}

Get Active Zone
{% highlight bash %}
$ firewall-cmd --get-active-zones
{% endhighlight %}

Get public ports
{% highlight bash %}
$ firewall-cmd --zone=public --list-ports
{% endhighlight %}

Allow the default HTTP and HTTPS port to firewall to be public (for example 80)
{% highlight bash %}
$ firewall-cmd --permanent --add-port=80/tcp
{% endhighlight %}

Or nor permanent
{% highlight bash %}
$ firewall-cmd --add-port=80/tcp
{% endhighlight %}

Remove ports from public (for example 80)
{% highlight bash %}
$ firewall-cmd --permanent --zone=public --remove-port=80/tcp
{% endhighlight %}

Or nor permanent
{% highlight bash %}
$ firewall-cmd --zone=public --remove-port=80/tcp
{% endhighlight %}

Disable firewallD
{% highlight bash %}
$ systemctl disable firewalld
{% endhighlight %}

Get status firewallD
{% highlight bash %}
$ systemctl status firewalld
{% endhighlight %}


Now, let's whitelist a specific IP which grants access to any port.

{% highlight bash %}
$ firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4" source address="xx.xx.xx.xx" accept'
{% endhighlight %}

Now, let's whitelist another IP, that we only want to have access to SSH, http, and https access. No other ports.
{% highlight bash %}
$ firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4" source address="xx.xx.xx.xx" service name="ssh" accept'
$ firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4" source address="xx.xx.xx.xx" service name="http" accept'
$ firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4" source address="xx.xx.xx.xx service name="https" accept'
{% endhighlight %}

If you're connecting via SSH, be sure to authorize your IP before applying your new rule set. When ready to apply the new rules.

{% highlight bash %}
$ firewall-cmd --reload
{% endhighlight %}

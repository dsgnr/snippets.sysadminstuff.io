---
layout: post
title: Useful Fail2Ban Commands
categories: fail2ban
permalink: /:categories/:title
---

Check the status of all jails:
{% highlight bash %}
$ fail2ban-client status
Status
|- Number of jail:	3
`- Jail list:	nginx-400, sshd, unifi
{% endhighlight %}

Show a list of all IPs blocked with Fail2ban within a particular jail:
{% highlight bash %}
$ fail2ban-client status nginx-400
Status for the jail: nginx-400
|- Filter
|  |- Currently failed:	0
|  |- Total failed:	6
|  `- File list:	/var/log/nginx/unifi.handsoff.cloud.access.log
`- Actions
   |- Currently banned:	1
   |- Total banned:	2
   `- Banned IP list:	10.50.3.12
{% endhighlight %}

Show a list of all IPs blocked with Fail2Ban from all jails:
{% highlight bash %}
$ fail2ban-client status | grep "Jail list:" | sed "s/ //g" | awk '{split($2,a,",");for(i in a) system("fail2ban-client status " a[i])}' | grep "Status\|IP list"
Status for the jail: nginx-400
   `- Banned IP list:	10.50.3.12
Status for the jail: sshd
   `- Banned IP list:
Status for the jail: unifi
   `- Banned IP list:	10.50.3.12 10.50.3.12fail2ban-client

{% endhighlight %}
Unban a particular IP address from a jail:
{% highlight bash %}
$ fail2ban-client set nginx-400 unbanip 10.50.3.12
10.50.3.12
{% endhighlight %}


{% highlight bash %}
fail2ban-client -vvv set JAIL banip
{% endhighlight %}

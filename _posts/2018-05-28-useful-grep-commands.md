---
layout: post
title: Useful Grep Commands
categories: grep
permalink: /:categories/:title
---

    Search for lines containing ‘PermitRootLogin’ from a file called main.yml:
{% highlight bash %}
$ grep PermitRootLogin main.yml
    - regexp: "^PermitRootLogin"
      line: "PermitRootLogin yes"
{% endhighlight %}

Search for all yaml files inside the current directory containing 'MariaDB':
{% highlight bash %}
$ grep MariaDB *.yml
install_centos.yml:- name: Install MariaDB
install_centos.yml:    - MariaDB-server
install_centos.yml:    - MariaDB-client
install_ubuntu_xenial.yml:- name: Install MariaDB
{% endhighlight %}

Search for all yaml files inside the current directory containing 'MariaDB' and show line numbers:
{% highlight bash %}
$ grep -n MariaDB *.yml
install_centos.yml:6:- name: Install MariaDB
install_centos.yml:9:    - MariaDB-server
install_centos.yml:10:    - MariaDB-client
install_ubuntu_xenial.yml:3:- name: Install MariaDB
{% endhighlight %}

Search for lines containing ‘ssh’ in all yaml files located in the current directory:
{% highlight bash %}
[root@v-cent003 roles]# find . -name '*.yml' -exec grep -l 'ssh' {} \;
./secure-ssh/tasks/main.yml
./secure-ssh/handlers/main.yml
{% endhighlight %}

List all Nginx processes:
{% highlight bash %}
root@V-Web001:/# ps aux | grep nginx
root      84788  0.0  0.0 138548  3072 ?        Ss   20:06   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
www-data  84792  0.0  0.2 138548  8636 ?        S    20:06   0:00 nginx: worker process
root      86839  0.0  0.0  12948   904 pts/6    S+   20:40   0:00 grep --color=auto nginx
{% endhighlight %}

Display total number of Redis connections on port 6379:
{% highlight bash %}
[root@v-cent003 /]# netstat -an | grep :6379 |wc -l
3
{% endhighlight %}

Search all yaml files for a text pattern of 'hosts':
{% highlight bash %}
[root@v-cent003 ansible]# find . -iname "*.yml" -exec grep -l "hosts" {} +
./secure-ssh.yml
./vsphere-guest-deploy.yml
./common.yml
./deploy-zabbix-agent.yml
./deploy-nginx.yml
./deploy-wp-cli.yml
./deploy-php7.1.yml
./deploy-vmware-tools.yml
./new-deployment.yml
{% endhighlight %}


To search for multiple patterns at one time, you can simply use the egrep command. egrep is the same as grep -E.
{% highlight bash %}
$ egrep 'zabbix-agent|zabbix_listen' main.yml
- name: Update the zabbix-agent configuration
      line: "Server={{ zabbix_listen_server }}"
      line: "ListenPort={{ zabbix_listen_port }}"
      line: "ServerActive={{ zabbix_listen_server_active }}"
    - Restart zabbix-agent
        port: "{{ zabbix_listen_port }}"
{% endhighlight %}

The fgrep searches a file or list of files for a fixed pattern string. fgrep is the same as grep –F.
{% highlight bash %}
[root@v-cent003 /]# fgrep 'cachedir' /etc/yum.conf
cachedir=/var/cache/yum/$basearch/$releasever
{% endhighlight %}


Search for a string in a file (this is not case sensitive):
{% highlight bash %}
 grep -i "the" demo_file
{% endhighlight %}

Print the matched line, along with the 3 lines after it.
{% highlight bash %}
grep -A 3 -i "example" demo_text
{% endhighlight %}

{% highlight bash %}
grep -B 3 -A 2 foo README.txt
{% endhighlight %}
If you want the same number of lines before and after you can use -C num.

{% highlight bash %}
grep -C 3 foo README.txt
{% endhighlight %}

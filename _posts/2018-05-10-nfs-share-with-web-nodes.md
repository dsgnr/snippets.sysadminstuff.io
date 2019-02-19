---
layout: post
title: NFS share creating with web nodes
categories: guides
permalink: /:categories/:title
---

Need to improve and elaborate on this:

On NFS server:
{% highlight python %}
apt-get update && apt-get upgrade -y
apt-get dist-upgrade -y
apt-get install nfs-kernel-server nfs-common less nfs4-acl-tools lvm2 -y
pvcreate /dev/xvdb1
vgcreate data /dev/xvdb1
lvcreate -l 12799 -n nfs data (specify your size)
mkfs -t ext4 -m 1 -v /dev/data/nfs
mkdir -p /mnt/var/www/vhosts
mkdir -p /home/backup
cp -a /etc/fstab /home/backup/
echo '/dev/data/nfs /mnt/var/www ext4 defaults,user_xattr,acl 0 0' >> /etc/fstab
cp -a /etc/exports /home/backup/
echo '/mnt/var/www/vhosts IPRANGE/22(rw,sync,fsid=0,crossmnt,no_subtree_check,no_root_squash)' >> /etc/exports
chown -R user:group /var/www/vhosts/
{% endhighlight %}

On Web nodes / NFS clients:

{% highlight python %}
apt-get update && apt-get upgrade -y
apt-get dist-upgrade -y
apt-get install less nfs-common php7.0 php-pear php7.0-bz2 php7.0-curl php7.0-gd php7.0-mbstring php7.0-zip php7.0-mysql php7.0-xml php7.0-bcmath php7.0-bz2 php7.0-dba php7.0-common python-mhash php7.0-soap -y
mkdir -p /var/www/vhosts
useradd -m -d /var/www/home_dir username -s /bin/bash
echo username:password | chpasswd
mkdir -p /home/backup/
cp -a /etc/fstab /home/backup/
echo 'IP OF SERVER:/mnt/var/www/home_dir /var/www/home_dir nfs auto,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0' >> /etc/fstab
rm /lib/systemd/system/nfs-common.service
systemctl daemon-reload
systemctl start nfs-common
systemctl enable nfs-common
mount -a
{% endhighlight %}

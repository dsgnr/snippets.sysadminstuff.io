---
layout: post
title: Docker Commands
categories: docker
permalink: /:categories/:title
---

<h3>Informational</h3>
List all docker containers
<code>docker container ls</code>

List running Docker containers
<code>docker ps</code>

List running and stopped Docker containers 
<code>docker ps -a</code>

To show Container information like IP adress.
<code>docker inspect $containername</code>

To show log of a Container.
<code>docker logs $containername</code>

To show running process in a Container.
<code>docker top $containername</code>


<h3>Container</h3>

To stop a Container.
<code>docker stop $containername</code>

To start a Container.
<code>docker start $containername</code>

To restart a Container.
<code>docker restart $containername</code>

To Connect to a running Container.
<code>docker attach $containername</code>

To copy file in a Container to the host.
<code>docker cp $containername:/etc/passwd .</code>

To mount the directory in host to a Container.
<code>docker run -v /home/vagrant/test:/root/test ubuntu echo yo</code>

<h3>Connecting</h3>
SSH into a Docker container
<code>docker exec -it $containerID /bin/bash</code>

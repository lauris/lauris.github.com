---
layout: post
title: "First impressions of Docker"
category: development
permalink: /first-impressions-docker
related: ["Moving away from the cloud", "Bash Productivity Tips", "The
Technology Behind Datazenit: Part 1"]
---

Finally I got a chance to play with Docker and was pretty satisfied with
the experience. There are some rough edges, but it didn't lessen my excitement.
Docker is stable for a few months, currently the latest version is 1.2.

I will try to use Docker to run different versions of MySQL and PostgreSQL for
testing purposes at [Datazenit](https://datazenit.com). Docker was pretty easy to
setup both on my development MacBook and on a Linux server. Docker offers a
nice, official package for OSX that installs all dependencies, including,
VirtualBox. [An interactive tutorial](https://docker.com/tryit/) can be found on Docker website, and it
covers all core aspects of Docker.

I found out that there are pre-made repositories for MySQL and PostgreSQL images. I
started with MySQL and got a working container within 10 minutes. Most of the
time was spent to download the image, so I can say that the process was really simple.
Sadly only the latest version worked flawlessly. I haven't yet looked carefully enough, but each of the older
versions had some random errors. Maybe it could be related to the fact that I
run all containers on a single host, but that would be strange and it would
also defeat the whole point of Docker containers.

Another unexpected thing was that you need to configure a separate volume
container if you want a persistant and stable storage for your containers. Link
to official docs regarding this –
[Managing Data in Containers](https://docs.docker.com/userguide/dockervolumes/).
However one sentence from docs was confusing: "Volumes persist until no containers use
them" So is the special volume container really persistent or not? If I reboot
my host will the volume container lose all its data? But this is probably just
a confusement caused by not RTFM. Will learn more and report back.

---
layout: post
title: "Servers are fun: Ansible"
category: servers
---

Server administration is an interesting form of art in which I was kinda drawn into. I do not consider myself anything near a system administrator, but I like working with Linux and servers. Most of my favorite development tools are run from a terminal, and I like them because they are fast, predictable and scriptable. 

<!-- more -->

Server tending is just a hobby for me, but I often get to do server administration semi-professionally. While working on [Datazenit](http://datazenit.com) and some other projects I do all the server stuff myself, mostly because it is economically advantageous and faster that way. As you probably know time and money are precious resources for a startup. Most of my freelance clients also need their servers set up quickly and they usually do not want to get a dedicated guy just for that, resulting in more Linux time for me.

Recently I finally decided to try [Ansible](http://www.ansible.com/home). I had heard good things about it, but always thought that it is too complex and that it probably would introduce a huge overhead, but I couldn't be more wrong. The core concepts behind it are really simple ones and it didn't take long to get familiar with Ansible. Essentially it is just executes scripts on a remote server and holds a list of SSH logins for your servers. You can execute commands on a single server or on multiple servers simultaneously, use existing or define your own scripts and create a whole configuration management and deployment system on top of it. Of course there is special vocubulary for all the things I just mentioned, like "tasks", "playbooks", etc., but the idea is still the same. 

The only thing that discouraged me in the beginning was [a bit overwhelming documentation](http://docs.ansible.com/) that felt more like a study material, but I am sure that there are guides especially for beginners too. The docs just made Ansible look more complex and advanced than it really is. You can get started in no time and already feel the benefit of it after a few uses.

I would like to recommend to try it out or check the alternatives like Chef, Puppet and others. Ansible made me feel that excitement about servers that I had forgotten about. I just want to dig deeper and get to know what else can it offer.

A small off-topic: Today I got a chance to set up Intel NUC Kit and was really surprised at how small these things have gotten. It is a small factor PC and in this case will be used as a LAMP server. Its dimensions doesn't exceed 11x11cm – you could just bring that around in your back pocket. It has a pretty decent Haswell processor, up to 16GB of RAM and this one had also a SSD drive. Not bad at all. You can also use it as a media center (it has HDMI, a display port and four USB ports) or even as a desktop PC.
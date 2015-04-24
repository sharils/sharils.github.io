---
layout: post
title:  "apt-add-repository in Dockerfile"
date:   2015-04-25 05:14:06
categories: jekyll update
---

This is an alternative to apt-add-repository which is useful for building
docker images. The following is an example for adding Phalcon repository from
launchpad.net

{% highlight dockerfile %}
FROM ubuntu
MAINTAINER maintainer@example.com

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 1E569794
RUN echo "deb http://ppa.launchpad.net/phalcon/stable/ubuntu trusty main" > /etc/apt/sources.list.d/phalcon-stable-trusty.list
{% endhighlight %}

See the picture below for where magic values are from. But I have no idea where
"/etc/apt/sources.list.d/phalcon-stable-trusty.list" is from though.

[![source of magic values](/cdn/2015-04-25-apt-add-repository-alternative/launchpad.png)](/cdn/2015-04-25-apt-add-repository-alternative/launchpad.png)

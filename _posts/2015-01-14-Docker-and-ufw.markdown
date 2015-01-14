---
layout: post
title:  "Docker and ufw"
date:   2015-01-14 23:46:00
categories: docker linux ubuntu firewall ufw
---

To enable host communication from `docker` container (for example to connect to MySQL database) you need to allow all connections for corresponding subnet:

{% highlight bash %}
$ ifconfig
docker0   Link encap:Ethernet  HWaddr 56:84:7a:fe:97:99
          inet addr:172.17.42.1  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::5484:7aff:fefe:9799/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:36219405 (36.2 MB)  TX bytes:1303680830 (1.3 GB)
...
{% endhighlight %}

{% highlight bash %}
$ ufw allow from 172.17.0.0/16
Rule added

$ ufw status
Status: active

To                         Action      From
--                         ------      ----
...
Anywhere                   ALLOW       172.17.0.0/16
...
{% endhighlight %}
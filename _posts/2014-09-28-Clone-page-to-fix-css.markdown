---
layout: post
title:  "Clone page to fix css"
date:   2014-09-28 00:26:00
categories: html css fix
---

If you want to fix `css` of remote web page, you can quickly download it with all deps and quick-serve as static site:

{% highlight bash %}
$ wget --page-requisites http://google.com/
...
$ cd google.com
$ python -m SimpleHTTPServer
{% endhighlight %}
---
layout: post
title:  "Hello World"
date:   2015-04-21 23:15:41
categories: jekyll update
---

PHP
---

{% highlight bash %}
docker run --rm php php -r 'echo "Hello PHP!";'
{% endhighlight %}

JavaScript
----------

{% highlight javascript %}
document.write("Hello JavaScript!")
{% endhighlight %}

Node.js
-------

{% highlight bash %}
docker run --rm node node -e 'console.log("Hello Node.js!")'
{% endhighlight %}

Python
------

{% highlight bash %}
docker run --rm python python -c 'print("Hello Python!")'
{% endhighlight %}

LiveScript
----------

{% highlight bash %}
docker run --rm cromo/livescript lsc -e 'console.log "Hello LiveScript!"'
{% endhighlight %}

CoffeeScript
------------

{% highlight bash %}
docker run --rm shouldbee/coffeescript coffee -e 'console.log "Hello CoffeeScript!"'
{% endhighlight %}

Lua
---

{% highlight bash %}
docker run --rm smutdose/lua lua -e 'print("Hello Lua!")'
{% endhighlight %}

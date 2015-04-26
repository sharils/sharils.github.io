---
layout: post
title:  "Zephir At First Glance"
date:   2015-04-25 05:14:06
categories: jekyll update
---

Installation
------------

There is a [Docker image for Zephir](https://registry.hub.docker.com/u/smutdose/zephir/).

Use PHP Function
----------------

You can use php function in zephir. For example

{% highlight zephir %}
namespace Test;

class Hello
{
    public function say()
    {
        fib();
    }
}
{% endhighlight %}

When you build, zephir shows you this:

Warning: Function "fib" does not exist at compile time in /tmp/test/test/Hello.zep on 7 [nonexistent-function]

{% highlight php %}
<?php
function fib()
{
    echo '1 1 2 3 5 8';
}
$hello = new Test\Hello();
$hello->say();
{% endhighlight %}

When you execute the php file, you see this:

1 1 2 3 5 8

This shows you that you can use php function in zephir.

Use Extension Function
----------------------

You can use function from other PHP extension. For example:

{% highlight zephir %}
namespace Test;

class Hello
{
    public function say()
    {
        var ch;

        let ch = curl_init("http://example.com/");

        curl_exec(ch);
    }
}
{% endhighlight %}

{% highlight php %}
<?php
$hello = new Test\Hello();
$hello->say();
{% endhighlight %}

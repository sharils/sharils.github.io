---
layout: post
title:  "PHP Callable Class"
date:   2015-05-13 23:35:18
categories: jekyll update
---

`` __invoke `` makes an object callable.

{% highlight php %}
<?php
class CallableObject
{
	public function __invoke()
	{
	}
}
?>
{% endhighlight %}

Though there is no magic method that makes a class callable e.g. ``
__invokeStatic ``.

But we can still make a callable class. That's to define a function with the
same name as the class. E.g.

{% highlight php %}
<?php
function CallableClass()
{
	return new CallableClass();
}

class CallableClass
{
	public function __invoke()
	{
	}
}
?>
{% endhighlight %}

Note that before PHP 5.6, the constructor signature has to duplicate again as
the function signature, this makes it a little bit awakard to define. (Using
Reflection won't be easier either) E.g.

{% highlight php %}
<?php
function CallableClassPhp53($lifeTime)
{
	return new CallableClassPhp53($lifeTime);
}

class CallableClassPhp53
{
	public function __construct($lifeTime)
	{
	}
}
?>
{% endhighlight %}

This is solved by the introduction of [Variable-length argument lists](http://php.net/manual/en/functions.arguments.php#functions.variable-arg-list) since PHP 5.6.

{% highlight php %}
<?php
function CallableClassPhp56()
{
	return new CallableClassPhp56(...func_get_args());
}

class CallableClassPhp56
{
	public function __construct($lifeTime)
	{
	}
}
?>
{% endhighlight %}

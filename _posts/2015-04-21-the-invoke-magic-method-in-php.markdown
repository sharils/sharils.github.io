---
layout: post
title:  "The Invoke Magic Method In PHP"
date:   2015-04-21 23:25:32
categories: jekyll update
---

I discovered a good use case of
[\_\_invoke](http://php.net/manual/en/language.oop5.magic.php#object.invoke) --
that's when a function expects a callable, e.g. spl\_autoload\_register.

In this case we often see implementation passes an anonymous function or a
named function.

[Anonymous function example](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader-examples.md#closure-example)

[Named function example](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md#example-implementatio)

We can also craft a class which implements \_\_invoke. It's not too awkward to
use.

[Callable object example](https://gist.github.com/sharils/794cb15a4be88d8c132c)

Let's compare these three methods.

{% highlight php %}
<?php
function autoload($fqcn)
{
}
spl_autoload_register('autoload');
?>
{% endhighlight %}

{% highlight php %}
<?php
spl_autoload_register(function ($fqcn) {
});
?>
{% endhighlight %}

{% highlight php %}
<?php
class Autoload
{
	public function __invoke($fqcn)
	{
	}
}
spl_autoload_register(new Autoload());
?>
{% endhighlight %}

The paragraphs above merely point out a fact that there is a third option when
we implement a callable.

Yet this becomes interesting when you want to dynamically generate a callable
for the function that expects a callable, e.g. spl\_autoload\_register.

{% highlight php %}
<?php
function autoload_factory($namespace, $dir)
{
	return function ($fqcn) use ($namespace, $dir) {
	};
}
spl_autoload_register(autoload_factory('Example', 'src'));
?>
{% endhighlight %}

{% highlight php %}
<?php
class AutoloadFactory
{
	public function __construct($namespace, $dir)
	{
	}

	public function __invoke($fqcn)
	{
	}
}
spl_autoload_register(new AutoloadFactory('Example', 'src'));
?>
{% endhighlight %}

That's all!

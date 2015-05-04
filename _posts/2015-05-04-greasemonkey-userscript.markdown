---
layout: post
title:  "Greasemonkey UserScript"
date:   2015-05-04 08:50:47
categories: jekyll update
---

example.com.user.js
-------------------

Assume the following is the content for [`example.com.user.js`](/cdn/2015-05-04-greasemonkey-userscript/example.com.user.js)

{% highlight js %}
// ==UserScript==
// @name		Example
// @namespace	http://example.com/
// @description	A simple example of UserScript
// @match		http://example.com/
// @require		http://code.jquery.com/jquery-2.1.3.js
// @version		1.0.0
// @grant		none
// @noframes
// ==/UserScript==

if (top === window) {
	alert(typeof this.$)
}
{% endhighlight %}

This will be used throughout this article.

Installed UserScript
--------------------

### Mozilla Firefox ###

It's located at
`~/.mozilla/firefox/<profile-folder>/gm_scripts/<@name>/<filename>`, e.g.
`~/.mozilla/firefox/liwedlz1.default/gm_scripts/Example/example.com.user.js`.

When the file is changed, it's applied immediately.

### Google Chrome ###

Assume the `ID` for `Example` in `chrome://extensions/` is
`okfhfojoehlfgaomjbceecgpkhgcodid`.

It's located at
`~/.config/google-chrome/<profile-folder>/Extensions/<id>/<@version>_<auto-increment>/script.js`
E.g. `~/.config/google-chrome/Profile
1/Extensions/okfhfojoehlfgaomjbceecgpkhgcodid/1.0.0_0/script.js`

when the file is changed, it's applied after chrome is restarted.

Metadata Block
--------------

Use one tab between // and @key instead one space causes unexpected behaviour
in both chrome and firefox.

OK: `// @name Example`

NG: `//	@name Example`

Tabs or spaces are both accepted between @key and its value.

- OK: `// @name     Example`

- OK: `// @name		Example`

It's a common practice to align values.

@grant
------

Firefox complains about missing `@grant` so add it.

@noframes
---------

Chrome 42.0.2311.135 still doesn't support `@noframes` directive. A workaround
for this is to test whether `top` is `window`. E.g.

{% highlight js %}
if (top === window) {
	console.log("Hello world");
}
{% endhighlight %}

A caveat here is that in Firefox, `top` is not identical to `this`, so the
following code won't work.

{% highlight js %}
if (top === this) {
	console.log("Hello world");
}
{% endhighlight %}

@require
--------

Chrome 42.0.2311.135 still doesn't support `@require` directive. So we see
`undefined` when we visit http://example.com in Chrome.

Firefox doesn't have this problem. So we see `function` when we visit
http://example.com/ in firefox.

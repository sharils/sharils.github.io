---
layout: post
title:  "PHP array_intersect"
date:   2015-05-25 12:01:37
categories: jekyll update
---

array\_intersect and array\_intersect\_key
------------------------------------------

`` array_intersect `` compares only values.

`` array_intersect_key `` compares only keys.

`` array_uintersect `` compares only values with a compare function.

`` array_intersect_ukey `` compares only keys with a compare function.

array\_intersect\_assoc
-----------------------

`` array_intersect_assoc `` compares keys and values.

`` array_intersect_uassoc `` compares keys and values with a key comparison function.

`` array_uintersect_assoc `` compares keys and values with a value comparison function.

`` array_uintersect_uassoc `` compares keys and values with a value comparison function and a key comparison function.

meaning of u
------------

When intersect is prefixed with u, it means a value comparison function.

When key or assoc is prefixed with u, it means a key comparison function.

two u's
-------

When there are two u's, first callback is for intersect, second callback is for
assoc. This is exactly the order they appear in the function name.

array\_diff
--------------------------------

Same applies to `` array_diff ``.

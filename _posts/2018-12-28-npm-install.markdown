---
layout: post
title:  "npm install"
date:   2018-12-23 23:38:15
categories: jekyll update
---

TL;DR

1. `npm` version `6.4.1`.
2. Use `NODE_ENV=production npm ci` for production build. E.g. in Dockerfile.
3. Use `NODE_ENV=production npm install --no-audit` with `--offline` or
   `--prefer-offline` when you are trying different package's. E.g. finding
   which dependency works or breaks.
4. Use `npm ci` whenever you think of `npm install`.
5. Use `npm install` in any other cases.

```
$ rm -fr ./node_modules && time npm install
real	1m37.645s
user	1m21.663s
sys	0m32.953s
```

The slowest.

```
$ rm -fr ./node_modules && time npm install --prefer-offline
real	1m10.059s
user	1m8.615s
sys	0m33.535s
```

`--prefere-offline` is faster than without it.

```
$ rm -fr ./node_modules && time npm install --offline
real	0m59.658s
user	1m2.794s
sys	0m30.149s
```

`--offline` is faster than `--prefer-offline`.

```
$ rm -fr ./node_modules && time npm install --offline --no-audit
real	0m54.984s
user	1m0.524s
sys	0m29.629s
```

`--no-audit` makes it a little bit faster.

```
$ rm -fr ./node_modules && time npm install --offline --no-audit --only=prod
real	0m35.677s
user	0m39.828s
sys	0m16.780s
```

`--only=prod` makes it much faster.

```
$ rm -fr ./node_modules && export NODE_ENV=production && time npm install --offline --no-audit
real	0m32.578s
user	0m38.242s
sys	0m16.573s
```

`NODE_ENV=production` is faster than `--only-prod`.

```
$ export NODE_ENV=production && time npm ci --offline --no-audit
real	0m22.572s
user	0m20.928s
sys	0m16.034s
```

`npm ci` is faster than `npm install`.

```
$ export NODE_ENV=production && time npm ci --no-audit
real	0m25.646s
user	0m17.084s
sys	0m13.334s
```

`--offline` makes `npm ci` a little bit slower.

```
$ export NODE_ENV=production && time npm ci
real	0m17.636s
user	0m16.791s
sys	0m9.699s
```

`--no-audit` also makes `npm ci` a little slower.

```
$ time npm ci
real	0m35.362s
user	0m18.570s
sys	0m16.471s
```

`NODE_ENV=production` makes `npm ci` much faster.

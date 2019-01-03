---
layout: post
title:  "Watchman log"
date:   2019-01-03 20:28:26
categories: jekyll update
---

```
If you used the --enable-statedir=<STATEDIR> configure option, that will be the
location that holds your logs. If not, the default for STATEDIR will be
<PREFIX>/var/run/watchman, or for older versions of watchman, the logs may be
placed in <TMPDIR>/.watchman.<USER>.log.
```
[Source][1]


```
"--enable-statedir=#{var}/run/watchman"
```
[Source][2]


Type `brew config` and look for the HOMEBREW_PREFIX config value. Now we know
it's located at:

`/usr/local/var/run/watchman/$USER-state/log`


[1]: https://facebook.github.io/watchman/docs/troubleshooting.html#where-are-the-logs "Troubleshooting | Watchman"
[2]: https://github.com/Homebrew/homebrew-core/blob/master/Formula/watchman.rb#L40 "homebrew-core/watchman.rb at master · Homebrew/homebrew-core"

---
layout: post
title:  "Notes for Updating a Cask"
date:   2018-10-29 20:08:07
categories: jekyll update
---

# Notes for [Updating a Cask][1]

## Check if PR for the cask is created

```sh
git clone https://github.com/Homebrew/homebrew-cask.git /tmp/homebrew-cask && \
cd /tmp/homebrew-cask && \
hub pr list | grep <cask>
```

## Update a cask

```sh
cd $(brew --repository) && \
hub issue && \
noti cask-repair <outdated_cask> -v <version>
```

Ensure that we won't have to redo (including redownloading the cask) just
because we don't have access.

Notify us when it's done.

Skip version prompt.

## Update polar-bookshelf

```sh
git clone https://github.com/Homebrew/homebrew-cask.git /tmp/homebrew-cask && \
cd /tmp/homebrew-cask && \
hub pr list | grep polar-bookshelf && \
noti cask-repair polar-bookshelf -v 1.0.11
```

## Update origin

```sh
git clone https://github.com/Homebrew/homebrew-cask.git /tmp/homebrew-cask && \
cd /tmp/homebrew-cask && \
hub pr list | grep origin && \
noti cask-repair origin
```

[1]: https://github.com/Homebrew/homebrew-cask/blob/master/CONTRIBUTING.md#updating-a-cask

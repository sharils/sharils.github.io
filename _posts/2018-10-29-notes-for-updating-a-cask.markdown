---
layout: post
title:  "Notes for Updating a Cask"
date:   2018-10-29 20:08:07
categories: jekyll update
---

# Notes for [Updating a Cask][1]

## Check if PR for the cask is created

### Using `Github website`

Check from Github website. Replace `%s` with the cask name.

```
open 'https://github.com/Homebrew/homebrew-cask/search?type=Issues&q=%s'
```

For example to check if there is a [PR for the latest polar-bookshelf][2]:

```
open 'https://github.com/Homebrew/homebrew-cask/search?type=Issues&q=polar-bookshelf'
```

Another example to check if there is a [PR for the latest origin][3]:

```
open 'https://github.com/Homebrew/homebrew-cask/search?type=Issues&q=origin'
```

### Using `hub`

Check from CLI with hub. Replace `<cask>` with the cask name.

```sh
git clone --depth=1 https://github.com/Homebrew/homebrew-cask.git /tmp/homebrew-cask && \
cd /tmp/homebrew-cask && \
hub pr list | grep <cask>
```

For example to check if there is a PR for the latest polar-bookshelf:

```sh
git clone --depth=1 https://github.com/Homebrew/homebrew-cask.git /tmp/homebrew-cask && \
cd /tmp/homebrew-cask && \
hub pr list | grep polar-bookshelf
```

## Input password for PGP key (optional)

We do this upfront so that we won't have to redo (including redownloading the
task) just becasue we put in the wrong PGP key password.

```sh
mkdir -p /tmp/cask-repair && \
cd /tmp/cask-repair && \
git init && \
git commit --allow-empty --message 'Initialize empty Git repository' && \
cd - && \
rm -fr /tmp/cask-repair
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

[1]: https://github.com/Homebrew/homebrew-cask/blob/master/CONTRIBUTING.md#updating-a-cask "homebrew-cask/CONTRIBUTING.md at master · Homebrew/homebrew-cask · GitHub"
[2]: https://github.com/Homebrew/homebrew-cask/search?type=Issues&q=polar-bookshelf "Search · polar-bookshelf"
[3]: https://github.com/Homebrew/homebrew-cask/search?type=Issues&q=origin "Search · origin"

---
layout: post
title:  "Notes for Updating a Cask"
date:   2018-10-29 20:08:07
categories: jekyll update
---

# Notes for [Updating a Cask][1]

`cd $(brew --repository) && hub issue && cask-repair <outdated_cask>`

Ensure that we won't have to redo (including redownloading the cask) just
because we don't have access.

[1]: https://github.com/Homebrew/homebrew-cask/blob/master/CONTRIBUTING.md#updating-a-cask

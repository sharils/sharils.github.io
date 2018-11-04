---
layout: post
title:  "CSS: Definitive Guide Chapter 7"
date:   2018-11-04 20:07:57
categories: jekyll update
---

## horizontal formatting

- containing block
- no auto makes margin-right auto (overconstrainted)
- margin-left: 1rem, width: 2rem, margin-right: auto makes width of containing block
- margin-left and margin-right autos makes width horizontally centered
- margin-left and width autos makes margin 0
- 3 autos makes both margin 0
- the trick is the make them sum up to containing block's width
- replaced width: auto = intrinsic width

## vertical formatting

- margin-top or margin-bottom auto makes both zero

## inline formatting

- inline box vs line box
- inline non-replaced padding, border, margin doesn't height of line box in contrary to inline replaced
- height of inline box: leading, replaced, baseline, vertical-align
- line-height inherits
- font-size does affect linebox height because it changes height above and below baseline
- just use scalar for line-height
- display: inline-block
- display: flow
- display: contents

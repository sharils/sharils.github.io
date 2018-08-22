---
layout: post
title:  "CSS: Definitive Guide Chapter 4"
date:   2018-08-22 08:30:47
categories: jekyll update
---

- global All property values: inherit vs initial vs unset vs revert
- Use "\^M" for line continuation; use "\A" for a real newline
- image-set() https://drafts.csswg.org/css-images-4/#image-set-notation
- absolute length units: https://ethercalc.org/zd82oa4saoto
- dpi vs dpcm vs dppx, 96 dpi = 1 dppx
- em, ex, rem, ch
- vw, vh, viewport width/height / 100
- vmin = min(vw, vh), vmax = max(vw, vh)
- calc(90% - 2em)
- attr(maxlength em) = 10em <input maxlength="10" />
- Named Colors https://www.w3.org/TR/css-color-4/#named-colors
- rgb(25.5%, 4200%, 98.6%) or rgb(255, 444, 255)
- rgba(25.5%, 4200%, 98.6%, 0.5) or rgb(255, 444, 255, 0.5)
- #666, #903bc0, #000000cc
- hsl(300, 0%, 25%), hsla(300, 0%, 25%, 0.8)
- currentColor, transparent
- 360deg, 400grad, 6.283rad, 1turn
- 2.4s, 2400ms, 128hz, 0.128khz
- html { --case-sensitive: #639 }, h1 { color: var(--case-sensitive) }
- calc(var(--gutter) * var(--offset))

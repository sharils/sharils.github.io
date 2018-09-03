---
layout: post
title:  "CSS: Definitive Guide Chapter 5"
date:   2018-09-03 23:01:52
categories: jekyll update
---

- "Times" is a font family just like "serif" is because it has bold, italic, etc.
- @font-face {
    font-family: "SwitzeraADF";
    src: url("SwitzeraADF-Regular.otf") format("opentype"), url("/fonts/SwitzeraADF-Regular.true") format("truetype");
    /* optional */
    font-style: normal;
    font-weight: normal;
    font-stretch: normal;
    font-variant: small-caps slashed-zero;
    font-feature-settings: "afrc" off, "smcp" off;
    font-unicode-range: U+4E00-9FFF, U+FF00-U+FF9F, U+30??;
  }
- @font-face and access-control-allow-origin: *
- @font-face lazy loads
- FOUC, flash of unstyled content vs FOUFT, flash of un-fonted text, solution: font-size
- [Bulletproof @font-face syntax - Paul Irish](https://web.archive.org/web/20171107174543/https://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/)
- license issue solution open source fonts or fontdeck and typekit
- font-optimisating tools e.g. typekit
- font-unicode-range helps reduce downloaded font file size
- * {
    font-weight: bold;
    font-size: normal;
    font-size-adjust: auto;
    font-style: oblique;
    font-stretch: expanded;
    font-kerning: auto;
    font-variant: small-caps;
    font-variant-ligatures: ;
    font-variant-caps: ;
    font-variant-numeric: ;
    font-variant-alternates: ;
    font-variant-east-asian: ;
    font-feature-settings: "liga" on, "smcp" 2;
    font-synthesis: weight style;
  }
- 400 normal, 700 bold
- em square or em box can be taller, equal or shorter than some characters
- [Design With FontForge: The EM Square](http://designwithfontforge.com/en-US/The_EM_Square.html)
- css 1, 2, 3 have different scaling factor, table 5-5
- em, % font-size are based on parent element
- 1.6em = 166%
- font-family: monospace, serif vs font-family: monospace
- aspect value = font-size / x-height, the higher the more legible
- https://meyerweb.github.io/csstdg4figs/05-fonts/ch0522.html vs https://meyerweb.github.io/csstdg4figs/05-fonts/ch0523.html
- oblique -> italic, ok, italic -> oblique, ng
- font-stretch https://meyerweb.github.io/csstdg4figs/05-fonts/ch0529.html
- font-kerning https://developer.mozilla.org/en-US/docs/Web/CSS/font-kerning
- { font-size: 12px; font: bold italic small-caps 200%/1.2 Verdana, Helvetica, Arial, sans-serif; }
- height = 12 * 200% * 1.2 = 28.8px
- https://meyerweb.github.io/csstdg4figs/05-fonts/ch0536.html
- { font: status-bar; font-size: 1em }
- font matching

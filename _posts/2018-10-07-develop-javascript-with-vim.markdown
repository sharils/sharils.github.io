---
layout: post
title:  "Develop JavaScript With Vim"
date:   2018-10-07 18:03:03
categories: jekyll update
---

We are going to talk about developing JavaScript with Vim in 2018. This article
assumes the audience has very little knowledge about Vim and its ecosystem.

## [junegunn/vim-plug: Minimalist Vim Plugin Manager][1]

`vim-plug` allows you to install/update your Vim plugins efficiently. I used to
use pathogen and `git submodule`.

However, the first problem is that the more git submodules you have the slower
your `git status` command becomes unless you pass `--untracked-files=no` to
your git status command which I don't want to.

Second, it's `git submodule foreach git fetch` updates repositories in series
while `vim-plug` updates repo in parallel.

As for upgrading `vim-plug` itself, don't worry about it. It comes with a
`:PlugUpgrade` command for upgrading itself from Vim.

You can checkout [my .vimrc][2] for how to configure your Vim to use
`vim-plug`.

## [Valloric/YouCompleteMe: A code-completion engine for Vim][3]

`YouCompleteMe` is a auto-complete plugin that suggests fuzzy completions for
you when you are in the insert mode.

Fuzzy completion means that assuming you have a variable `currentUserProfile`
and when you type `cup` in the insert mode, `YouCompleteMe` will suggest
`currentUserProfile`.

To fully utilise its power, I recommend you to also run `yarn global add
typescript` to install `TSServer` so that it can suggest completions based on
your cursor in your JavaScript context. If you are worried that this means you
have to write TypeScript, nope, this is not the case. It's just using
`TSServer` for completion. You can still write JavaScript.

But simply installing `TSServer` isn't enough, you also have to install type
definitions for libraries you use. Say you use `jest` for testing, then you
also have to run `yarn add @types/jest` so that `YouCompleteMe` can provide
better suggestions.

You can find type definitions at [TypeScript Types Search][4].

You can also checkout [my config for YouCompleteMe][5]

## [w0rp/ale: Asynchronous linting/fixing for Vim and Language Server Protocol (LSP) integration][6]

`ale` provides super fast lint (even auto fix) for you when you are editing
your JavaScript files based on the linting tools defined in the package.json
file.

You can checkout [my config for ale][7]

## [jiangmiao/auto-pairs: Vim plugin, insert or delete brackets, parens, quotes in pair][8]

`auto-pairs` auto add closing single quote/double quote/bracket/square
bracket/curly bracket etc.

You can checkout [my config for auto-pairs][9]

## [editorconfig/editorconfig-vim: EditorConfig plugin for Vim][10]

`editorconfig-vim` makes your vim editor to respect `.editorconfig` file. You
sure don't want to be glared by your colleagues, right?

## [junegunn/fzf.vim: fzf vim][11]

`fzf.vim` allows you to do fuzzy search on files/buffer/maps/history/command
history/search history. You name it!

I also recommend installing [`rg`][12] along with `fzf.vim` for searching text
inside your project.

There is also a CLI version of [junegunn/fzf: A command-line fuzzy finder][13].
With the CLI version installed, you can type `vim **<TAB>` in your shell, then
jump right into the file you want to edit.

You can checkout [my config for fzf][14].

## [SirVer/ultisnips: UltiSnips - The ultimate snippet solution for Vim. Send pull requests to SirVer/ultisnips!][15]

`ultisnips` allows you to expand a trigger into a snippet. Say there is a
trigger `us` and it expands to `'use strict';`. Now type `us<TAB>` in insert
mode, then it expands to `'use strict';`.

But that's not all `ultisnips` can do, it also allows us to define priority and
context for snippets and have the same trigger expand to different snippets
based on it's context. The placement of your cursor can of course be defined
too.

Whether it be a good idea or not, say you want `a<TAB>` expand to `async` if the
same line contains `=>` or `function` or `method() {}` so that you can make
arrow function, function declaration, function expression or object method
async, and have `a<TAB>` expand to `await` in other circumstance. That's possible.

Or perhaps you want to have `border-top:` and `float:` expand to `borderTop:`
and `cssFloat:` respectively, that's totally possible.

You can check out [my config for ultisnips][16], [my javascript.snippets
file][17] and [my javascript snippets folder][18].

## [alvan/vim-closetag: Auto close (X)HTML tags][19]

`vim-closetag` allows you to close tag automatically, just like `auto-pair` but
for tags. E.g. type `<div>` in insert mode, and it automatically adds `</div>`
to be after your cursor.

It's also smart that  when you type `<hr>` it won't add `</hr>` and instead it
makes `<hr>` or `<hr/>` baesd on the file type.

You can check out [my config for vim-closetag][20].

NOTE: this config has to be loaded before `Plug 'alvan/vim-closetag'` otherwise it won't work.

## [hail2u/vim-css3-syntax: CSS3 syntax (and syntax defined in some foreign specifications) support for Vim's built-in syntax/css.vim][21]

`vim-css3-syntax` makes new CSS syntax (e.g. gap, column-gap) shown correctly.

## [ludovicchabant/vim-gutentags: A Vim plugin that manages your tag files][22]

`vim-gutentags` auto generates tags for your JavaScript projects. This is
important so that you can type `CTRL-]` or `gCTRL-]` on keywords in the normal
mode and jump to it's definition for efficient browsing/editing/

To make it work, you also need to config your `~/.ctags` file to know
JavaScript. That sounds complex, but don't worry, you can see [my .ctags
file][23] and it's based on [romainl/ctags-patterns-for-javascript: Exuberant
Ctags Patterns for JavaScript][24]

You can also checkout [my config for vim-gutentags][25]

## [moll/vim-node: Tools and environment to make Vim superb for developing with Node.js. Like Rails.vim for Node.][26]

`vim-node` allows you to type `gf` in a file path without a file extension to
jump to it. E.g. type `gf` above `"./currentUserProfile"` and jump to the
`"currentUserProfile.js"` file.

## [sheerun/vim-polyglot: A solid language pack for Vim.][27]

`vim-polyglot` provides syntax files for html5, jasmine, javascript, json, jsx,
scss, stylus, typescript, vue etc

## [honza/vim-snippets: vim-snipmate default snippets (Previously snipmate-snippets)][28]

`honza/vim-snippets` imports community-maintaining snippets for UltiSnips. If
you are that kind of person who likes to follow crows, this is for you.

But it doesn't conflict to have `honza/vim-snippets` and your own private
snippets coexist though.

[1]: https://github.com/junegunn/vim-plug
[2]: https://github.com/sharils/home/blob/master/.vimrc
[3]: https://github.com/Valloric/YouCompleteMe
[4]: https://microsoft.github.io/TypeSearch/
[5]: https://github.com/sharils/home/blob/master/.vim/plugged/after/plugin/YouCompleteMe.vim
[6]: https://github.com/w0rp/ale
[7]: https://github.com/sharils/home/blob/master/.vim/plugged/after/plugin/ale.vim
[8]: https://github.com/jiangmiao/auto-pairs
[9]: https://github.com/sharils/home/blob/master/.vim/plugged/after/plugin/auto-pairs.vim
[10]: https://github.com/editorconfig/editorconfig-vim
[11]: https://github.com/junegunn/fzf.vim
[12]: https://github.com/BurntSushi/ripgrep
[13]: https://github.com/junegunn/fzf
[14]: https://github.com/sharils/home/blob/master/.vim/plugged/after/plugin/fzf.vim.vim
[15]: https://github.com/sirver/UltiSnips
[16]: https://github.com/sharils/home/blob/master/.vim/plugged/after/plugin/ultisnips.vim
[17]: https://github.com/sharils/home/blob/master/.vim/plugged/after/UltiSnips/javascript.snippets
[18]: https://github.com/sharils/home/tree/master/.vim/plugged/after/UltiSnips/javascript
[19]: https://github.com/alvan/vim-closetag
[20]: https://github.com/sharils/home/blob/master/.vim/plugged/before/plugin/vim-closetag.vim
[21]: https://github.com/hail2u/vim-css3-syntax
[22]: https://github.com/ludovicchabant/vim-gutentags
[23]: https://github.com/sharils/home/blob/master/.ctags
[24]: https://github.com/romainl/ctags-patterns-for-javascript#generator-functions
[25]: https://github.com/sharils/home/blob/master/.vim/plugged/after/plugin/vim-gutentags.vim 
[26]: https://github.com/moll/vim-node
[27]: https://github.com/sheerun/vim-polyglot
[28]: https://github.com/honza/vim-snippets

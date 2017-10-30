+++
author = "Carsten Sandtner"
categories = ["pico-8", "gamedev", "atom"]
date = 2016-12-30
description = ""
draft = false
slug = "pico-8-and-atom"
tags = ["pico-8", "games", "development"]
title = "Pico-8 and atom"
summary = """
I love [Lexaloffles fantasy console](http://www.lexaloffle.com/pico-8.php). But I would like to use [Atom](https://atom.io/) for coding. Recently I've seen a screenshot by Jacopo Colò on Twitter
"""
+++

I love [Lexaloffles fantasy console](http://www.lexaloffle.com/pico-8.php). But I would like to use [Atom](https://atom.io/) for coding. Recently I've seen a screenshot by Jacopo Colò on Twitter

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Christmas afternoon, everyone chilling, me implementing a proper collision system. 💪 <a href="https://twitter.com/hashtag/pico8?src=hash">#pico8</a> <a href="https://t.co/d8h4VGpFmH">pic.twitter.com/d8h4VGpFmH</a></p>&mdash; Jacopo Colò (@jacopocolo) <a href="https://twitter.com/jacopocolo/status/813033799906951168">December 25, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I've asked him what kind of setup he is using. And it's a lot easier than I thought.

He uses Atom and Pico-8 in split-view. I've googled around and found some nice Atom extensions to be used with Pico-8. Here is my final setup:

* For syntax highlighting I'm using `language-pico8`by [Keiya Bachhuber](https://github.com/keiyakins/language-pico8)
* To be able to run my code directly from atom, I'm using `script` by [Kyle Kelley](https://github.com/rgbkrk/atom-script).

_Script_ needs some setup to run with Pico-8. Edit the configuration located in `~/.atom/packages/script/lib/grammars.coffee` and add

```
  Pico8:
    "File Based":
      command: "/Applications/PICO-8.app/Contents/MacOS/pico8"
      args: (context) -> ["-run",context.filepath]
```

Now you are able to run run `.p8`files using `CMD-SHIFT-P`and type `run`. Pico-8 will be started with your cartridge. Leave Pico-8 open and edit your code. Save and press `CMD-R` in Pico-8 to reload your cartridge. Now arrange your editor an Pico-8 windows as you like.

Thats all! Happy Coding!
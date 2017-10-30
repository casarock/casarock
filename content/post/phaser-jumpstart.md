+++
author = "Carsten Sandtner"
categories = ["HTML5", "gamedev", "development"]
date = 2015-09-27
description = ""
draft = false
slug = "phaser-jumpstart"
tags = ["phaser", "games", "development"]
title = "My PhaserJS jumpstart template"

+++

I love [PhaserJS](http://phaser.io) by Photonstorm. One of the best and most complete engine you can get for creating games with HTML5.

![PhaserJS Logo](/content/images/2016/01/phaser-logo.png)

I've created a [Boilerplate Project](https://github.com/appsbu-de/phaserBoilerplate) in February 2014 based on Grunt and a lot of tasks like concat, minimize etc. That's nice, if you want to create a game to be distributed sometime. For me the setup was to "complicated" when I just want to create a small prototype or proof of concept.

Therefore I've created a little [Jumpstart-Template](https://github.com/appsbu-de/phaserJumpstart). In fact it's just a directory structure to work with, based on [Phasers Templates](https://github.com/photonstorm/phaser/tree/master/resources/Project%20Templates). I've tried to have a clean repository where you are able to rename your project with some oneliners or in your editor.

My preferred way of using is to clone the repository and remove everything git related:

`git clone --depth=1 --branch=master https://github.com/appsbu-de/phaserJumpstart.git dirformynewrepo && rm -rf !$/.git`

Then I use perl (right, perl!) to rename the project classes:

`perl -pi -w -e 's/RENAME_ME/MYAWESOMENAME/g;' states/*.js index.html`

I'm shipping the latest minified Phaser, a structure for `preloader`, `boot`, `mainmenu` and `game` scene with boilerplate code. An `index.html` is being provided with some initial setup.

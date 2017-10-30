+++
author = "Carsten Sandtner"
categories = ["HTML5", "mobile", "cocoon", "cordova", "phonegap"]
date = 2015-09-20
description = ""
draft = false
slug = "html5-games-for-mobile"
tags = ["html5", "games", "development"]
title = "Bring HTML5 games to mobile"

+++

2007: Steve Jobs announced the first iPhone. No SDK! Everything is HTML5! Revolutionary. But what do we have now? Native Apps in native App Stores. I love HTML5 based games. What should I do if I want my game to be distributed on various App Stores?

There are several possible solutions:

1. Install the App using HTML5 WebApp Manifest and put your game on home screen.
2. Write a "wrapper" app using a WebView.
3. Use [Cordova](https://cordova.apache.org/)/[PhoneGap](http://phonegap.com/) or similar containers.

There are many more solutions. Let's got through the above mentioned topics.

1. Yes, probably the most HTML5ish solution. But you have to rely on the platforms rendering engine performance. At least on Android it may get interesting. Android Stock Browser isn't known to be the best. And if you want to use "native"-Like services like Game Center or Google Play, you may have _some_ trouble.

2. _Sounds_ like a good solution. Unfortunately it only sounds like a solution. iOS' WebView is not being known to be the fastest. WebGL? "Works", but... etc. It's a wide field of problems you may encounter. You have to support native wrapper for every ecosystem.

3. If you have to decide between the mentioned three solutions, this one is the _best_. You have Plugins for nearly everything (Sensors, Services like ads etc.). But they rely on a platforms native WebView-Implementation. Goto 2.

But why are WebViews slow? Desktop Browsers have a great performance nowadays. Why does at least Apple not support a WebView with proper WebGL performance? I assume  they don't want to see a new ecosystem grow beside their App Store(s). Every sold App and IAP are worth 30% of the Apps price. It's about the money, not a technical problem.

There is a an _other solution_ to bring a HTML5 based game into App Stores. A solution which includes a performant Canvas and WebGL. [Ludei's Cocoon](http://cocoon.io)! It's a _Cloud Compiler_. It compiles your HTML5 Web App to native mobile apps for Android, iOS, Tizen etc. The Canvas is WebGL enabled and does not rely on native WebView implementations. It is _fast_. CocoonJS has Javascript plugins with hooks to "native" services like _Game Center_, _Advertising_, _IAP_ and many more. It’s my preferred way at the moment.

Cocoon has a launcher App in every App Store. With this App you are able to test some demos and you could launch your HTML5 App from your URL to test and develop. You don’t have to compile your app during development.

I stick with Cocoon, even if it's commercial and a cloud compiler. You should try. It's free fro two projects.

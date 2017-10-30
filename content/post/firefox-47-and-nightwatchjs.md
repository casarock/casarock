+++
author = "Carsten Sandtner"
categories = ["nightwatch", "qa", "testing", "firefox", "selenium", "geckodriver"]
date = 2016-10-04
description = ""
draft = false
slug = "firefox-47-and-nightwatchjs"
tags = ["firefox", "nightwatch", "testing", "qa"]
title = "Firefox >47 and NightwatchJS"
summary = """
Get NightwatchJS-Tests working again while Firefox updates to a version >=47.0
"""
+++

## The challenge:
Get NightwatchJS-Tests working again while Firefox updates to a version >=47.0

## The problem:
Starting with Firefox 47, extension based version FirefoxDriver is no longer working.

## The Solution:
You have to use geckodriver for your nightwatch tests. Go to [Mozilla/Geckodriver](https://github.com/mozilla/geckodriver/releases) and download version **0.9.0**. Yes this isn't the latest version (V0.10.0 was the latest when I've written this post). V0.10.0 did **not** work.

## The Configuration:
```
{
    ...
    "selenium": {
        ...
        "cli_args": {
            "webdriver.gecko.driver" : "./bin/geckodriver"
        }
    },

    "test_settings": {
        "default": {
            ...
            "desiredCapabilities": {
                "browserName": "firefox",
                "marionette": true
            }
        },
        ...
    }
}
```
Where `./bin/geckodriver` is your path to the downloaded file.

And your tests are working in Firefox again.
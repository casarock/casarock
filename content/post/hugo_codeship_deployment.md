+++
author = "Carsten Sandtner"
categories = ["hosting", "hugo"]
date = 2017-11-14T10:30:00+02:00 
description = ""
draft = false
slug = "hugo-codeship-deployment"
tags = ["codeship", "hugo", "deployment"]
title = "Using Hugo with Codeship"
summary = """
After using Ghost powering my webpage, I’ve switched to [Hugo](https://gohugo.io/) - a static site generator written in Go. So far everything works like a charm and nearly out of the box. To be able to publish posts and updates from different machines I’m using a Github repository and deployment is being realised by using [Codeship](https://codeship.com/). 
"""
+++

# Deploy Hugo with Codeship
After some time using Ghost powering my webpage, I’ve switched to [Hugo](https://gohugo.io/) - a static site generator written in Go. So far everything works like a charm and nearly out of the box. To be able to publish posts and updates from different machines I’m using a Github repository and deployment is being realised by using [Codeship](https://codeship.com/). There a several good articles how to configure Codeship for Hugo deployment but I’ve ran into an problem compiling Hugo itself on Codeship.  For a Basic setup I’ve used [Ryan Tiffanys great explanation](http://tinylab.info/automatic-hugo-deployment-using-codeship/).

If you want to use a current version of Hugo, you need to install a new _Go_ version at _Codeship_. As they are using V1.4 out of the box, your build will fail. The solution is to add a setup script provided in their [scripts repository](https://github.com/codeship/scripts/blob/master/languages/go.sh). I’m using Go 1.9.2 and my script looks like this

```bash
#!/bin/bash
# Install a custom Go version, https://golang.org/

GO_VERSION=${GO_VERSION:="1.9.2"}

CLEANED_PATH=$(echo "${PATH}" | sed -r 's|/(usr/local\|tmp)/go(/([0-9]\.)+[0-9])?/bin:||g')
CACHED_DOWNLOAD="${HOME}/cache/go${GO_VERSION}.linux-amd64.tar.gz"
 
# configure the new GOROOT and PATH
export GOROOT="/tmp/go/${GO_VERSION}"
export PATH="${GOROOT}/bin:${CLEANED_PATH}"
# no set -e because this file is sourced and with the option set a failing command
# would cause an infrastructure error message on Codeship.
mkdir -p "${GOROOT}"
wget --continue --output-document "${CACHED_DOWNLOAD}" "https://storage.googleapis.com/golang/go${GO_VERSION}.linux-amd64.tar.gz"
tar -xaf "${CACHED_DOWNLOAD}" --strip-components=1 --directory "${GOROOT}"
# check the correct version is used
go version | grep "${GO_VERSION}"
```

Add the script in the *setup commands* section

![Setup Commands](/img/codeship_commands.png)

Now my build works.

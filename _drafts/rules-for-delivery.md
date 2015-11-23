---
layout: post
title: Rules for Software Delivery ...
description: "Rules for delivering your software" 
category: articles
tags: [ software development, software delivery ]
image:
  feature: squarepeg-round-hole.jpg
---

These are rules I would love to enforce for any 3rd party application vendor
when you're shipping stuff to me. I love the [12 Factor](http://12factor.net/)
rules but they are lengthy. I get most of the value from these... 

### Versioning
* Version all artifacts
* Use [Semantic Versioning](http://semver.org/)
* Artifacts are sacrosanct - once an artifact is produced at a specific
version, it is essentially a shippable product. Don't open it up to change 
something. Need to fix something? Revision and fix forward.

### Packaging
* Package using a non-distribution & non-platform specific package format
first (e.g. .zip/.tar.gz) Then build distribution / platform specific
packages.
* If you're using a binary packaging model (e.g. rpm), make your source
available for packaging.
* Include the version in the package name Don't package up third party open
source tools and deliver them on someone else's behalf.
* List dependencies in the packages. If possible, don't tie to specific minor
versions of tools. i.e. depend on MySQL 5.1 not MySQL 5.1.73
* Include documentation in your package about installing & configuring your
software. A README.txt or README.md is pretty normal. 
* Please do not add do a bunch of pre or post install magic in your packaging upon
installation. Copying files to directories, setting up permissions, relevant
users etc. is all fine. 

### Installation
* Where using distribution specific packages, a simple yum install
top-level-package  should install your package and all of it's dependencies.
* Please try and adhere to [FHS](http://www.pathname.com/fhs/) and the 
distributions standards for installation on *nix operating systems. 
* Please integrate in with the local system startup for the distribution you're
targeting when providing distribution specific packages.
* Install with sane defaults that preferably allow me just to start your
application without configuring stuff, or with minimal (obvious)
configuration. Helps me play with stuff in dev.

### Support / Production
* LTS - Have a support strategy that lines in with common distribution LTS
support strategies.
* Have a debug mode which enables more verbose logging and allows you to
capture inputs & outputs from your various channels/services. Particularly
in a distributed application. 
* If configuration is complicated (i.e. you need to edit more than one file),
provide a way to show configuration 

_With the amount of code, libraries and full blown systems now out there,
delivery is becoming more important. Don't try and re-invent the wheel. Plenty
of other people have been doing this for some time._

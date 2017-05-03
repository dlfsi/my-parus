---
layout: post
title: A Github blog based on HEXO
date: 2016-12-20
comments: true
external-url:
categories: Github
---

> Github + HEXO on Windows 10 64bit



## Install HEXO
Before HEXO installation, it's a must to install
- Node.js
- Git

After installation, open Git Shell, type in or execute:
```shell
npm install -g hexo-cli
```
if success, then create a local directory, let's say "deepai", then execute below commands:
```shell
hexo init deepai
```
structure of deepai directory looks like:
```
.
|-- node_modules
|-- scaffolds 
|-- source
|-- themes
|-- _config.yml
|-- package.json
```
then execute:
```shell
hexo s
```
if message shows "Hexo is running at http://localhost:4000/", then open web browser to access the url, the hello world page will show if all things go well.

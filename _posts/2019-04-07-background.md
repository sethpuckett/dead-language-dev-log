---
layout: post
title: Background
categories: [development, art]
tags: [art, minigame prototype]
fullview: false
comments: false
---

Added a tiled background image that I got from Open Game Art. It's a small change, but it looks a lot better.

![Tiled Background](/assets/media/posts/2019-04-07/background.gif "Tiled Background")

``` js
  this.background = this.add.tileSprite(0, 0, this.cameras.main.width, this.cameras.main.height - 50, 'grass');
  this.background.setOrigin(0, 0)
  this.background.setDepth(-1)
```
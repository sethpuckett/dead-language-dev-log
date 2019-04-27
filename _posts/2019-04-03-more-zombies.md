---
layout: post
title: More Zombies
categories: [development, learning]
tags: [zenva, minigame prototype]
fullview: false
comments: false
---

I added a few more things to get a basic prototype working. I’m starting to have a few ideas about the kinds of classes and control flows I’ll need to keep this maintainable. My next steps are adding support for multiple correct answers (e.g. “time” can be “vez” or “tiempo”), keeping track of successful responses, implementing a game timer, and keeping track of misses/freeing up words (currently zombies just walk off the bottom of the screen forever).

The Zenva tutorials have been helpful so far. They are at least showing me what's available in Phaser. And they're a good jumping off point for digging into the documentation.

![Multiple Zombies](/assets/media/posts/2019-04-03/multi-zombie.gif "Multiple Zombies")


``` js
minigame.getSpawnLocation = function() {
  // TODO: don't hard code padding
  return Phaser.Math.RND.between(25, this.cameras.main.width - 25)
}

 minigame.getSpawnDelay = function() {
  return this.baseSpawnRate + Phaser.Math.RND.between(-this.spawnRange, this.spawnRange)
}

 minigame.getFallSpeed = function() {
  // TODO : don't hard code this equation here
  return (this.baseFallSpeed + Phaser.Math.RND.between(-this.fallRange, this.fallRange)) / 40
}

 minigame.spawnZombie = function() {
  // TODO: add zombie class to store extra data
  let zombie = this.add.sprite(
    this.getSpawnLocation(),
    -35, // TODO: don't hard code this here. Should be in config or init
    'zombie'
  )
  zombie.setScale(.6, .6) // TODO: Don't hard code this
  zombie.speed = this.getFallSpeed()
  // TODO: put font in config
  // TODO: don't hard code position (need to calculate center)
  // TODO: pulling language1 off this is ugly. Move to helper class?
  zombie.text = this.add.text(zombie.x - 15, -10, this.reserveVocabWord().language1, { font: '16px Courier' })

   this.zombies.push(zombie)
  this.activateSpawnTimer()
}
```
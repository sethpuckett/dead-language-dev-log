---
layout: post
title: The First Zombie
categories: [development]
tags: [text, input, minigame prototype]
fullview: false
comments: false
---

It’s been a while. I was out of town for a week and didn’t work on this at all. The Phaser course is going well. I don’t know the best way to structure a large javascript/phaser application, so my one file game is getting a little bloated. I put some hacky code together and managed to get a sprite and some text on screen, and some logic to compare submitted guesses against the value on screen. It’s a nice start. The zombie graphic came from [here](https://opengameart.org/content/pixel-zombie). OpenGameArt.org is a great community with helpful people and it’s full of useful resources. The creator of this sprite says they are with lonegames.net, but the website is defunct.

```js
  this.zombie = this.add.sprite(100, 0, 'zombie')
  this.zombie.setScale(.6, .6)
  this.zombieSpeed = .2
  this.zombieText = this.add.text(90, 30, vocab.words[0].language1, { font: '16px Courier' })
```
```js
  minigame.update = function() {
    this.zombie.y += this.zombieSpeed
    this.zombieText.y += this.zombieSpeed
  }
```
```js
  minigame.submitAnswer = function() {
    if (this.textEntry.text === vocab.words[0].language2) {
      this.zombie.destroy()
      this.zombieText.destroy()
    }
    this.textEntry.text = ''
  }
```

![Simple Zombie Sprite](/assets/media/posts/2019-04-02/zombie.gif "Simple Zombie Sprite")
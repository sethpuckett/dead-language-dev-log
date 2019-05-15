---
layout: post
title: Vocab Study
categories: [development]
tags: [vocab study, target practice]
fullview: false
comments: false
---

I want to make sure this isn't just a "review" game for people that already know the language. I want people to be able to use it to learn new vocab and grammar as well. The game as it is now is pretty much impossible if you don't already know the words, so I'm working on a study screen that will take the form of a no-pressure bottle shooting minigame.

It took a little while to get the dynamic positioning & resizing of the vocab in this screen looking good, but I'm happy with the results.

![Vocab List](/assets/media/posts/2019-05-07/vocab-study.png "Vocab List")

I also abstracted all the logic for the HUD into a reusable manager class, since there are already 2 screens that use it, and there will likely be more. It takes a config object that determines which elements to display, how much health the player has, etc.

```js
    this.hudManager.createHud({
      ...minigame.ui.hudConfig,
      startHealth: this.currentLevel.startHealth,
      maxHealth: this.currentLevel.maxHealth,
    });
    this.hudManager.setSubmitCallback(this.submitAnswer);
```

And finally I updated the title screen to allow the player to choose whether to start the game or go to the (unfinished) target practice screen. This will change when I start adding more levels, but it works for a demo.

![Title Menu](/assets/media/posts/2019-05-07/menu-options.gif "Title Menu")
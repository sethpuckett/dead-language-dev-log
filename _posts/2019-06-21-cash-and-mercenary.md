---
layout: post
title: Cash and Mercenary
categories: [development]
tags: [minigame, cash, items, mercenary]
fullview: false
comments: false
---

This week I got started on the infrastructure for the next big game enhancement... items!

One of the problems with the game currently is that when a word shows up on the screen the player either knows it or they don't. If they know it they can type the translation, no problem. But if they don't know it they have no choice but to watch the zombie slowly make its way to the bottom and attack. This doesn't make for a very fun game.

I want to improve the resource management aspect of the game by adding items that can help the player down the road. This forces the player to make a choice: Do I focus on keeping the zombies under control, or do I risk ignoring them for a moment and getting items which might help out later.

The first item I've added is cash. Collecting cash allows the player to pay a mercenary to take out zombies for words the player doesn't know. If the player types out the word in English the mercenary will kill the zombie and take $100. If the player doesn't have enough money the mercenary will refuse to help.


```js
switch (itemType) {
  case minigameItems.cash:
    this.cash += this.currentLevel.items.cashAmount;
    this.hudManager.setCash(this.cash);
    this.statusManager.setStatus({
      message: minigame.statusMessages.cashReceived,
      displayTime: minigame.statusTime,
    });
    break;
  default:
    throw Error('invalid itemType');
}
```

Eventually I want to add a smart study system that will keep track of the words a player has difficulty with and show those words more often. The ultimate goal here is to help the player learn Spanish, and that is not served if they can get around learning certain words through the use of items. So in the end using the mercenary will be a short-term strategy, because the word will show up again and again until the player is actually able to translate it without assistance.

![Cash and Mercenary](/assets/media/posts/2019-06-21/cash-and-mercenary.gif "Cash and Mercenary")

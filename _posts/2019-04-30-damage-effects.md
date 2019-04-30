---
layout: post
title: Damage Effects
categories: [development, art]
tags: [minigame prototype,]
fullview: false
comments: false
---

Lots of code organization in the last few days. I'm trying to get the giant minigame class under control by separating things out into various manager classes.

There are a couple of graphical updates as well. The zombies now play a death animation and leave behind a blood splatter when they're killed.

![Zombie Death](/assets/media/posts/2019-04-30/zombie-death.gif "Zombie Death")

I also added some camera effects and a status message when the player takes damage. Phaser makes the flash & screen shake really easy, and it looks pretty nice.

![Damage Effect](/assets/media/posts/2019-04-30/damage.gif "Damage Effect")
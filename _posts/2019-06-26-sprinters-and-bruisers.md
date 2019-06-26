---
layout: post
title: Sprinters and Bruisers
categories: [development]
tags: [minigame, enemies, sprinters, bruisers, items]
fullview: false
comments: false
---

I added the first special zombies this week. Sprinters move at double speed, and bruisers are slightly slower, but take 3 shots to kill.

I had to rework a lot of the zombie logic to allow for the new behavior. It's much more flexible now.

I also re-colored the zombie sprites to make it more obvious when a special zombie is onscreen. The normal zombies are all green and gray now, and the special zombies are red. If I ever get around to doing a major graphical overhaul I would like to make this difference more than just color-based. There are a lot of color blind folks out there for whom the red/green differentiation isn't going to be very useful.

I'm hoping these new types make gameplay a little more interesting since now it doesn't always make sense to focus on the closest zombies. The player needs to plan ahead a little bit.

I'm also planning to add some additional items to make dealing with special zombies a little easier. This should add an additional layer of decision making.

Speaking of items, I've added food to the game! Currently food behaves just like the cash item, accept when it is retrieved the player gets 1 point of health back.

The spawn rates for items and special zombies is fully configurable, which should allow me to make some pretty interesting specialty levels.

![Sprinters and Bruisers](/assets/media/posts/2019-06-26/sprinters-and-bruisers.gif "Sprinters and Bruisers")

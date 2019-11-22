---
layout: post
title: Improved Endgame Screen
categories: [development]
tags: [endgame, stats]
fullview: false
comments: false
---

My latest update is an improved endgame screen. Until now when the timer ran out in the minigame the game abruptly switched to a bland endgame screen that just stated whether or not the player had won or lost and gave a simple menu to choose where to go next.

Now when the timer runs out a modal is displayed that chooses one of several random messages depending on whether the player one or lost. When the modal is closed the game transitions to the endgame screen, which now shows a list of stats about the player's performance. These include:

* Zombies killed
* Hits taken
* Cash collected
* Food eaten
* Merc payments
* Shots fired
* Accuracy
* Letter grade based on above stats

The letter grade is calculated based on the number of hits taken, the number of times the mercenary was used, and the player's shot accuracy.

```js
calculateLetterGrade(params) {
  // loss is an automatic F
  if (params.status === endgame.lose) {
    return letterGrades.f;
  }

  const hitsTakenScore = this.getHitsTakenScore(params.hitsTaken);
  const mercScore = this.getMercenaryScore(params.mercenaryKills);
  const accuracyScore = this.getAccuracyScore(params.shotsFired, params.shotsHit);

  return this.getGradeFromScore(hitsTakenScore + mercScore + accuracyScore);
}
```

Additionally, the screen shows a field of dead zombies if the player won the round, or a horde of stampeding zombies if the player lost.

I think it's a smoother, more interesting experience now. Eventually I want to persist the stats to the player profile and display the "Best Grade" for each completed stage, and provide overall stats. I also want to add the ability to view the words that the player missed in the stage to help them study problem vocab.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ue4ISOTQ2UU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
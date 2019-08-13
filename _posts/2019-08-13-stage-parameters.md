---
layout: post
title: Stage Parameters
categories: [development, level design]
tags: [game progress]
fullview: false
comments: false
---

One worry I have is that the game will feel too repetitive if every stage is exactly the same - just with new vocab. To alleviate this I want to have different parameter settings that can be applied to stages to make them feel varied.

For example, some stages might have an abundance of sprinters or bruisers. Or some stages might be longer than usual. Or sometimes the zombies might come in bursts with lots of zombies vs. a steady stream of zombies.

I would also eventually like to add 'team leader' system in which the player can unlock and choose team leaders that confer benefits, e.g. more shotguns spawn or mercenary is cheaper, etc.

But I'm getting ahead of myself. The latest update is in support of varying staging parameters. Now I can create named sets of stage parameters and for each stage list the names of potential parameters that can be used there. This also allows me to do things like make review stages a little longer, and make the initial stages a little easier while the player is figuring things out.

```js
getStageParams(stageId) {
  const paramMap = stageParameterMap.find(p => p.stage === stageId);
  if (paramMap == null) {
    throw Error(`No stage parameters available for stageId: ${stageId}`);
  }
  const paramId = this.getRandomParameterId(paramMap.availableParameters);
  const stageParams = stageParameters.find(p => p.id === paramId);
  if (stageParams == null) {
    throw Error(`No stage parameters found with id: ${paramId}`);
  }
  return stageParams;
}
```

An additional change I've made is showing the correct answer when a zombie attacks. It's a little frustrating without this, because a player is likely to see the same word several times in a stage, and if they don't get it the first time they're probably not going to get it in subsequent appearances. Showing the answer acts as a reminder for the player and gives them a chance to get it right next time. The flashing answer also appears when the mercenary is used.

![Flashing Answer](/assets/media/posts/2019-08-13/flashing-answer.gif "Flashing Answer")

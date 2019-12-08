---
layout: post
title: Persisting and Displaying Stats
categories: [development]
tags: [stats, game progress, firebase]
fullview: false
comments: false
---

With my last update I started calculating and displaying stats on the endgame screen of each stage. Now I'm saving those stats to the player profile and displaying the best grade for each stage on the map screen. I hope this will encourage players to not just try to pass each stage, but to go for an 'A'.

I wasn't sure if it would be best to save the stats as a new collection in Firebase or as an array of maps on the existing profile. I ended up going with the array of maps. That makes it easier to keep all the profile data together and load it with a single query. This seems to be working fine. Storing it as a collection would have expanded my querying options, but it was not worth the overhead, and I don't need that flexibility right now anyway.

I only want to store the "top" stats for each stage. When the player replays a stage and does better the old stats are replaced. This made the code a little convoluted because I couldn't find a way to remove the old stats and add the new with a single Firebase query. So it requires multiple saves & callbacks. But it works well enough.

```js
saveStatsIfBetter(stats, callback) {
  if (this.areStatsBetter(stats)) {
    const oldStats = this.getStats(stats.stageId);
    if (oldStats != null) {
      this.removeStats(oldStats, () => {
        this.saveNewStats(stats, callback);
      });
    } else {
      this.saveNewStats(stats, callback);
    }
  } else {
    callback(true);
  }
}
```

![Display Grade](/assets/media/posts/2019-12-07/display-grade.png "Display Grade" )
---
layout: post
title: Music & Sound Effects
categories: [audio]
tags: [music, sound effects, minigame]
fullview: false
comments: false
---

I've added all the music and sound effects that I need for now. I'm limited to what came in the bundle I purchased, so I had to make a few compromises, but I'm generally pretty happy with how things are turning out. The music is pretty inconsistent from screen to screen, but it works for now.

I've improved the music start delay and fade out on screen transition, so the switch is not so abrupt. I also added support for tracks that feature an intro in addition to a main audio loop. The minigame uses such a track.

```js
playMusic(override = false) {
  if (this.optionsManager.musicEnabled() || override) {
    if (this.musicState === STOPPED) {
      if (this.musicIntro != null) {
        this.playMusicIntro();
      } else {
        this.playMainMusicLoop();
      }
    } else if (this.musicState === INTRO_PAUSED) {
      this.resumeMusicIntro();
    } else if (this.musicState === PAUSED) {
      this.resumeMainMusicLoop();
    }
  }
}
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/r1W2X9P1_bQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
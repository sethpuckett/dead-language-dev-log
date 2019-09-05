---
layout: post
title: Audio & User Options
categories: [development, audio]
tags: [music, sound effects, user options]
fullview: false
comments: false
---

I've started adding music and sound effects to the game, currently all of which came from an indie game dev bundle. I know a lot of folks will want to be able to control this, so I've also added an options menu. Preferences are saved to a user's profile, so they only need to be set once.

```js
playMusic() {
  if (this.optionsManager.musicEnabled()) {
    this.music.play({ loop: true });
    this.musicState = PLAYING;
  }
}
```

I've added a couple other menu options as well, but currently only the audio settings are hooked up to anything.


<iframe width="560" height="315" src="https://www.youtube.com/embed/0A5Im4_S0Ac" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

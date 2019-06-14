---
layout: post
title: Locked Lessons
categories: [development]
tags: [level select, game progression]
fullview: false
comments: false
---

Just a few more updates to the map now that the game persists completion status.

I added logic to persist the last selected location on the map. It was very annoying that every time I returned to the map I was back at lesson 1, stage 1. Now when you leave the screen (or even the whole game) and come back the map & stage selection will be right where you left them.

```js
setMapPosition(lessonId, stageId, callback) {
  const user = this.db.getCurrentUserProfile();
  if (user != null) {
    user.update({ mapState: { lesson: lessonId, stage: stageId } }).then(() => {
      this.db.loadUserProfile();
      if (callback != null) {
        callback(true);
      }
    });
  } else if (callback != null) {
    callback(false);
  }
}
```

I also updated the stage info component to differentiate between normal stages and review stages, as well as cleared and non-cleared stages. I'm trying to make it as clear as possible what has been completed and what hasn't been completed yet.

Map pins are now color coded based on whether they are cleared, available, or locked. A lesson is locked if any prerequisite lessons have not been cleared. Players are also prevented from selecting locked lessons now.

![Locked Lesson](/assets/media/posts/2019-06-14/locked-lesson.gif "Locked Lesson")

The map screen is in a pretty good place for now. I'm going to shift gears and get back to enhancing the main vocab game. I want to add items, different zombie types, and new weapons. I'm hoping those will make it more fun to play.
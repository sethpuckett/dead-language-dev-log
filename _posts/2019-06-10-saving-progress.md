---
layout: post
title: Saving Progress
categories: [development]
tags: [level select, game progress, review, firebase]
fullview: false
comments: false
---

I've been working on persisting player progress to the database. Now when a stage is cleared it's added to a list of 'cleared stages' for the logged in player. The map has a different icon for cleared stages.

Right now players can play the game without being logged in, but nothing is saved, so they can't make it very far. Eventually I would like to have a simple 'demo mode' for non-logged in users to showcase the game and encourage folks to make an account. But that's way down the line.

```js
const user = this.db.getCurrentUserProfile();
if (user != null) {
  user.update(
    { stagesCompleted: firebase.firestore.FieldValue.arrayUnion(stageId) }
  ).then(() => {
    this.db.loadUserProfile();
    callback(true);
  });
}
```

I also added some logic for the review stage. Now the review stage cannot be selected until all other stages in the lesson have been completed. Once it's unlocked and a players selects it they are warned that it's going to be tougher. Once in the minigame the review stage loads the vocab words for every stage in that lesson.

Next up is saving lessons as 'completed' once all stages are cleared and unlocking the follow up lessons.

![Saved Progress](/assets/media/posts/2019-06-10/save-progress.gif "Saved Progress")
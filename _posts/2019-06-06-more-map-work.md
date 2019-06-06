---
layout: post
title: More Map Work
categories: [development]
tags: [level select, ui, firebase]
fullview: false
comments: false
---

I'm making good progress on the map screen. It still needs work, but the basic flow is there. Now the player can choose a lesson, choose a stage, and then go to the practice screen or straight into the game. And the player can also press 'Esc' at any time to go back to the previous step.

The modal at the end is reusable and dynamically sized so I can make these kind of option modals anywhere without much work now.

The map screen code could use a lot of cleanup, but at least it works.

```js
createStageSelectedModal() {
  this.disableInputHandling();
  this.stageModal = new ChoiceModal(
    this, townMap.choiceModals.stageSelected.text, townMap.choiceModals.stageSelected.choices
  );
  this.stageModal.draw();
  this.stageModal.enableInputHandling();
  this.stageModal.setCloseCallback((index) => {
    this.stageModal.disableInputHandling();
    // TODO: move these index values to config or something
    if (index === 0) { // start game
      this.nextScreen = screens.minigame;
    } else if (index === 1) { // target practice
      this.nextScreen = screens.vocabStudy;
    }
    this.cameras.main.fade(townMap.screenFadeTime, 0, 0, 0, false, this.fadeCallback);
  });
  this.stageModal.setCancelCallback(() => {
    this.stageModal.disableInputHandling();
    this.stageModal.close();
    this.stageSelectManager.enableInputHandling();
  });
}
```

![Map Screen](/assets/media/posts/2019-06-06/map-screen.gif "Map Screen")
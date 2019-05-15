---
layout: post
title: Target Practice
categories: [development, art]
tags: [vocab study, target practice, modals]
fullview: false
comments: false
---

I've put in some more work on the vocab study screen.

I added a reusable popup modal class so I can add instructional text throughout the screen. Right now I have to specify the size, but I want to make the modal automatically resize based on the size of the text passed in. That's the next step.

```js
this.modal = new Modal(
  this,
  vocabStudy.modals.tutorial.width,
  vocabStudy.modals.tutorial.height,
  vocabStudy.modals.tutorial.text
);
this.modal.draw();
this.modal.enableInputClose();
```

![Practice Modal](/assets/media/posts/2019-05-15/practice-modal.gif "Practice Modal")

The target practice mini game is mostly done now, too. Words are shown one at a time in random order with no time limit. Getting it correct explodes the bottle and shows the word in green. Missing shows the word in red. My thinking is this will make it easier to study just the words you got wrong after a practice session.

The bottle sprite came from the graphics pack I bought, but I had to do the explode animation myself.

![Target Practice](/assets/media/posts/2019-05-15/target-practice.gif "Target Practice")

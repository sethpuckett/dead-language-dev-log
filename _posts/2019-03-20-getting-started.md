---
layout: post
title: Getting Started
categories: [development, planning, learning]
tags: [trello, zenva, learning, text, input, github, minigame prototype]
fullview: false
comments: false
---

I’ve started an online course with Phaser through [Zenva Academy](https://academy.zenva.com/). I’ve never heard of this site, there weren’t a lot of reviews, and it cost $60, but I really wanted some kind of structured learning course. As is typical in tech, there are a thousand “Hello World” tutorials, but then it’s impossible to find instructional material for the next step. So I’m hoping this course will at least get me to the point where I’m comfortable enough with the framework to figure things out from the documentation.

I made a design document and Trello board for this project. I’m laying out my ideas and I added some epics and themes. Hopefully this helps keep me organized.
![Trello Board](/assets/media/posts/2019-03-20/trello.png "Trello Board")

I made a [Github repo](https://github.com/sethpuckett/dead-language) last night and pushed a couple commits. The first dev task is already proving a little tricky. Phaser does not have native text input support, so I have to add it myself. This means listening for player input, updating a text object based on the keystroke, and updating the display with the modified text. The code is just a proof of concept, but it’s a start.
{% highlight javascript %}
minigame.create = function() {
  this.textEntry = this.add.text(10, 50, '', { font: '32px Courier', fill: '#ffff00' });
  this.keys = this.input.keyboard.addKeys('SPACE, BACKSPACE, ENTER')

   this.input.keyboard.on('keydown', function (event) {
    if (event.keyCode === this.keys.BACKSPACE.keyCode  && this.textEntry.text.length > 0) {
      this.textEntry.text = this.textEntry.text.substr(0, this.textEntry.text.length - 1);
    } else if (isLetter(event.keyCode)) {
      this.textEntry.text += event.key;
    }
  }, this);
}
{% endhighlight %}
![Text Input](/assets/media/posts/2019-03-20/typing.png "Text Input")
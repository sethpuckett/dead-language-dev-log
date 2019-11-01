---
layout: post
title: Smooth Font
categories: [development]
tags: [user options, fonts]
fullview: false
comments: false
---

One bit of feedback I’ve gotten from several people is that the pixelated font, while fitting for the game, can be difficult to read. This is especially true when there’s a screen full of zombies barreling towards the player. In an effort to make the game as accessible as possible I’ve added the option to change the font to a smoother, more-readable one.⁣

I went with Verdana for the new font. I don't know much about fonts, but I know that Verdana was designed to be easy to read on computer screens, so it made sense. As with the original Blue Sky font, I converted the TTF font to a bitmap font using the handy <a href="http://kvazars.com/littera/">Littera</a> tool.

This update was a bit of a pain since I had hard coded the original font all over the place. I've fixed that so no now the font is read from user options. This configuration should make it easier to change or add fonts in the future, as well.

```js
getFontForUserOption(value) {
  if (value === userOptions.values.pixel) {
    return fonts.blueSky;
  }
  if (value === userOptions.values.smooth) {
    return fonts.verdana;
  }

  throw Error(`Invalid selected font option: ${value}`);
}
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/ap2dxB91IB4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
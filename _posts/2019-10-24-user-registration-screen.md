---
layout: post
title: User Registration Screen
categories: [development]
tags: [game progress, firebase, bugs]
fullview: false
comments: false
---

I reached to friends and family recently to get some feedback on the game. Until now most of the people that have played the game have had me over their shoulder telling them what to do. I was curious what people would think without my support. Would the game make sense? Would they be able to register an account? Would it be fun?

I got some good feedback, and I have a few things I want to work on sooner rather than later. One very common problem was that the game sometimes crashed when registering an email address. This is a problem I noticed already, and implemented a dumb-but-quick solution, which obviously didn't work.

The problem is with the way Firebase handles authentication. Firebase Auth and Firestore do not talk to each other at all. Firebase does not allow custom data to be stored in the auth system, it has to be put in Firestore. Unfortunately Firestore does not know about the auth system, so associating profile data with a particular user becomes tricky.

The solution I came up with is Google Function that fires whenever a new user is registered. It takes the username from the auth system and creates an associated document in the Users collection in Firestore. When the process is finished it works great. A users logs in with the auth system, and then the game is able to retrieve their profile from Firestore with their User ID.

Unfortunately, there is a brief lag between when the account is created in the auth system and when the user document is created in Firestore. This lag can be a few milliseconds up to several seconds. My old approach of immediately reloading the game when a new user was registered meant sometimes there was no user profile yet for that user, which caused the game to crash.

I've been working on a fix for that and I'm happy to say I got it working. The game still reloads immediately, but now the database logic is able to determine if the user profile does not exist yet, and sends the player to a new Registration/Loading screen to let them know something is going on. This screen pings the database every second or so until the profile exists, and then it starts the game.

This approach worked well in my testing. We'll see if I continue getting reports of crashes.

```js
  onProfileLoad(loginState) {
    if (loginState === LogInState.REGISTERING) {
      this.nextScene = screens.registration;
    } else {
      this.nextScene = screens.loading;
    }

    if (this.startOnLoadComplete) {
      this.startNextScene();
    }
  }
```

<iframe width="560" height="315" src="https://www.youtube.com/embed/1VjpkAOkHYc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
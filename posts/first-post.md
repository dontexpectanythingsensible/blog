extends: default.liquid

title: Fish game started!
date: 8 March 2017 12:00:30 +0000
---

# Fish game devlog

When I was playing Stardew Valley last year, I really enjoyed the fishing mini-game, so decided to make my own version which can also be played on a phone. The fishing game will be pretty similar to Stardew Valley's version: you will move a bar up and down the screen based on clicks or taps to try to keep the bar over a fish. While the bar is over the fish, a progress meter fills up, and when the bar is not over the fish, the meter empties. If the meter fills entirely you've caught the fish, and if it empties then the fish has escaped and you lose.

To keep things interesting, you won't know the type of fish until it's been caught; instead, a generic fish icon will be used, although the speed and frequency of movement will change depending on the type of fish. There will also be collectables in the fishing screen which appear away from the fish, so you have a choice between carrying on catching the fish or risking it get away by going for the collectable. Both these elements are present in the Stardew Valley version, and are both things I really enjoyed.

##Tools

I'm going to use Unity to make this game - I haven't used Unity before, but there are a lot of tutorials and a large community around it which should make it relatively straightforward to learn how to use, and also offers export to phone apps. With my other games, I've used Javascript, so have had to use wrappers like Cordova or Electron to get non-web versions of the game, so using Unity means I can have one codebase which can export to multiple platforms with a click of a button. Joy!

## Progress pics

Quick prototype: I dragged a sprite into Unity and it rendered, so here it is!

![](../img/first-screenshot.png)


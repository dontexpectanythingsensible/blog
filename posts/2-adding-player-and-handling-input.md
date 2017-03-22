extends: default.liquid

title: Adding a player and handling input
date: 11 March 2017 12:00:00 +0000
description: Being able to interact with the game is usually a good idea.
---

# Adding a player and handling input

Generally, games involve a player being able to interact with things, and my fish game was completely lacking these. First things first: a player character is now in the game:

![The player character](img/player.png)

Lovely, isn't it? The player character is just a rectangle; I'll probably keep this in the final game since you need to be able to see if you're over the fish, and this is nice and thin at the moment.

The player needs to be able to move up and down to chase the fish, so I've added basic keyboard controls (just the up key). Gravity will pull the player down, so you can't directly control your height - you can move up the screen, but will have to rely on gravity if the fish moves down the screen. This adds a bit of challenge: if you could precisely move up and down the screen, it would be far too easy to keep your avatar over the target.

For phones I'll implement tap to move up, and this one-key approach should make changing key-bindings easier in the future.

<div class="video">
  <iframe src='https://gfycat.com/ifr/PersonalTintedBlackfly' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe>
</div>

## Collisions

To catch a fish, you need to keep the player over the fish until the progress bar has been filled, so being able to detect whether or not the player is over the fish I added collision detection. Unity has a few methods which make this pretty easy; I'm using the trigger methods, since I only need to detect whether the player and fish are overlapping. The other set of methods are collider methods, which should be used when two components need to apply forces to each other.

<!-- TODO: video of hovering over fish with console -->

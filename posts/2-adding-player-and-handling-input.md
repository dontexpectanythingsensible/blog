extends: default.liquid

title: Adding a player and handling input
date: 11 March 2017 12:00:00 +0000
---

# Adding a player and handling input

Generally, games involve a player being able to interact with things, and my fish game was completely lacking these. First things first: a player character is now in the game:

TODO add player sprite image

The player character is an abstract image of a rectangle; I'll probably keep this in the final game since you need to be able to see if you're over the fish, and this is nice and thin at the moment.

The player needs to be able to move up and down to chase the fish, so I've added basic keyboard controls (just the up key). Gravity will pull the player down, so you can't directly control your height - you can move up the screen, but will have to rely on gravity if the fish moves down the screen. This adds a bit of challenge: if you could precisely move up and down the screen, it would be far too easy to keep your avatar over the target.

For phones I'll implement tap to move up, and this one-key approach should make changing key-bindings easier in the future.

## Collisions

To catch a fish, you need to keep the player over the fish until the progress bar has been filled, so being able to detect whether or not the player is over the fish I added collision detection.


- added player sprite
- key handling
- player needs to collide with fish
- isTarget
- Collided vs collision

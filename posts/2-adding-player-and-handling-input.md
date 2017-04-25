extends: default.liquid

title: Adding a player and handling input
date: 11 March 2017 12:00:00 +0000
description: Being able to interact with the game is usually a good idea.
---

# Adding a player and handling input

Generally, games involve a player being able to interact with things, and my fish game was completely lacking these. First things first: a player character is now in the game:

![The player character](/img/player.png)

Lovely, isn't it? The player character is just a rectangle; I'll probably keep this in the final game since you need to be able to see if you're over the fish, and this is nice and thin at the moment.

The player needs to be able to move up and down to chase the fish, so I've added basic keyboard controls (just the up key). Gravity will pull the player down, so you can't directly control your height - you can move up the screen, but will have to rely on gravity if the fish moves down the screen. This adds a bit of challenge: if you could precisely move up and down the screen, it would be far too easy to keep your avatar over the target.

For phones I'll implement tap to move up, and this one-key approach should make changing key-bindings easier in the future.

<div class="video">
  <iframe src='https://gfycat.com/ifr/PersonalTintedBlackfly' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe>
</div>

Actually moving the player component is pretty simple - I've added a 2D body object to the component, which means I can apply forces to the component, and then in the update function I check whether the vertical axis input is pressed. If so, then I apply upward force to the component, so the player accelerates upwards while the button is pressed. I also ignore the down input - the player can only apply upwards force, and will have to rely on gravity to pull them back down.

```cs
public float speed;

void FixedUpdate () {

  // check the vertical input
  float moveVertical = Input.GetAxis("Vertical");

  // less than 0 means down is pressed. We don't care about that, so
  // set back to 0 to ignore it
  if (moveVertical < 0) {
    moveVertical = 0;
  }

  Vector2 movement = new Vector2(0, moveVertical);

  // speed is set in the GUI, so it's easy to update
  body2d.AddForce(movement * speed);
}
```

Now we can move up the screen by pressing a button, and the gravity will gradually pull the player back down when the button isn't pressed. As an aside, I really like how declaring variables as public in a class exposes them to the Unity GUI, which makes them really simple to tweak as you play-test.


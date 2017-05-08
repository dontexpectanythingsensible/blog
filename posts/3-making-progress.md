extends: default.liquid

title: Making progress
date: 12 Mar 2017 12:00:00 +0000
description: Catching fish, and the one that gets away
---

# Making progress

In [the last post](/posts/2-adding-player-and-handling-input.html), we added a player and could move up or down. The next step is being able to catch a fish, and showing how close the player is to either catching it or the fish escaping, via a progress bar.

The progress bar is a simple rectangular sprite, which is scaled up or down depending on how much progress is made. Progress is increased when the player is over the fish, and decreased when the fish has escaped.

## Catching the fish

To be able to catch a fish, you need to keep the player over the fish until the progress bar has been filled, so being able to detect whether or not the player is over the fish we need collision detection. Unity has a few methods which make this pretty easy; we're using the trigger methods, since we only need to detect whether the player and fish are overlapping. The other set of methods are collider methods, which should be used when two components need to apply forces to each other.

The fish sprite is set to be a trigger through the Unity GUI: this means the trigger callbacks will be called, rather than the collider functions. Then, in the player controller script, we set the trigger callbacks and check whether the object collided with is the fish:

```cs
// progress is a component, set via GUI
public GameObject progress;

// the amount to update the progress bar by
private const int MOVE_AMOUT = 5;

// OnTriggerEnter - when the player wasn't over the trigger but now is (last frame compared with this)
void OnTriggerEnter2D (Collider2D other) {

  // check to see if the trigger we've collided with is the fish sprite
  // Tags are set through the GUI and are strings
  if (other.gameObject.CompareTag("Fish")) {

    // we're over the fish! Tell the progress bar to update
    progress.SendMessage("updateProgress", MOVE_AMOUT);
  }
}

// called if in the last frame we were colliding with the trigger, and we still are
void OnTriggerStay2D (Collider2D other) {
  if (other.gameObject.CompareTag("Fish")) {
    progress.SendMessage("updateProgress", MOVE_AMOUT);
  }
}

// called if we were colliding in the last frame, and are no longer
void OnTriggerExit2D (Collider2D other) {
  if (other.gameObject.CompareTag("Fish")) {

    // like above, tell the progress bar to update.
    // This time, it should reduce since we're no longer over the fish
    progress.SendMessage("updateProgress", -MOVE_AMOUT);
  }
}
```

This bit of code tells the progress bar to update, either a positive or negative amount, based on whether or not the player is currently hovering over the fish.

There's a bit of discussion about whether `SendMessage` is a relatively expensive way to update components. Since we currently have very few components in the game, this doesn't seem to be a problem, and `SendMessage` is a very simple way of implementing this functionality. If in the future this code seems to be causing performance problems, then I'll have to revisit it, but for now, it seems fine.

## Scaling

To give visual indication about how close the player is to losing or catching a fish, the progress bar needs to scale according to the progress value.

```cs
// public so we can set the inital value via GUI
public void progress;

// this is the method called by the `SendMessage` call above
public void updateProgress(int amount) {
  this.progress += amount;

  // pixelsPerPercent is the screen height times the camera scale
  float percent = this.progress * this.pixelsPerPercent;

  // scale the sprite vertically (the y axis) and keep x and z as they are
  transform.localScale = new Vector3(1, percent, 1);
}
```

The scale is changed into a percentage, otherwise adding 1 to the progress will double the size of the sprite (i.e. scales from `Vector3(1, 1, 1)` into `Vector3(1, 2, 1)`).

A nice improvement to this would be to change the colour based on how close the player is to succeeding or failing, to reinforce the feedback to the player.




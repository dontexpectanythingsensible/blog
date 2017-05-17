extends: default.liquid

title: Animations and movement
date: 15 May 2017 12:00:00 +0000
description: Making the fish fun to catch
slug: animating-the-fish
---

In the inital versions of the game, the fish moved up and down in a linear fashion for a set period of time (see the video from <a href="/posts/winning-the-game" title="Chapter 4 - Winning the game">the last post</a>):

<video src="/img/4-game-loop.mp4" class="video" controls autoplay loop="true">
	Sorry, your browser doesn't support video. You can <a href="/img/4-game-loop.mp4">download the video here</a>.
</video>

At the start of the game, the fish started moving in one direction, then after a set period of time it changed direction and moved back the other way. Obviously, for a game this incredibly boring because it's easy to predict and is the same every single time, so we needed a better way for the fish to move.

<video src="/img/5-fish-movement.mp4" class="video" controls autoplay loop="true">
	Sorry, your browser doesn't support video. You can <a href="/img/5-fish-movement.mp4">download the video here</a>.
</video>

Fish now wait where they are for a period of time, then move at a semi-randomised speed for a period of time, then stop again. We now have several types of fish with different movement patterns - some are slow and don't move very far, while others can move quickly and over long distances. Eventually we'll have a large group of fish which all move in distinctive ways - the goal is that the player will always see the same image when trying to catch a fish (so won't immediately know which species of fish it is), but each species of fish will move in an individual way to give the player a hint.

Here's the (slightly simplified) code controlling the fish movement:

```cs
void Update () {
	// make a note of the current time - used to check whether the fish should start or stop moving
	float currentTime = Time.time - this.startTime;

	// if the fish isn't moving, and it's time to start,
	// then pick a direction to move in,
	// set a flag that the fish is moving
	// and make a note of the time the movement started (used to calculate the duration of movement)
	if (currentTime > this.nextMove && !this.moving) {
		this.direction = this.pickDirection();
		this.moving = true;
		this.startMoveTime = currentTime;
	}

	// if the fish is moving, and should still be moving
	// ie the current time is less than when the fish started moving added to the duration of movement
	// (set in the fish params)
	// then move the fish by changing the body velocity
	if (this.moving && currentTime < this.startMoveTime + fish.getDuration()) {
		if (this.direction == Direction.Up) {
			this.body2d.velocity = new Vector2(0, Random.Range(fish.getMinSpeed(), fish.getMaxSpeed()));
		} else {
			this.body2d.velocity = new Vector2(0, Random.Range(-fish.getMinSpeed(), -fish.getMaxSpeed()));

		}
	}

	// if the fish is currently moving but has moved for the max duration
	// then stop moving and reset everything
	if (this.moving && currentTime > this.startMoveTime + fish.getDuration()) {
		body2d.velocity = new Vector2(0, 0);
		this.moving = false;
		this.startTime = Time.time;
		this.nextMove = Random.Range(0f, fish.getDirectionChangeFrequency());

	}
}

```

Altogether, this makes the fish movement a lot less predictable and so more fun to try to catch!

<video src="/img/5-fish-movement.mp4" class="video" controls autoplay loop="true">
	Sorry, your browser doesn't support video. You can <a href="/img/5-fish-movement.mp4">download the video here</a>.
</video>

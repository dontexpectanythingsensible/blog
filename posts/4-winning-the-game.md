extends: default.liquid

title: Closing the loop
date: 08 May 2017 12:00:00 +0000
description: Winning and losing UI states
slug: winning-the-game
---

# Winning the game

Now [we have a progress bar](/posts/3-making-progress.html) to show how close the player is to catching the fish, we need to add a way for the fish to actually be caught.

<video src="/img/4-game-loop.mp4" class="video" controls autoplay loop="true">
	Sorry, your browser doesn't support video. You can <a href="/img/4-game-loop.mp4">download the video here</a>.
</video>


To check if the fish has been caught, we added a new GameObject called `UIManager` which will handle winning and losing states, along with showing relevant text when this happens. The UIManager reads the progress value from the `ProgressController`, then shows the win state if progress is over one hundred, and the fail state if it's zero or under. The `ProgressController` stores progress as a percentage, which is why the range is between zero and one hundred.

The winning and losing UI is just some text added to the scene at the moment, and the UIManager just loops over the relevant text and changes the component's `setActive` flag:

```cs
GameObject[] lose;

void Start () {

	// save ref here - setactive(false) means findgameobjects return null
	// once you have these references then you can loop through and call SetActive(false)
	// to hide the UI text
	lose = GameObject.FindGameObjectsWithTag ("Lose");
}


void Update () {

	// progress is a reference to the ProgressController
	if (progress.progress < 0) {
		Debug.Log ("lose!");

		// show text
		showLose ();

		// pause the game
		Time.timeScale = 0;
	}

	if (progress.progress > 100) {
		Debug.Log ("win");
		showWin ();
		Time.timeScale = 0;
	}
}

// similar function for the win state
private void showLose () {

	// if you tried to use FindObjectsWithTag here, then nothing would be found
	// since we called SetActive(false) in the Start method
	foreach (GameObject o in lose) {
		o.SetActive (true);
	}
}

```

Here's a video of it in action:

<video src="/img/4-game-loop.mp4" class="video" controls autoplay loop="true">
	Sorry, your browser doesn't support video. You can <a href="/img/4-game-loop.mp4">download the video here</a>.
</video>
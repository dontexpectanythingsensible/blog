extends: default.liquid

title: Android test builds
date: 30 August 2017 12:00:00 +0000
description: Loading phones to test the flow
slug: android-build-and-testing
---

Shimi Paperfish is designed to run on phones and tablets, so it's probably a good idea to get a version of the game running on phones as soon as possible to check that the game works, and also that it's actually fun.

With this in mind, we've now got Shimi running on Android!

<div class="gallery">
    <img src="/img/shimipaperfish-map2.png" alt="Overworld map placeholder" />
    <img src="/img/shimipaperfish-fishing1.png" alt="Fishing" />
    <img src="/img/shimipaperfish-fishing2.png" alt="Fishing" />
</div>

As you can see from the screenshots, we've added an overworld map so you can choose where to go fishing (this is just a placeholder image at the moment though!), with the idea that there will be several areas where different fish are prevalent.

Building for phones was really useful since it brought to light a number of things which aren't obvious when developing on a laptop. For instance, on phones the progress bar in the fishing screen disappears off the side of the screen, and a number of UI elements are far too small, despite everything seeming fine on laptops. Creating a phone version as early as possible means we can fix these things as we go, rather than having a huge backlog of work later on.

We also ran into problems when building for Android - it turns out there was a bug when using Unity and newer versions of the Android SDK. The fix for this involved upgrading the version of Unity, which is always risky mid-project! Luckily the upgrade didn't cause any problems and fixed the issue we had with Android, which was a relief.

As the project is still in early development, there are no public builds yet - hopefully there will be some time soon!

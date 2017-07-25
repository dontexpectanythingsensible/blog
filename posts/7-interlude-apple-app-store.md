extends: default.liquid

title: Interlude - Apple's App Store
date: 3 July 2017 12:00:00 +0000
description: Jumping through hoops to create an app
slug: interlude-apple-app-store
---

We've been quiet for the last couple of weeks since we're busy preparing one of our other games, [Pairs](https://www.jamestease.co.uk/games/pairs/), for release on iOS devices.

Since the game is written in Phaser, and is [already out for Android](https://play.google.com/store/apps/details?id=uk.dontexpectanythingsensible.pairspro), we thought this would be a relatively quick process - we'd just need to run the relevant Cordova command and upload the built app, similarly to the Android process. Well, not quite.

Apple's review process sounds like a good idea - it prevents broken or low-effort apps from flooding the app store, which means that all apps available for users have a minimum level of quality. However, the process itself, and especially the tooling around it are quite lacking. Our original submission of Pairs failed the review process in two places:

1. one icon was different on a 12" retina iPad (icons should be identical except for size)
2. we used the word 'memory' in one of the app store fields.

## Copyright

The word 'memory' is banned from app titles because a German games company has managed to copyright it in a few European countries, which is annoying enough by itself. However, Apple don't have a way for apps to be selectively excluded from certain countries, so instead there's just a blanket ban on a common English word so Apple don't have to deal with copyright lawsuits.

Both of these issues seem like they should be automated so they can be caught long before app submission and the days of waiting before any problems come to light. The icon might be slightly trickier to automate, but even a way to see all icons in the app next to each other would make things a lot clearer.

Anyway, we're back in the review cycle, so work on the fishing game will be continuing very soon!
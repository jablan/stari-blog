---
layout: post
title: Mac-like drag-locking on Linux
date: '2012-03-31T18:23:00+02:00'
tags:
- linux
- touchpad
- lxde
tumblr_url: http://jablan.radioni.ca/post/20230225234/mac-like-drag-locking-on-linux
---
If you have used a Mac and “tap to click” option on it, you probably know about drag locking, i.e. the ability to shortly raise your finger from the touchpad while not stopping the dragging (say when you are marking some text, and your finger reaches the end of the touchpad).

Well, there is the same feature on Linux as well, just there’s no GUI (as far as I know) for turning it on. Console to the rescue! Just do this:

    synclient LockedDrags=1

and you will have locked dragging. The initial timeout is too long though (5 seconds), so you will probably want to make it shorter, something like half a second or so (play with different values until you reach what suits you the best):

    synclient LockedDragTimeout=500

And you’re good to go. In LXDE, you can put these setting to `~/.config/lxsession/LXDE/autostart` to make it permanent.

If “tap to click” doesn’t work by default, turn it on using

    synclient TapButton1=1


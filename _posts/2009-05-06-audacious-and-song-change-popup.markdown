---
layout: post
title: Audacious and song change popup
date: '2009-05-06 15:42:39 +0200'
mt_id: 233
post_id: 233
author: jablan
lang: en
---
If you're using Linux and like the simple winamp-like UI for your music player, you are probably using [Audacious](http://audacious-media-player.org/) (if not, you should definitely take a look). Audacious offers its own OSD for notifying about song changes etc, but I don't like it, and I wanted to make use of nice notification system [Jaunty](http://www.ubuntu.com/) uses (notification-daemon). Audacious doesn't offer the possibility to communicate with notification-daemon out of the box (at least not that I know of), but offers the plugin which invokes arbitrary command upon certain actions, such as song change.

Here's what you need to do to get nice popup notification from Audacious:

Install notify-send:

    jablan@jablan-hp:~$ sudo apt-get install libnotify-bin

This small command allows you to pop up anything from the command line, you can try it out:

    jablan@jablan-hp:~$ notify-send "Audacious plays" "Blah Blah - We Are the Blah Blahs" -i audacious

Next, enable "Song Change" plugin in Audacious, and go to its properties. Add something like _notify-send "Audacious" "%s" -i audacious_ to edit-box for the command upon the song change.

And, that's it, you should get a little black balloon displayed each time Audacious plays another song!


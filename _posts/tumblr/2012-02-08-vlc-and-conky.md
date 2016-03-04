---
layout: post
title: VLC and Conky
date: '2012-02-08T18:56:00+01:00'
tags:
- linux
- vlc
- conky
tumblr_url: http://jablan.radioni.ca/post/17270281908/vlc-and-conky
---
I needed a way to display currently playing item from VLC in Conky. The usual solution doesn’t work for me as it doesn’t seem to display track names when listening to radio streams.

So here’s an alternative way which utilizes window title of VLC window (which actually displays track name). It uses [`xlsclients`](http://www.xfree86.org/current/xlsclients.1.html) command which lists currently opened X11 windows and their properties. Combine that with `grep` and you can have the track title…

So, at the end, I just put this to my `.conkyrc`:

    ${exec xlsclients -l | grep "VLC media player" | cut -c -9 --complement}


---
layout: post
title: First Natty and Unity impressions
date: '2011-05-04T11:36:00+02:00'
tags:
- ubuntu
- natty
- unity
- review
- linux
tumblr_url: http://jablan.radioni.ca/post/5186158826/first-natty-and-unity-impressions
---
I was curious about the new UI included in latest Ubuntu release called Unity so I decided to give it a shot. I haven’t reinstalled my main working machine (10.10 still working there), but I took 10-20 GB off MacbookPro’s hard drive to install it there.

Installation went smoothly, Ubuntu even recognized the MacOS on the other partition and offered whether it should replace it (boy that was tempting!) or install alongside with it. Upon installation, everything went well, I got Unity right off, it is in fact written as a Compiz plugin, so, you got Compiz, you can have Unity and vice versa, no Compiz (say, no adequate graphic card or adequate driver), no Unity.

I had some problems installing Broadcom Wifi drivers, had to experiment and google a bit, but eventually it started working.

After the install, I just removed couple of applications I don’t use (everything using Mono, for example, Gwibber, Empathy, Shotwell etd), and installed couple I use (Kupfer, Pidgin, gThumb, Exaile). Natty occupies some 280 MB in memory upon boot. Seems rather modest to me.

Now about Unity, as it’s the biggest change new Ubuntu brings.

It may look intimidating to the users used to traditional Gnome interface. Top panel, although similar, _is not_ your old Gnome panel. Right-clicking doesn’t work. Icons on the right are not panel applets, but indicators (not the same). So you might feel frustrated by expecting for it to behave the way you used to.

### Launcher

![Launcher shortcuts](http://i.imgur.com/jCHQK.png)On the left, you’ll see the launcher. If you used Mac OS or Windows 7, you’ll know what you have, same icons reused both for favourite applications you would like to be able to launch easily, and for currently running applications. I always liked that on Mac, I like it here as well. The only thing that annoyed me on Mac seems to be solved here: if you have more than one window opened for an application, you don’t see it on Mac, and if you want to pick one from them, you need to press and hold the icon until a (text) menu appears. In Unity you 1) have one small arrow on the left of the icon per every window opened, and 2) another click on the icon shows the thumbnails of the opened windows in that app, and you can pick one easily. The launcher hides automatically if some of your windows covers it, or if you maximize any window.

There’s a nice feature in the launcher: each icon is assigned a keyboard shortcut - `Super+1` for the first icon on the top, `Super-2` for the second etc. If you have couple of icons fixed there (say, for a file manager, terminal, browser and a chat application, you can switch between them really quickly, lot faster and more accurate than using Alt-Tab (which, of course, still works). There is also `Super-W`, which displays thumbnails of all open windows, and couple of other shortcuts.

### Windows

Application menus are moved away from application windows, to the top panel. Again, MacOS users will feel at home here. Very sane decision, to save space by not displaying menubars of inactive windows.

Maximized windows are really maximized. All you will see is the top panel. No window bar - close, minimize and maximize buttons and window title are, again, moved to the top bar.

### Dash

Dash is something like Gnome menu replacement - you get it when you either click top left ubuntu button, or tap `Super` key once. It’s convenient for searching and launching applications and documents. You might find it useful if you are a power user, but I guess some inexperienced users would expect to see all installed applications which they would browse at a single place. I, personally, prefer Unity’s type-and-search approach, but it’s inferior to existing applications dedicated to it, and here I must praise [Kupfer](http://kaizer.se/wiki/kupfer/) again, a brilliant application for power users (I believe Quicksilver is the original application for Mac). I would really like to see integration of Kupfer and Unity as it could easily serve as the “engine” which powers dash search.

### Cons

The biggest problem I see with Unity is the fact that it relies and requires video acceleration. Combine that with the fact that often you can’t rely on graphic drivers to exist or work on your specific hardware, you can’t guarantee that Unity will work on any hardware around.

Also, there are some aesthetic annoyances, unaligned buttons and images here and there, it just feels a little unpolished.

There is no centralized place for customizing look and feel. You can’t add, remove and rearrange app indicators as you could gnome’s panel applets. Right click is often unused.

### General impressions

After couple of days of active Unity usage I really don’t feel restrained in any way by it, and I believe I will continue using it on my primary machine. Also, I believe it will improve in time, both in terms of aesthetics, features and customization. But generally, as a power user, I find it more friendly than the old Gnome.

### Couple of hints

- Install `ccsm` (CompizConfig Settings Manager), you’ll be able to tweak some Unity’s features there.
- If your touchpad supports it, you can use three-finger scroll for moving windows around, and four-finger tap for invoking Dash.
- Check [this list](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html), you might find something that suits you.

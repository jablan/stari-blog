---
layout: post
title: Get first and last line from a file
date: '2011-03-29T16:46:45+02:00'
tags:
- unix
- coreutils
- gnu
- command line
tumblr_url: http://jablan.radioni.ca/post/4184844466/get-first-and-last-line-from-a-file
---
I needed to get only first and last line from a file (actually, not a file, but rather output from another command). `head -1` and `tail -1` can be used to get either first or last, but how to combine the two at the same time? Here’s how. Enter [`tee`](http://linux.die.net/man/1/tee):

    cat somefile | grep something | tee >(head -1) >(tail -1) > /dev/null

Neat, huh?


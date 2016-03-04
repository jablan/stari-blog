---
layout: post
title: Appeasing programming language gods
date: '2011-04-27T22:30:00+02:00'
tags:
- php
- language war
tumblr_url: http://jablan.radioni.ca/post/4991817597/appeasing-programming-language-gods
redirect_from: '/post/4991817597/appeasing-programming-language-gods/'
lang: en
---
Just recently, a fellow coder wrote the following tweet:

> you know what function #php is missing? preg\_file\_get\_contents - get only the content part which matches the pattern

I’m not usually reacting to such appeals, but I felt this is very suitable to try to explain what’s so deeply wrong about PHP, and not as much with PHP but with the whole attitude in communities around certain platforms. I said that that statement is wrong on so many levels, so here I’ll try to address some of them.

### `language == function`

This is so symptomatic in PHP - identifying the language with the function set provided with it. That tells helluva lot about the language (or, rather, the lack of one). Hey, I thought languages are there to allow _you_, the programmer, to actually create the functions you need.

### Micro-specification

Instead of having few very poweful functions which you can combine to achieve your goal, you rely on myriad of tiny, ultra-specialized functions crafted to perform a single specific task. You need function to get lines from a file that match a pattern? All you really need is:

1. The possibility to iterate through lines of a file
2. The possibility to `select` items from an iterator based on a given criteria
3. The possibility to perform regex on a string
4. And a language powerful enough to combine the above three elegantly (no, C’s function pointers doesn’t count)

Something like this (Ruby, but any decent modern language has something similar):

    File.foreach('pi.c').select{|line| line =~ /print/}
    # ^ ^ ^ ...which match the given regex
    # | | ...select only those lines...
    # | iterating through every line of a file...

See? Not even worth putting in a separate method.

### Relying on gods’ mercy

Waiting for the language creators (or, in extreme cases, a comitee) to accept something which would make your life easier is frustrating, time-wasting and plainly insulting. Such gods should be overthrown, caught and imprisoned. [Good gods](http://en.wikipedia.org/wiki/John_McCarthy_(computer_scientist)) just should give us the basic tools, a hammer and a chisel, and we’ll make the rest ourselves.


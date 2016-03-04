---
layout: post
title: StackOverflow-style syntax highlight on Tumblr
date: '2010-12-11T22:28:00+01:00'
tags:
- tumblr
- syntax highlight
- stackoverflow
- code
tumblr_url: http://jablan.radioni.ca/post/2177846097/stackoverflow-style-syntax-highlight-on-tumblr
---
There are several articles on how to enable (client-based) syntax highlighting on Tumblr. None of these solutions worked for me, as each requires setting class on `pre` or `code` tags manually for coloring JS snippet to recognize areas to colorize. This is not simple in my case, as I am using [Markdown](http://daringfireball.net/projects/markdown/syntax) as markup language, and generating HTML tags (and their attributes, such as `class`) is out of control there.

So I decided to slightly modify existing solutions to suit my needs. I took [prettify](http://code.google.com/p/google-code-prettify/) module and combined it with small jQuery snippet of my own, which prepares existing HTML (created using Markdown) for prettification, by dynamically assigning `prettyprint` class to code blocks.

If you want to do the same, just customize your theme’s HTML to include following lines:

    <link rel="stylesheet" type="text/css" href="http://static.tumblr.com/n9ku3gx/bmmlda7os/prettify.css" />
    <script type="text/javascript" src="http://static.tumblr.com/n9ku3gx/1k0lda7q0/jquery.min.js"/>
    <script type="text/javascript" src="http://static.tumblr.com/n9ku3gx/DiKlda7r3/prettify.min.js"/>
    <script type="text/javascript">
      $(function() {
        $('pre > code').addClass('prettyprint');
        prettyPrint();
      });
    </script>

And that should be all it takes to get your code nicely highlighted!


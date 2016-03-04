---
layout: post
title: Reverse a string using regexps
date: '2011-04-23T12:55:05+02:00'
tags:
- ruby
tumblr_url: http://jablan.radioni.ca/post/4862704249/reverse-a-string-using-regexps
---
I know you have always wondered how would one reverse a string without using loops or any kind of iteration, using, say, regular expressions and recursion. So stop wondering you:

    class String
      def r_revert
        sub(/(.+)(.)/){$2 + $1.r_revert}
      end
    end
    'jablan'.r_revert
    #=> 'nalbaj'

or, if you prefer recursive lambdas instead of monkey-patching:

    l = ->(s){s.sub(/(.+)(.)/){$2 + l.($1)}}
    l.('jablan')
    #=> 'nalbaj'


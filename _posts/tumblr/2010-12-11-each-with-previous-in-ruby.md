---
layout: post
title: '"Each with previous" in Ruby'
date: '2010-12-11T18:10:00+01:00'
tags:
- ruby
- enumerable
- each
- programming
tumblr_url: http://jablan.radioni.ca/post/2175717120/each-with-previous-in-ruby
---
I often need a variant of `Enumerable#each` method, with a “twist”: sometimes I want to have previous element available along with the current one, most often for comparison between the two. Here’s a trivial example:

    array = [
      {name: 'foo', value: 15},
      {name: 'foo', value: 6},
      {name: 'bar', value: 2},
      {name: 'bar', value: 7},
      {name: 'bar', value: 14},
      {name: 'baz', value: 4},
      {name: 'baz', value: 1}
    ]
    
    array.each_with_prev{|prev, curr|
      # Want to display name only before the first record in the group
      puts curr[:name] unless prev && prev[:name] == curr[:name]
      puts " #{curr[:value]}"
    }
    foo
        15
        6
    bar
        2
        7
        14
    baz
        4
        1

And here’s (very simple, `inject` based) implementation of `each_with_prev`:

    module Enumerable
      def each_with_prev
        self.inject(nil){|prev, curr| yield prev, curr; curr}
        self
      end
    end


---
layout: post
title: Making use of multiple processor cores in Ruby
date: '2009-01-14 15:24:09 +0100'
mt_id: 232
post_id: 232
author: jablan
---
Most today's computers have more than one processor core, and it's a pity not to make use of that fact, especially when using a language as slow as Ruby. Unfortunately, ruby threads all execute on the same core as the process itself, so no luck there (I think jRuby works better there, but often it's not a choice). But sometimes we can use processes instead of threads. In the following example we're doing just that, forking several processes to execute a task that's suitable for parallel processing.

    #!/usr/bin/ruby
    
    # number of simultaneous processes
    sim = 4
    # array of elements to process
    a = (1..20).to_a
    
    # function that processes the data
    def do_the_do i
      puts "starting #{i}"
      # do something, for example, sleep between 5 and 10 seconds
      sleep(rand(5)+5)
      puts "done #{i}"
    end
    
    # starting first N processes
    sim.times do
      i = a.pop
      Process.fork {do_the_do(i)}
    end
    # start one by one as the previous finish
    a.each do |i|
      Process.wait(0)
      Process.fork {do_the_do(i)}
    end
    # wait for all to finish
    Process.waitall
    puts "done all"

The code is explained in the comments, should be pretty straightforward.


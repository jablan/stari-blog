---
layout: post
title: Counting visits with Ruby
date: '2008-12-21 12:25:11 +0100'
mt_id: 231
post_id: 231
author: jablan
lang: en
---
Here's a piece of ruby code I wrote to count visits in log files. I'll explain it in more details afterwards:

    #!/usr/bin/ruby
    require 'date'
    
    log = [
      ['user1', '2008-12-20 14:03:00'],
      ['user1', '2008-12-20 13:00:00'],
      ['user2', '2008-12-20 13:01:00'],
      ['user3', '2008-12-20 13:02:00'],
      ['user1', '2008-12-20 13:03:00'],
      ['user1', '2008-12-20 14:00:00'],
      ['user2', '2008-12-20 14:01:00'],
      ['user2', '2008-12-20 14:02:00'],
      ['user1', '2008-12-20 15:00:00']
    ]
    
    users_visits = {}
    log.each do |line|
      users_visits[line[0]] ||= []
      users_visits[line[0]] SESSION_TIMEOUT ? 1 : 0)]
      }[1]
      puts "Userid: #{userid} visits: #{visits}"
      total_visits += visits
    end
    
    puts "Total visits: #{total_visits}"

Here we start out with an array of arrays, which is more likely to be an array of apache log lines, but the point is the same. We take one by one and construct a hash of arrays: keys are userids (most often if the form of md5 hashes or so), and values are arrays of the timestamps when the user accessed our site. At the end, we can get unique count simply by getting the number of hash members.

Then, for each user, we need to count visits. By "visit" we refer to a set of consecutive requests by the same user which was made with no less than a certain amount of time (here, 30 mins) in between. This number is in fact same to the number of slots between consecutive requests longer than this timeout limit. So we are using convenient ruby method [inject](http://www.ruby-doc.org/core/classes/Enumerable.html#M003160) (also known as "reduce" or " [fold](http://en.wikipedia.org/wiki/Fold_(higher-order_function))" in functional programming) on a sorted array of the timestamps. As a starting value, we use timestamp of 1970-01-01 in order to make sure first request is counted as a visit as well, and also zero, which is used as the initial value of accumulator.

Feel free to correct and/or improve the code in the comments!


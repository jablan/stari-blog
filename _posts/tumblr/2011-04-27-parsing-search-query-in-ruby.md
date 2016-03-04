---
layout: post
title: Parsing search query in Ruby
date: '2011-04-27T13:44:45+02:00'
tags:
- ruby
- search
- regexp
tumblr_url: http://jablan.radioni.ca/post/4982485974/parsing-search-query-in-ruby
---
Here’s a regular expression you can use if you want to parse a user’s search query, along with some Ruby to put the result into neat Hash. The query supports prefixing with plus or minus, adding string prefix (a la Google’s `site:www.site.com`) and quoting whole phrase for exact matching:

    def parse_query s
      s.scan(/((\S+)\:\s?)?([+-])?(("(.+?)")|(\S+))/).map{|match|
        Hash[
          [nil, :prefix, :plusminus, nil, nil, :phrase, :word].zip(match).select(&:all?)
        ]
      }
    end

so that:

    parse_query 'foo +bar -baz "dev pro talk" site:devprotalk.com category:cat1'

returns:

    [
      {:word=>"foo"},
      {:plusminus=>"+", :word=>"bar"},
      {:plusminus=>"-", :word=>"baz"},
      {:phrase=>"dev pro talk"},
      {:prefix=>"site", :word=>"devprotalk.com"},
      {:prefix=>"category", :word=>"cat1"}
    ]


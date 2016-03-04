---
layout: post
title: Locale dependent string sorting in Ruby
date: '2010-05-06 16:34:33 +0200'
mt_id: 235
post_id: 235
author: jablan
---
You'll forgive me if there is already a library or gem which already provides this feature. This piece of code was thrown together quickly as a [response](http://stackoverflow.com/questions/2779880/locale-based-sorting-function-in-ruby/2780628#2780628) to a StackOverflow question. Not tested thoroughly, and not production-ready quality, but could be usable if polished a little bit.

So, say you make a multilingual application and good ol' Ruby's string comparison (thus sorting string arrays, for example) doesn't work as you expect for languages other than English. With the following method, you just need to provide a string with all the letters from the desired language properly ordered for comparison and sorting to work. It would be, theoretically, possible to alter default string comparison method <tt>String#</tt>, but previously somehow feed it with alphabetically ordered string.

    class String
      # compares two strings based on a given alphabet
      def cmp_loc(other, alphabet)
        order = Hash[alphabet.each_char.with_index.to_a]
    
        self.chars.zip(other.chars) do |c1, c2|
          cc = (order[c1] || -1) (order[c2] || -1)
          return cc unless cc == 0
        end
        return self.size other.size
      end
    end
    
    class Array
      # sorts an array of strings based on a given alphabet
      def sort_loc(alphabet)
        self.sort{|s1, s2| s1.cmp_loc(s2, alphabet)}
      end
    end
    
    array_to_sort = ['abc', 'abd', 'bcd', 'bcde', 'bde']
    
    ALPHABETS = {
      :language_foo => 'abcdef',
      :language_bar => 'fedcba'
    }
    
    p array_to_sort.sort_loc(ALPHABETS[:language_foo])
    #=>["abc", "abd", "bcd", "bcde", "bde"]
    
    p array_to_sort.sort_loc(ALPHABETS[:language_bar])
    #=>["bde", "bcd", "bcde", "abd", "abc"]


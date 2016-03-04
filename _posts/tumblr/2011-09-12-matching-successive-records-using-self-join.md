---
layout: post
title: Matching successive records using self-join
date: '2011-09-12T18:58:07+02:00'
tags:
- sql
- join
- databases
- programming
tumblr_url: http://jablan.radioni.ca/post/10128857773/matching-successive-records-using-self-join
---
SQL joins can be really powerful once you got the hold of them. Especially interesting could be self-joins, i.e. joining the table onto itself.

Let’s say you have a table of daily temperatures:

    create table temperatures (
      id serial,
      date date,
      temp numeric(4,2)
    );
    
    insert into temperatures (date, temp) values ('2011-09-01', 30);
    insert into temperatures (date, temp) values ('2011-09-02', 28);
    insert into temperatures (date, temp) values ('2011-09-03', 27);
    insert into temperatures (date, temp) values ('2011-09-04', 32);
    insert into temperatures (date, temp) values ('2011-09-06', 26);
    
    select * from temperatures;
    
     id | date | temp  
    ----+------------+-------
      1 | 2011-09-01 | 30.00
      2 | 2011-09-02 | 28.00
      3 | 2011-09-03 | 27.00
      4 | 2011-09-04 | 32.00
      5 | 2011-09-06 | 26.00
    (5 rows)

Say that we want a query which would, for each day, calculate the difference between that and the previous measurement.

We will start with a simple query to get all date’s temperatures:

    select date, temp from temperatures order by date;
    
        date | temp  
    ------------+-------
     2011-09-01 | 30.00
     2011-09-02 | 28.00
     2011-09-03 | 27.00
     2011-09-04 | 32.00
     2011-09-06 | 26.00
    (5 rows)

Ok, that’s easy. Now we will expand this table with other dates, but we can narrow our query to only get dates prior to the current one:

    select t1.date, t1.temp, t2.date
    from temperatures t1
    left join temperatures t2 on t1.date > t2.date
    order by t1.date, t2.date;
    
        date | temp | date    
    ------------+-------+------------
     2011-09-01 | 30.00 | 
     2011-09-02 | 28.00 | 2011-09-01
     2011-09-03 | 27.00 | 2011-09-01
     2011-09-03 | 27.00 | 2011-09-02
     2011-09-04 | 32.00 | 2011-09-01
     2011-09-04 | 32.00 | 2011-09-02
     2011-09-04 | 32.00 | 2011-09-03
     2011-09-06 | 26.00 | 2011-09-01
     2011-09-06 | 26.00 | 2011-09-02
     2011-09-06 | 26.00 | 2011-09-03
     2011-09-06 | 26.00 | 2011-09-04
    (11 rows)

Now we have matched every date with _all_ previous dates. (An important thing to note is that 2011-09-01 doesn’t have matched record. That’s because there is no date prior to 2011-09-01 in the table). So, for example, for 2011-09-04 we have all three, 01, 02, and 03. matched. We need just the most recent one, i.e. 03.

We will now use a trick to achieve this. We will add _another_ join to eliminate all the dates but the most recent one:

    select t1.date, t1.temp, t2.date, t3.date
    from temperatures t1
    left join temperatures t2 on t1.date > t2.date
    left join temperatures t3 on t3 < t1 and t2 < t3
    order by t1.date, t2.date, t3.date;
    
        date | temp | date | date    
    ------------+-------+------------+------------
     2011-09-01 | 30.00 | | 
     2011-09-02 | 28.00 | 2011-09-01 | 
     2011-09-03 | 27.00 | 2011-09-01 | 2011-09-02
     2011-09-03 | 27.00 | 2011-09-02 | 
     2011-09-04 | 32.00 | 2011-09-01 | 2011-09-02
     2011-09-04 | 32.00 | 2011-09-01 | 2011-09-03
     2011-09-04 | 32.00 | 2011-09-02 | 2011-09-03
     2011-09-04 | 32.00 | 2011-09-03 | 
     2011-09-06 | 26.00 | 2011-09-01 | 2011-09-02
     2011-09-06 | 26.00 | 2011-09-01 | 2011-09-03
     2011-09-06 | 26.00 | 2011-09-01 | 2011-09-04
     2011-09-06 | 26.00 | 2011-09-02 | 2011-09-03
     2011-09-06 | 26.00 | 2011-09-02 | 2011-09-04
     2011-09-06 | 26.00 | 2011-09-03 | 2011-09-04
     2011-09-06 | 26.00 | 2011-09-04 | 
    (15 rows)

What’s this? Even more records! We join with `t3`, but in such way that the date from t3 must be _between_ dates from `t1` and `t2`. But if you note the “missing” bits in `t3.date` column, you will see that for some date pairs from `t1` and `t2`, there is no `t3.date`. That’s the records where `t2.date` is right before `t1.date`. We need only that records. So, we’ll just add `WHERE` clause to discard all the records where `t3.date` exists:

    select t1.date, t1.temp, t2.date, t3.date
    from temperatures t1
    left join temperatures t2 on t1.date > t2.date
    left join temperatures t3 on t3 < t1 and t2 < t3
    where t3.date is null
    order by t1.date, t2.date, t3.date;
    
        date | temp | date | date 
    ------------+-------+------------+------
     2011-09-01 | 30.00 | | 
     2011-09-02 | 28.00 | 2011-09-01 | 
     2011-09-03 | 27.00 | 2011-09-02 | 
     2011-09-04 | 32.00 | 2011-09-03 | 
     2011-09-06 | 26.00 | 2011-09-04 | 
    (5 rows)

Right! Back to 5 rows, with just right values in t2.date column. Now all we have to do is add the temperature difference, and we’re done:

    select t1.date, t1.temp, t2.date, t1.temp - t2.temp as diff
    from temperatures t1
    left join temperatures t2 on t1.date > t2.date
    left join temperatures t3 on t3 < t1 and t2 < t3
    where t3.date is null
    order by t1.date, t2.date, t3.date;
    
        date | temp | date | diff  
    ------------+-------+------------+-------
     2011-09-01 | 30.00 | |      
     2011-09-02 | 28.00 | 2011-09-01 | -2.00
     2011-09-03 | 27.00 | 2011-09-02 | -1.00
     2011-09-04 | 32.00 | 2011-09-03 | 5.00
     2011-09-06 | 26.00 | 2011-09-04 | -6.00
    (5 rows)

That’s it. :)


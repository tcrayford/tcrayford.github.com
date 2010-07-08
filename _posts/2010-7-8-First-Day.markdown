---
layout: post
title: First day at Eden
---
I've just finished my first day as an apprentice at [EDEN]. As an exercise for
the first day, Enrique (my mentor) had me going through the Ruby Koans [LINK],
which were pleasantly surprising.

As a further add on to this, Enrique added the rule of not having any method
longer than 4 lines. I first saw an idea like this whilst reading Clean Code
(which is a very good read). In the past I probably would have written a large
method, but this encouraged me to write much smaller ones.

The nice part about the koans is they teach parts of the language one might
never touch much (I've never really used array slicing, for example). The
scoring problem (the koan I'm currently on), was also an interesting design
challenge. The solution I ended up with is here:

Even this small exercise reminded me of the important point of finding the
right technique being crucial to clean code. With the right angle on the
problem, code can become significantly smaller and easier to change.

The right abstraction in this case was finding triples by using

    (1..6).each do |i|
      if dice.count(i) >= 3
      ...

After I discovered this, the problem was easy to solve (and the code was cleaner too).

Annendum
---
Learn to type week (as suggested by Corey[http://programmingtour.blogspot.com/2010/07/learn-to-type-week.html])
is next week, and I'll definitely be taking part in it.

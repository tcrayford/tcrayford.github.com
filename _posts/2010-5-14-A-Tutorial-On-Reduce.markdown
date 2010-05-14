
---
layout: post
title:  A tutorial on the universality and expressiveness of reduce
---

I was getting up to date on [The Joy of Clojure](LINK_HERE) recently,
and found a link to [this
paper](http://www.cs.nott.ac.uk/~gmh/fold.pdf). It shows some
interesting demonstrations of `fold` (better known to Clojure
programmers as `reduce`), but I had to struggle through reading them
in Haskell.

The paper starts out by demonstrating that some standard list
processing functions can be written using reduce:


    (defn my-count [coll]
      (reduce (fn [n x] (inc n)) 0 coll))

    (my-count [1 2 3 3]) ;; produces 4

    (defn my-reverse [coll]
      (reduce (fn [xs x] (into [x] xs)) [] coll))

    (my-reverse [1 2 3]) ;; => [3 2 1]

    (defn my-map [f coll]
      (reduce (fn [xs x] (conj xs (f x))) [] coll))

    (my-map inc [1 2 3]) ;; => [2 3 4]

    (defn my-filter [pred coll]
      (reduce (fn [xs x] (if (pred x)
                           (conj xs x)
                           xs))
              []
              coll))

    (my-filter even? [1 2 3]) ;; => [2]

All of the above functions only work on vectors (the original Haskell
versions use lists). They're also not lazy, and lose a lot of benefits that the
full clojure implementations have. Furthermore, I personally find
`reduce` VERY hard to read. Having said that, there's
something to be said for how reduce expresses the above definitions.

The laziness problem is obviously avoided in Haskell (given its lazy
nature). I'm mostly bothered (at the moment) by the readability
problem. I don't find many of the above definitions clear at all, and
most of the time I need to use reduce, I don't, only noticing it
when I'm refactoring later (and even then I question it, due to the
readability problem).

The paper also taught me some more reasons for having first class
functions in a language (not that I needed more). See the following
definition of comp.


    (defn my-binary-comp [f g]
      (fn [x] (f (g x))))

    (defn my-comp [& fs]
      (reduce my-binary-comp identity fs))

    ((my-comp inc inc inc) 1) ;; => 4

Again, this isn't as all encompassing as clojure's implementation, but
it further demonstrates the expressiveness of reduce.

Users of Haskell will know that Haskell also defines the `foldl` function,
which simply processes arguments in the opposite order from
reduce. Hutton points out that this new function is sometimes more
useful than `fold`, by defining reverse in terms of it.

    (defn foldl [f value coll]
      (reduce f value (reverse coll)))

    (defn my-reverse [coll]
      (foldl (fn [xs x] (conj xs x)) [] coll))

    (my-reverse [1 2 3]) ;;=> [3 2 1]

Notes
---

All the above code can be found [here](http://gist.github.com/401618).

Hutton's original paper is [here](http://www.cs.nott.ac.uk/~gmh/fold.pdf)

---
layout: post
title: Second day at Eden
---
(This post is part of a series documenting my apprenticeship at Eden. For more,
visit the [archives](http://www.tcrayford.net/archive.html))

I've now finished the Ruby Koans I started on the first day. The remaining
koans taught me some useful things about message passing and method_missing,
which I have since used for a little test framework.

After finishing these Enrique got me tdding a wiki server using just the ruby
standard library. The twist to this is that you're not allowed to use
Test/Unit, so you basically have figure out how to write tests.

After finishing the day, I looked over the test code, and found it extremely
ugly. I've often found that ugliness in code means that I'm missing the right
abstraction, or at the very least that my design is flawed. My fault here was
entirely in the test code, which seemed very unstructured.

To resolve this, I wrote a small (77 lines) implementation of the xUnit testing
framework, so that I can clean up the tests on my third day. I wrote this (from
memory), based on Kent Beck's example from [TDD by
example](http://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530)
There's also a tiny mocking thing, based on
[Dingus](http://bitbucket.org/garybernhardt/dingus/), which I am using for testing
servlets.

After writing these two to help me organise the tests, I'm think the rest of
the wiki should be much easier to test (and therefore write). This reminds me
again of the importance of aesthetics in code. I've found ugly code is often
very difficult to work with, and makes the developers working on it unhappy 
as well.

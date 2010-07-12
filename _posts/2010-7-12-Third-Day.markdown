---
layout: post
title: Third Day at Eden
---
(This post is part of a series documenting my apprenticeship at Eden. For more,
visit the [archives](http://www.tcrayford.net/archive.html))

This a retrospective post, which I'm writing on Monday morning (for Friday).
On Friday I finished most of the wiki exercise, then paired with aimee for some
client work.

Wiki Retrospective
----

The wiki exercise was interesting, not least in learning more about testing and
abstraction. I think the main flaw with my program (as it stands now) is that
every action is modelled with its own Webrick servlet class. This has cost me
significantly in flexibilty; if I were to do this assignment again I would
write one servlet that just routes actions to something akin to a rails
controller. This would have made the testing much easier, and reduced
(somewhat) the level of mocking I did.

I'm quite happy with the mocking library that emerged, and found that testing
interactions (as apposed to state) fits nicely with my (newbie ish) ideas 
about OO testing.

The other main lesson I learned was with regards to ruby metaprogramming.
Whilst not as 'flexible' as lisp macros, I'm finding ruby metaprogramming
an interesting way of thinking, because you are mostly manipulating
methods on objects (and classes).

The other pleasant thing here was finding out how little code it takes to
write a minimum viable testing framework. I also wrote a little rspec
clone on top of my testing stuff, which was very simple to do. I didn't end
up using it, because it would have meant converting all my tests to
a new format (again, after I converted them to xUnit style), and everything 
was pretty much finished already. Furthermore, the examples were already
pretty readable, and I didn't feel that specs would add more.

Finally, I keep on feeling spoilt by Clojure's sequence library. There are a
number of functions there that I'd love to have in ruby (`partition-by` would
have been useful for the scoring kata, and `group-by` is dang useful).

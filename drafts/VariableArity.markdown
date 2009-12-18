---
layout: post
title: Variable Arity
---

Arity refers to the number of arguments a function takes. Clojure and Java both have instances where they use variable arity, specifically different implimentations of a function depending on the number of arguments passed to said function. One place most java programmers know about this is in chaining constructors:

    public Sketch () {
      this("Tom",1000);
    }

    public Sketch (String username, int badDrawingLevel) {
      this.username = username;
      this.badDrawingLevel = badDrawingLevel;
    }

Note that the first constructor takes no arguments, and calls the second constructor with the arguments filled in.

Clojure takes an approach that functions can have different implimentation depending on the number of arguments they are passed. This is often used (as in the Java example) to set some defaults up before running a more specific version of the function.

    (defn read-project
      ([file] (load-file file)
         project)
      ([] (read-project "project.clj")))

(Code taken from [leiningen](http://github.com/technomancy/leiningen/blob/master/src/leiningen/core.clj))

Python has default parameters for its functions, like so:

    def Sketch(name="Tom",bad_drawing_level=1000):
      pass

I find the python method for default parameters far easier on the eye than the clojure method. Although the clojure method has more power, it trades this for readability (when using variable arity for default arguments).

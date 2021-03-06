---
layout: post
title:  Clojure Autotest
---
I've been doing a lot of testing for a clojure side project recently, and got envious of Ruby people having nice tools. In particular I liked the coloured output and automatic test running from [rspactor](http://github.com/rubyphunk/rspactor "rspactor").

I found [watchr](http://github.com/mynyml/watchr "watchr") and came up with [this script](http://gist.github.com/251881 "watchr script"), which simply watches for changes to .clj files in `/src` and `/test` and runs `lein test` in the shell window.

To get started, install watchr

    gem install watchr

and run the script in the home directory for your Leiningen-backed clojure project.

    watchr /path/to/script

The script also does some (very basic) red/green colouring of outputs using zsh color codes.

Sample output:
![Sample output](/files/lein-autotest.png "sample output")

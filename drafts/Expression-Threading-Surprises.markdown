I was recently surprised whilst testing out my clojure refactoring
tool that the follwing thread-last expression works:

    (->>
        sym
        (rec-contains? (rest node))
        (for [sym *binding-forms*])
        (some #(= % true))
        (not))

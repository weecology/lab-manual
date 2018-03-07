## Modularize

* Break code into chunks. Ideally functions (but separating by comment blocks is better than nothing).
* Functions are good for readability even if they aren't called repeatedly.

## Documentation

* [Document what the code does and how to use it, not how it does it](http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745#s8)
* Use standard documentation comment styles
    * R: [roxygen](http://r-pkgs.had.co.nz/man.html)
    * Python: [docstrings](https://www.python.org/dev/peps/pep-0257/)
    * These can create formatted documentation, but they are useful visual indicators even if you don't do this

## Naming

* Pothole casing for variables and functions `portal_data`
    * Do not use `.` in names (this is very R specific and even [Hadley says not to](http://adv-r.had.co.nz/Style.html))
* Concise and meaningful, but meaningful is more important than concise
* No single letter names unless it is representing equations

## White space

* spaces after commas
* spaces around operators (unless inside the argument definitions in Python)
* no spaces around parentheses

## Line length

* Lines <= 80 characters
    * But a few extra characters can be better than confusing contortions to make length
* Parentheses with breaks after commas are typically better than line break characters (but not always)

## Indentation

* Always indent to indicate that code is inside a function, loop, etc. (Python makes you do this. Thanks Python!)
* Use spaces, not tabs (but it's fine for you IDE to turn the tab key into spaces)
* Follow language convention for number of spaces
    * R: 2
    * Python: 4
* When breaking lines with parentheses (mostly in function calls/definitions) align with the leading character after the opening parenthesis
    ```
    (stuff, things,
     more_things)
    ```
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

* Use snake_case for variables and functions `portal_data`
    * Do not use `.` in names (this is very R specific and even [Hadley says not to](http://adv-r.had.co.nz/Style.html))
* Be concise and meaningful, but meaningful is more important than concise
* No single letter names unless it is representing equations
* Constants, and only constants, should be in all caps
* For object oriented programming in Python use UpperCamelCase for class names

## White space

* spaces after commas
* spaces around operators (unless inside the argument definitions in Python)
* no spaces around parentheses

## Line length

* Lines <= 80 characters
    * But a few extra characters can be better than confusing contortions to make length
* Parentheses/brackets/braces with breaks after commas are typically better than line break characters (but not always)

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

## Loops

* Loop over items unless you actually need indices

## Language specific style guides

* Follow official language style guides (within reason). This helps make your code broadly readable and makes external contributions more likely.
    * Python: [Official Python Style Guide (PEP8)](https://www.python.org/dev/peps/pep-0008/)
    * Julia: [Official Julia Style Guide](https://docs.julialang.org/en/stable/manual/style-guide/)
    * R: [Hadley Wickham's style guide](http://adv-r.had.co.nz/Style.html). This isn't official, or broadly agreed on, but it serves as the base (or at least justification) for a lot of what we do

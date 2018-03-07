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
    * Do not use `.` in names (this is very *R* specific and [Hadley says not to](http://adv-r.had.co.nz/Style.html))
* Concise and meaningful, but meaningful is more important than concise
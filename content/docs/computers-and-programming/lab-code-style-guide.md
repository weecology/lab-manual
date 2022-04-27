---
title: "Lab Style Guide for Code"
linkTitle: "Code Style Guide"
---

# Guiding Principles

This document provides a guide to code structure and formatting across languages used within the Weecology projects. Links to language-specific guides are provided below.

Generally, this guide follows the principles outlined [here](http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745#s2). In particular:
1. Write and style your code for human readers
2. Minimize the number of facts a reader is expected to hold at one time
3. Use consistent, distinct, and meaningful names
4. Employ consistent style and formatting

# Structure 

## Modularize

* Break code into chunks corresponding to contained tasks 
* Whenever possible write code into functions, even if the function isn't called repeatedly

## Loops

* Loop should be used with repeated tasks unless you actually need the indices
* If the language allows, use vectorized functions in place of loops to speed computation and reduce code volume

# Style

## Naming

* Be concise and meaningful, but conveying meaning is more important than brevity
    * Document abbreviations if they are not common or immediately intuitive
    * Functions are verbs, variables are nouns
* Use snake_case for variables and functions (e.g., `portal_data`)
    * Exceptions: 
        * established prefixes (e.g., `n` in `nobs` to indicate the number of observations)
        * established suffixes (e.g., `i` in `obsi` to indicate the specific observation in a for loop)
* Use UpperCamelCase for class names for object oriented programming (primarily in Python) 
* Do not use `.` in names ([particularly in R](http://adv-r.had.co.nz/Style.html))
* Do not use single-letter names 
    * Exceptions: 
        * representing a term in an equation (e.g., `y` in `y = m * x + b`)
        * using an established name in a language (e.g., `n` references the number of draws from a random variable in R)
* Constants, and only constants, should be in all caps

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

## References

* Magic numbers (numeric references to elements, columns, rows, etc.) should be avoided. 
* References should be made by name or-in the case of loops-position. 

# Documentation

## In-line commenting

* [Document what the code does and how to use it, not how it does it](http://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745#s8)

## External documentation

* Use standard documentation comment styles
    * R: [roxygen](http://r-pkgs.had.co.nz/man.html)
    * Python: [docstrings](https://www.python.org/dev/peps/pep-0257/)
    * These can create formatted documentation, but they are useful visual indicators even if you don't do this

# Language specific style guides

* Follow official language style guides (within reason). This helps make your code broadly readable and makes external contributions more likely.
    * Python: [Official Python Style Guide (PEP8)](https://www.python.org/dev/peps/pep-0008/)
    * Julia: [Official Julia Style Guide](https://docs.julialang.org/en/stable/manual/style-guide/)
    * R: [Hadley Wickham's style guide](http://adv-r.had.co.nz/Style.html). This isn't official, or broadly agreed on, but it serves as the base (or at least justification) for a lot of what we do

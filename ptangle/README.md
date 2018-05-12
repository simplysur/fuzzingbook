# Generating Software Tests

This is the repository for the book "Generating Software Tests" (working title)

Project page:

	 https://projects.cispa.saarland/zeller/gstbook

## Summary

The idea is to have a _textbook on software test generation,_ teaching students and professionals alike the latest and greatest concepts in test generation.  The book would come with plenty of code samples that allow the reader to immediately try out the concepts as well as extend them for her/his own purposes.  These code samples would come in Python, as the language easily allows for all sorts of code analysis.

## Contents and Organization

The contents and organization of the book would roughly be based on the lecture “Security Testing” that Andreas and Rahul are currently running.  A typical set of chapters could be based on the lectures we have prepared, plus a few more:

1. Introduction
2. Fundamentals of Testing
3. Text-Based Fuzzing
4. Grammar-Based Fuzzing
5. Generating Complex Inputs
6. Mutation-Based Fuzzing
7. Parsing Inputs
8. Simplifying Inputs
9. Search-Based Testing
10. Evolving Test Suites
11. Solving Constraints
12. Symbolic Testing
13. Mining Grammars
14. Taint Analysis
15. Mutation Analysis
16. Probabilistic Testing
17. Generating Unit Tests
18. Carving Unit Tests
19. Inferring Invariants
20. Protection and Repair
21. Fuzzing in the Large
22. The Future of Test Generation
* Appendix: Glossary

Each chapter would be about 10–20 pages in length, such that the book overall would have about 300 pages.  Keep in mind that the code is (mostly) part of the book, so this is programming as well as writing. Each chapter would come with exercises, typically extending the given code in some way, as well as references to related work.

**Open Issue:** GUI and API fuzzing is not covered (but probably should---possibly by illustrating that a grammar can also produce API calls and/or events).

**Open Issue:** Techniques on unstructured input (e.g. simple random fuzzing or random mutation) should be discussed first before going into grammar-based fuzzing and mutations.


### Title

The working title of the book is "Generating Software Tests".  So far, this has not seen any major objection.


### Glossary

I will start with a glossary of terms that should be consistently used throughout the book.


## Technical Organization

### Literate Programming with Pweave

On the technical side, I would like to adopt a “literate programming” style, where each chapter comes in a single file from which one can extract

* a LaTeX file, to be converted into PDF
* a HTML file, to be read in the browser
* a Python file with all the code

The “literate programming" style would also allow to execute the code samples as they are being typeset; this allows for quality assurance as well as easy explanation of what the code is doing.  For details, see the *pweave* framework:

	http://mpastell.com/pweave/

For your convenience, the "ptangle-demo" folder holds an example with one .texw source file and derived HTML, PDF, and Python files; note how everything including syntax highlighting is done from one source.  The file "gstbook.texw" and the included .texw chapter files will contain the real thing.



### LaTeX Conventions

#### Macros

For the LaTeX side, I will come with central *macros* that should help organize the code.  Please use these as much as possible; avoid introducing macros that replicate existing features.

#### Building

The project comes with a Makefile that allows to create the book (make pdf) as well as derivatives (make html, make code).  See the first lines of the Makefile for examples.  You will need _pweave_ and _htlatex_ installed.

I also have written a shell script _pdflatex.sh_ which works like _pdflatex_, except that the input is a .texw file (and not a .tex file).  This is useful in integrated environments (such as my TextMate editor), where you can then replace the name of your PDFLaTeX binary by "pdflatex.sh".  This script also restores some of the synchronization between the source file and the PDF, such that you can navigate between them.


### Python Conventions

#### Keep Things Simple

For Python, rule number one is to keep things *as simple as possible.*

* Stick to simple functions and data types.  We want our readers to focus on functionality, not Python.
* Avoid Python-specific features.  We want our readers to be able to translate our code into languages of their choice---say, C or Java code.
* Avoid object orientation.  OO in Python is special, so do not burden readers with it unless necessary.  Using existing Python classes is fine, as long as you do not derive new classes from them.
* Avoid defining data structures.  Stick to lists, maps, tuples, as provided by Python.

The exception to the above rules is if a specific Python feature saves so much code that even with its natural language rationale

#### Consistency

Rule number two is *consistency*.  By default, all Python code should follow the rules as set forth in PEP 8:

	https://www.python.org/dev/peps/pep-0008/

We use Python 3 (specifically, Python 3.6) for all code.  Still, try to write code that can be easily backported to Python 2.



### Quality Assurance

#### Assertions

In your code, make use of plenty of assertions that allow to catch errors quickly.  You can also add _hidden assertions_ that would not be included in the final PDF, but still run (and break the build if they fail).


#### Issue Tracker

The GitLab project page allows to enter and track issues.


#### Git

We use git in a single strand of revisions.  Do not branch, do not merge. Sync early; sync often.  Only push if everything builds and passes.


## Publishing

On the publishing side, the could be made available in HTML form during a “beta” phase, with new chapters being published in regular intervals (i.e., one per week), announced on Facebook, Twitter, etc.  This should create some buzz for the printed book and give our colleagues opportunity for feedback.  When the printed book comes out, my idea is that parts of the HTML (say, later chapters or later sections in a number of chapters) would no longer be accessible, asking to purchase the "final" book instead.  We can still update the original sources, such that the Python code can be up-to-date; we can also add more chapters, which would then be available in full until the next edition comes out.  We also have to find a publisher for the book, maybe revitalizing our previous relationship with Morgan Kaufmann.

## Design

### PDF

The printed version (paper and/or PDF/ebook) will be handled by the publisher.  We need to make sure that we can still maintain our source code; that is. we have to include the publisher's style files and react to comments.


### HTML

Regarding design, we will need to find someone with good knowledge in CSS and HTML design, such that we have a nice-looking HTML output

The book "Rust by Example" has a nice functional design, also combining code snippets with explanations.  I love the way you can execute code to see the output - hey, you can even *change* the code (how?):

	https://rustbyexample.com/index.html


### Illustrations

I would love to have some full-page illustrations as in the TeXBook (maybe one per chapter?); pointers to illustrators are welcome.



## Timeframe

Finally, the timeframe. "Security testing" will be taught again starting October 2018, so this would be the time when new material can be beta-tested on a large scale, and at least the early chapters would have to be finalized.

I would love to publish one new chapter per week to the public for general comment; this is something we can also start in October 2018.

Gordon would also like to teach this in Spring 2019; at this point, the manuscript could already have significantly matured, based on feedback by our students and the public feedback.  Hence, this would serve as a second trial run; if all goes well, the manuscript could then go to the editor in Summer 2019.


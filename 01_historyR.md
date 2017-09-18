A Brief History of R
========================================================
author:
date:
autosize: true

What is R?
========================================================

- R is an open source programming language mainly used for __statistics__ and __data science__.

- R is a descendant of S, __a dialect of S__
    - written primarily in C, fortran and R.

- R was created at the University of Auckland (New Zealand) and is currently developed by the R Development Core Team under the __GNU General Public License__
    - the project was conceived in 1992,
    - an initial version (0.16) released in 1995 and
    - first stable version (1.0) for production use in 2000.

---

__What is S?__

- S is a language that was developed in 1976 at Bell Labs (John Chambers and others)
    - an internal statistical analysis environment (implemented as Fortran libraries) used _"to turn ideas into software, quickly and faithfully"_.

- In 1988 Version 3 of the language was rewritten in C and began to resemble what we have today.

- In 1998 Version 4 of the S language was released and it is the version in use today.

- The fundamentals of the S language itself has not changed dramatically since 1998.

- TIBCO (since 2008) is the current owner of the S language and its exclusive developer.

R Philosophy (inherited from the S language)
========================================================

In "Stages in the Evolution of S", John Chambers writes:

> "[W]e wanted users to be able to begin in an interactive environment,
> where they did not consciously think of themselves as programming.
> Then as their needs became clearer and their sophistication increased,
> they should be able to slide gradually into programming, when the
> language and system aspects would become more important."

http://www.stat.bell-labs.com/S/history.html

Features of R
========================================================

- An __open source__ programming language and a software environment for statistical computing and graphics.

- Run on almost any standard computing platform/OS (even on the PlayStation 3)

- Frequent releases (annual + bugfix releases); active development.

- Quite lean, as far as software goes; functionality is divided into modular packages

- Useful for interactive work, and a powerful programming language for developing new tools (user -> programmer)
    - One if the best IDE (RStudio) available on the market.

- A massive set of packages for statistical modelling, machine learning, visualisation, and importing and manipulating data ([CRAN - the Comprehensive R Archive Network](https://cran.r-project.org/)).
    - Cutting edge tools. Researchers in statistics and machine learning will often publish an R package to accompany their articles. This means immediate access to the very latest statistical techniques and implementations(See [Bioconductor](http://bioconductor.org/), open source software for bioinformatics).

- Very active and vibrant user community ([RStudio](https://www.rstudio.com/), Stack Overflow, R-help mailing list, ...)
    - academic world & companies (IBM, Microsoft, RStudio, ...)




Features of R (Cont'd)
========================================================

It is free, as __free software.__ It allows the following _freedoms_:

-   The freedom to run the program, for any purpose (__freedom 0__).

-   The freedom to study how the program works, and adapt it to your needs (__freedom 1__).

-   The freedom to redistribute copies so you can help your neighbor (__freedom 2__).

-   The freedom to improve the program, and release your improvements to the public, so that the whole community benefits (__freedom 3__).

https://www.r-project.org/Licenses/, http://www.fsf.org

Drawbacks of R
========================================================

-   Essentially based on 40 year old technology, but __things are quickly changing__...
    - integration R and Spark - see [`sparklyr`](https://spark.rstudio.com/) package
    - web application as data products [shinyApps.io](https://www.shinyapps.io/) ([gallery](https://shiny.rstudio.com/gallery/))

-   Functionality is based on consumer demand and user contributions.
    - If no one feels like implementing your favorite method, then it's *your* job! _(Or you need to pay someone to do it)_

- Much of the R code you'll see in the wild is written in haste to solve a pressing problem. As a result, code is not very elegant, fast, or easy to understand. Most users do not revise their code to address these shortcomings.
    - but __things are changing__, more and more software developers are joining...
        - unit testing (`testthat` package), continuous building/ integration/ deployment ([travis CI](https://travis-ci.org/))

- R is not a particularly fast programming language, and poorly written R code can be terribly slow. Memory, processing, ....

-   Not a __silver bullet__, not ideal for all possible situations.


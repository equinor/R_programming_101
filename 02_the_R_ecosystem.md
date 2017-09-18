The R Ecosystem
========================================================
author:
date:
autosize: true

The R environment
========================================================

The R environment is divided in 2 different conceptual parts:

- the _"base"_ R system, what is installed when installing R from __CRAN__, and
- everything else.

R functionality is divided into __packages__ and the _"base"_ R system contains the core functionality required to run R
- the `base` package, and
- other packages like  `utils, stats, datasets, graphics, grDevices, grid, methods, tools, parallel, compiler, splines, tcltk, stats4`

More functionality can be added to the R environment installing the relevant packages.

---

__What is a package?__

A __package__ is essentially a __library__ designed to accomplish a task or a set of tasks. E.g. the `tidyr` package provides functionality for data tidying, the `ggplot2` package provides functionality for plotting and visualization, ...

Packages can be found in
- [CRAN](https://cran.r-project.org/)
- [BioConductor](http://bioconductor.org/)
- GitHub/ BitBucket ([an example](https://github.com/tidyverse/tidyr))

Package Management
========================================================

__Installing Packages__

From CRAN/ local file

<font size = "6px">
```r
# Installing new packages
# 1. Use the RSTUDIO IDE:
#    Tools->Install Packages...

# 2. Use command line
install..packages("...")
```
</font>

From GitHub/ BitBucket

<font size = "6px">
```r
# Installing new packages

require(devtools)
install_github(repo = "", username = "...")

# Note! Sometime the repository contains source code
# then the proper compilers must be installed.
```
</font>

---

__Loading and Unloading Packages__

A package needs to be loaded only once in a R session.

<font size = "6px">
```r
# Loading a package
#   resilient: return TRUE if done, otherwise FALSE
require(packageName)

#   throw an error if not done
library(packageName)

#   load the required function in the package
packageName::function
```
</font>

<font size = "6px">
```r
# unloading a package
detach("package:packageName")
```
</font>

__Removing Packages__

<font size = "6px">
```r
# 1. Use the RSTUDIO IDE - Packages tab

# 2. Command line
remove.packages(...)
```
</font>

Getting Help
========================================================

There are many resources on the Internet and, because of its single-letter name, R is difficult to search for using general-purpose search engines such as Google.

- __Searching for more information and help__

    - The Comprehensive R Archive Network (CRAN) at http://cran.r-project.org/
    - The R Project home page, http://www.r-project.org/
        - See __Manuals__ section.
        - See __Search__ section.

    - Stack Overflow


- __Asking for help__

    - R email lists at http://www.r-project.org/mail.html.

Getting Help  (Cont'd)
========================================================

__The `help` function__ can be used to get online help.

```r
# We want to get some more information about the args function
help(args)

# a shortcut...
?args

# working with special characters
?"+"
?"for"
```

__The `example` function__ can be used to run examples provided in the help entries.

```r
help(args)
# In most of the online help pages there is an Examples section
# with some examples on how to use what we have been searching for
# some examples can be run using the example function

example(args)

# Another example
# 'persp' draws perspective plots of a surface over the x–y plane
example(persp)
```

Getting Help (Cont'd)
========================================================

If you do not know exactly what you are looking for. `help.search` can be used to perform a Google-style search through R documentation.

```r
help.search("multivariate normal")

# shortcut
??"multivariate normal"
```

If you want to access information related to a specific package...

```r
help(package=dplyr)
```

Some other topics...

```r
?files
?Arithmetic

# Arithmetic, Comparison, Control, Dates, Extract, files, Math, Memory, NA
# NULL, NumericaConstants, Paren, Quotes, Startup, Syntax
```

The [`sos`](https://cran.r-project.org/web/packages/sos/index.html) package offers highly sophisticated searching of R materials (instaled packages).


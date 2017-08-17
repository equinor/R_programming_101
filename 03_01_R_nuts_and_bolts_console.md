R nuts and bolts: Console Input and Evaluation
========================================================
author:
date:
autosize: true

Entering Input
========================================================

At the R prompt we type expressions. The `<-` symbol is the assignment operator.

```r
> x <- 1
> print(x)
[1] 1
> x
[1] 1
> msg <- "hello"
```

The grammar of the language determines whether an expression is complete or not.

```r
> x <-  ## Incomplete expression
```

The # character indicates a comment. Anything to the right of the # (including the # itself) is ignored.

Evaluation & Printing
========================================================

When a complete expression is entered at the prompt, it is evaluated and the result of the evaluated expression is returned. The result may be auto-printed.

```r
> x <- 5  ## nothing printed
> x       ## auto-printing occurs
[1] 5
> print(x)  ## explicit printing
[1] 5
```

The `[1]` indicates that `x` is a vector and `5` is the first element.

Hands-On (15 minutes)
========================================================

```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Basic Building Blocks" entry [1]

# Enjoy :)
```

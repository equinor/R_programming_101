R nuts and bolts: Console Input and Evaluation
========================================================
author:
date:
autosize: true

How To Run R
========================================================

R actually operates in two modes: _interactive_ and _batch_.

- _Interactive mode_, the one typically used where you (as the user) type in a command and R display the result and so on. Note that R commands can also be stored in a file (convetion: suffix .r or .R).

- _Batch mode_, it does not require interaction with the user. It is useful for pipeline, production and automated jobs.

The main mode for us is __Interactive Mode__ through the R Console.

Entering Input
========================================================

Started a R session, in the R console at the R prompt we type expressions. The grammar of the language determines whether an expression is complete or not.

- The `<-` symbol is the assignment operator. `=` symbol could be used but it is discouraged cause does not work in special situation.
- The # character indicates a comment. Anything to the right of the # (including the # itself) is ignored.

```r
> x <- 1 # complete expression
> msg <- "hello" # complete expression
```


```r
> x <-  ## Incomplete expression - you will be asked to continue in the next line (+)
+
```

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

Note! The `[1]` indicates that `x` is a vector and `5` is the first element.

First R Session
========================================================

```r
> x <- c(1,2,3)
> #show the content of x

> y <- c(x,4,x)
> # show the content of y & its length

> y[2:4]

> data() #show the available datasets
> #use the Nile dataset - what is it about?
> hist(Nile)
> #calculate the mean and standard deviation

> # to quite the R Session use q()
```


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

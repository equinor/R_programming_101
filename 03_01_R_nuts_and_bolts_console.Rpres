R Nuts and Bolts: Getting Started
========================================================
author:
date:
autosize: true

How To Run R
========================================================

R actually can operate in two modes: an _interactive_ mode and a _batch_ mode.

- _Interactive_ mode, require an interacion with the user.
    - A R session is started.
    - The user types in/ executes a command or a set of commands.
    - R displays the result and so on.

- _Batch_ mode, it does not require interaction with the user.
    - It is useful for implementing __pipelines__, __production and automated jobs__, __reproducible research__.

Note! We will run R in an __interactive__ mode through the R Console/ IDE.

Some Basic Information
========================================================

- The # character indicates a comment. Anything to the right of the # (including the # itself) is ignored.

```r
> # This is a comment
```

- The `<-` symbol is the assignment operator.
    - `=` symbol could be used but it is discouraged cause does not work in special situation (historical reason).

```r
> x <- 1 # Assign 1 to x
> msg <- "hello" # Assign "hello" to msg
```

- The grammar of the language determines whether an expression is complete or not.

```r
> x <- 1 # complete expression
>
```

```r
> x <-  # Incomplete expression - you will be asked to continue in the next line (+)
+
```

Some Basic Information (Cont'd)
========================================================

When a complete expression is entered at the prompt, it is evaluated/ executed and the result of the evaluated expression is returned. The result may be auto-printed.

```r
> x <- 5  # Assignment - nothing printed

> x       # auto-printing occurs, normally used when working in interaction mode
[1] 5

> print(x)  ## explicit printing, normally used when working with function
[1] 5
```

Note! The `[1]` indicates that `x` is a vector and `5` is the first element.

A First R Session
========================================================

```r
> x <- c(1,2,3) # Create a vector and assign to x
> x # show the content of x

> y <- c(x,4,x) # Create a new vector based on x
> print(y) # show the content of y & its length

> y[2:4] # (Subsetting) Get 2nd to 4th elements of y

> data() # Show the available datasets (default)

> ?Nile # Nile dataset - what is it about?
> View(Nile) # Show its content

> hist(Nile) # plot an histogram of Nile dataset

> mean(Nile) #calculate the mean and standard deviation
> sd(Nile) #calculate the standard deviation
```


Hands-On (15 minutes)
========================================================

```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Basic Building Blocks" entry [1]
```

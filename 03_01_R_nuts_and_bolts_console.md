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

<font size = "6px">
```r
> # This is a comment
```
</font>

- Variables, R does __not require variable types to be declared__.
    - A variable can take on any available data type (at any point)

    - Variable Assignment is performed using the assignment operator `<-` or `assign` function.
        - `=` operator could be used but it is discouraged cause does not work in special situation (historical reason).

<font size = "6px">
```r
> x <- 1 # Assign 1 to x
> x
[1] 1
> x <- "hello" # Assign "hello" to x
> x
[1] "hello""

> assign("j", 4)
> j
[1] 4
```
</font>


Some Basic Information (Cont'd)
========================================================

- The grammar of the language determines whether an expression is complete or not. When a complete expression is entered at the prompt, it is evaluated/ executed.

<font size = "6px">
```r
> x <- 1 # complete expression
>
```

```r
> x <-  # Incomplete expression - you will be asked to continue in the next line (+)
+
```
</font>

- Printing...

<font size = "6px">
```r
> x <- 5  # Assignment - nothing printed

> x       # auto-printing occurs, normally used when working in interaction mode
[1] 5

> print(x)  ## explicit printing, normally used when working within function
[1] 5
```
</font>

Operators
========================================================

__Arithmetic Operators__: these unary and binary operators perform arithmetic on numeric or complex vectors (or objects which can be coerced to them). See `?Arithmetic` for more information.

<font size = "6px">

```r
+ x
- x
x + y
x - y
x * y
x / y
x ^ y
x %% y
x %/% y
```
</font>

---

__Logical Operators__: these operators act on raw, logical and number-like vectors. See `?Logical` for more information.

<font size = "6px">

```r
! x
x & y #  elementwise comparisons
x && y # only the first element of vectors
x | y
x || y
xor(x, y)

isTRUE(x)
```
</font>


A First R Session
========================================================

<font size = "6px">
```r
> 5 + 3 # Use as a calculator
[1] 8

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
</font>

Hands-On (15 minutes)
========================================================

```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Basic Building Blocks" entry [1]
```

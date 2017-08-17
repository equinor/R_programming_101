R nuts and bolts: Data Types
========================================================
author:
date:
autosize: true

Atomic Classes
========================================================

R has five basic or "atomic" classes (aka atomin modes):

-   __character__ (Strings)
    - Ex. "Survived"

-   __numeric__ (default to floating point numbers)
    - Ex. 3.14

-   __integer__
    - Ex. 3

-   __complex__
    - Ex. 1 + 1i

-   __logical__
    - Ex. TRUE/FALSE


Numbers
========================================================

-   Numbers in R a generally treated as numeric objects (i.e. double
    precision real numbers)

    -   If you explicitly want an integer, you need to specify the ```L```
    suffix

    -   Ex: Entering ```1``` gives you a numeric object; entering ```1L```
    explicitly gives you an integer.

-   There is also a special number ```Inf``` which represents infinity;
    e.g. ```1 / 0```; ```Inf``` can be used in ordinary calculations;
    e.g. ```1 / Inf``` is 0

-   The value ```NaN``` represents an undefined value ("not a number");
    e.g. 0 / 0; ```NaN``` can also be thought of as a missing value
    (more on that later)


Compound Objects
========================================================

- Vector,
- List,
- Factor,
- Matrix,
- Data frame, ..

Vector
========================================================

__The most basic object is a vector__

-   A vector can only contain objects of the same class

Vector: Creating vectors
========================================================

Using the `vector()` function to create an empty vector

```r
> x <- vector("numeric", length = 10)
> x
 [1] 0 0 0 0 0 0 0 0 0 0
```

Vector: Creating vectors
========================================================

The `c()` function can be used to create vectors of objects.

```r
> x <- c(0.5, 0.6)       ## numeric
> x <- c(TRUE, FALSE)    ## logical
> x <- c(T, F)           ## logical
> x <- c("a", "b", "c")  ## character
> x <- c(1L, 2L)         ## integer
> x <- 9:29              ## integer
> x <- c(1+0i, 2+4i)     ## complex
```

Vector: Mixing Objects
========================================================

A vector can contain objects of the same class. What about the following?

```r
> y <- c(1.7, "a")   ## character
> y <- c(TRUE, 2)    ## numeric
> y <- c("a", TRUE)  ## character
```

When different objects are mixed in a vector, _automatic coercion_ occurs so that every element in the vector is of the same class.

Vector: Explicit Coercion
========================================================

Objects can be explicitly coerced from one class to another using the `as.*` functions, if available.

```r
> x <- 0:6
> class(x)
[1] "integer"

> as.numeric(x)
[1] 0 1 2 3 4 5 6

> as.logical(x)
[1] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE

> as.character(x)
[1] "0" "1" "2" "3" "4" "5" "6"
```
---

Nonsensical coercion results in `NA`s.

```r
> x <- c("a", "b", "c")
> as.numeric(x)
[1] NA NA NA
Warning message:
NAs introduced by coercion
```

List
========================================================

Lists are a special type of vector that can contain elements of different classes.

```r
> x <- list(1, "a", TRUE, 1 + 4i)
> x
[[1]]
[1] 1

[[2]]
[1] "a"

[[3]]
[1] TRUE

[[4]]
[1] 1+4i
```

Lists are quite important in R, eg. objects (OO) are list with attributes.

Hands-On (15 minutes)
========================================================


```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Vectors" entry [4]

# Enjoy :)
```

Factors
========================================================

**Factors are used to represent categorical data.**

Factors can be unordered or ordered. One can think of a factor as an integer vector where each integer has a _label_.

Using factors with labels is _better_ than using integers because factors are self-describing; having a variable that has values “Male” and “Female” is better than a variable that has values 1 and 2.

---

```r
> x <- factor(c("yes", "yes", "no", "yes", "no"))
> x
[1] yes yes no yes no
Levels: no yes

> table(x)
x
no yes
 2   3

> unclass(x)
[1] 2 2 1 2 1
attr(,"levels")
[1] "no"  "yes"
```

Factors (Cont'd)
========================================================

The order of the levels can be set using the `levels` argument to `factor()`.

```r
> x <- factor(c("yes", "yes", "no", "yes", "no"),
              levels = c("yes", "no"))
> x
[1] yes yes no yes no
Levels: yes no
```

Matrices
========================================================

Matrices are vectors with a _dimension_ attribute. The dimension attribute is itself an integer vector of length 2 (nrow, ncol)

```r
> m <- matrix(nrow = 2, ncol = 3)
> m
     [,1] [,2] [,3]
[1,]   NA   NA   NA
[2,]   NA   NA   NA

> dim(m)
[1] 2 3

> attributes(m)
$dim
[1] 2 3
```

---

Matrices are constructed _column-wise_.

```r
> m <- matrix(1:6, nrow = 2, ncol = 3)
> m
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6
```

Matrices (Cont'd)
========================================================

Matrices can be created by _column-binding_ or _row-binding_ with `cbind()` and `rbind()`.

```r
> x <- 1:3
> y <- 10:12
> cbind(x, y)
     x  y
[1,] 1 10
[2,] 2 11
[3,] 3 12
> rbind(x, y)
  [,1] [,2] [,3]
x    1    2    3
y   10   11   12
```

Data Frames
========================================================

__Data frames__ are used to store tabular data. Seen as __a special type of list where every element of the list has to have the same length__ and __each element of the list can be thought of as a column__.

Unlike matrices, __data frames__ can store different classes of objects in each column (just like lists); matrices must have every element be the same class

__Data frames__ also have a special attribute called `row.names`

__Data frames__ are usually created by calling `read.table()` or `read.csv()`

---

```r
> x <- data.frame(foo = 1:4, bar = c(T, T, F, F))
> x
  foo   bar
1   1  TRUE
2   2  TRUE
3   3 FALSE
4   4 FALSE

> nrow(x)
[1] 4

> ncol(x)
[1] 2
```

Hands-On (15 minutes)
========================================================


```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Matrices and Data Frames" entry [7]

# Enjoy :)
```

Missing Values
========================================================

__Missing values__ are denoted by `NA` or `NaN` for undefined mathematical operations.

- `is.na()` is used to test objects if they are `NA`

- `is.nan()` is used to test for `NaN`

- `NA` values have a class also, so there are integer `NA`, character `NA`, etc.

- A `NaN` value is also `NA` but the converse is not true

---

```r
> x <- c(1, 2, NA, 10, 3)
> is.na(x)
[1] FALSE FALSE  TRUE FALSE FALSE

> is.nan(x)
[1] FALSE FALSE FALSE FALSE FALSE

> x <- c(1, 2, NaN, NA, 4)
> is.na(x)
[1] FALSE FALSE  TRUE  TRUE FALSE
> is.nan(x)
[1] FALSE FALSE  TRUE FALSE FALSE
```

Attributes
========================================================

R objects can have attributes

-   names, dimnames

-   dimensions (e.g. matrices, arrays)

-   class

-   length

-   other user-defined attributes/metadata

Attributes of an object can be accessed using the ```attributes()``` function.

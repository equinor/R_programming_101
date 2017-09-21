R Nuts and Bolts: Data Types
========================================================
author: Pier Lorenzo Paracchini
date: 20.09.2017
autosize: true
font-import: http://fonts.googleapis.com/css?family=Risque
font-family: 'Risque'

Atomic Classes
========================================================

R has five basic types or "atomic" classes (aka modes):

-   __character__ (Strings)
    - Ex. "Survived"

-   __numeric/ double__ (default to floating point numbers)
    - Ex. 3.14

-   __integer__
    - Ex. 3

-   __complex__
    - Ex. 1 + 1i

-   __logical__
    - Ex. TRUE/FALSE

---

__More on numbers__

-   Numbers in R a generally treated as numeric/ double objects (i.e. double
    precision real numbers)

    -   If you explicitly want an integer, you need to specify the ```L```
    suffix

    -   Ex: Entering ```1``` gives you a numeric/ double object; entering ```1L```
    explicitly gives you an integer.

-   There is also a special number ```Inf``` which represents infinity;
    e.g. ```1 / 0```; ```Inf``` can be used in ordinary calculations;
    e.g. ```1 / Inf``` is 0

-   The value ```NaN``` represents an undefined value ("not a number");
    e.g. 0 / 0; ```NaN``` can also be thought of as a missing value
    (more on that later)


R Objects
========================================================

- Vectors,
- Lists,
- Factors,
- Matrices,
- Data frames

`mode` and `typeof` functions can be used to understand the internal type or storage mode for an R object.


Vectors: the R workhorse
========================================================

__Vector is the fundamental data type in R.__

- __Scalar__s do not really exist in R, actually a scalar is a vector of 1 element (a special vector).
-   A vector can __only contain objects of the same data type/ atomic class__,
    - in other words, elements of a vector are all of the same type.
- The __size of a vector__ is __determined at its creation__,
    - so if you wish to add or delete elements, you’ll need to reassign the vector.

---

<font size = "6px">

```r
# Scalar -> vector of 1 element
x <- 8
x
[1] 8
```
</font>

<font size = "6px">

```r
x <- c(88,5,12,13)

# Insert a new element (168) in the vector
# just  before the 13
x <- c(x[1:3],168,x[4])
x
[1]  88   5  12 168  13
```
</font>

Vectors: How to create vectors
========================================================

The `c()` (concatenate) function can be used to create vectors.

<font size = "6px">

```r
x <- c(0.5, 0.6)       ## numeric vector
x <- c(1L, 2L)         ## integer vector

x <- c(TRUE, FALSE)    ## logical vector
x <- c(T, F)           ## logical vector

x <- c("a", "b", "c")  ## character vector

x <- c(1+0i, 2+4i)     ## complex vector
```
</font>

The `:` operator can be used to create `integer` vectors.

<font size = "6px">

```r
x <- 5:10
x
[1]  5  6  7  8  9 10

typeof(x)
[1] "integer"
```
</font>

---

Using the `vector()` function to create an empty vector. It creates a vector of the given _mode_ and _length_.

Note! Logical vector elements are initialized to FALSE, numeric vector elements to 0, character vector elements to ""...

<font size = "6px">

```r
x <- vector("numeric", length = 10)
x
 [1] 0 0 0 0 0 0 0 0 0 0

mode(x)
[1] "numeric"

length(x)
[1] 10
```
</font>

Other functions used for creating vectors are `seq()` and `rep()`.

<font size = "6px">

```r
seq(0, 1, length.out = 11)
 [1] 0.0 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1.0

rep(x = 1:4, times = 2)
[1] 1 2 3 4 1 2 3 4
```
</font>

Vectors: Length of a vector
========================================================

The `length()` function can be used to obtain the length of a vector.

<font size = "6px">

```r
x <- c(1,2,4)
length(x)
[1] 3
```
</font>

You need to be careful using length...

<font size = "6px">

```r
x <- c() # Equivalent to x <- NULL
x
NULL

length(x)
[1] 0

# What does it happen if i want to create an index
# used to loop through the element of a vector
# for example: i in 1:length(x)
for(i in 1:length(x)) print(i)
[1] 1
[1] 0

1:length(x)
[1] 1 0
```
</font>

Vectors: Implicit Coercion
========================================================

A vector contains only objects of the same (atomic) class/ data type.

__What does it happen when we try to mix different types within the same vector?__

<font size = "6px">

```r
# Mixing numeric (double) with characters
y <- c(1.7, "a")   # coerced to character
typeof(y)
[1] "character"
y
[1] "1.7" "a"  
# Mixing boolean with numeric
y <- c(TRUE, FALSE, 2)    # coerced to numeric (double)
typeof(y)
[1] "double"
y
[1] 1 0 2

# Mixing boolean with character
y <- c("a", TRUE)  ## coerced to character
typeof(y)
[1] "character"
y
[1] "a"    "TRUE"
```
</font>

When different objects are mixed in a vector, _automatic/ implicit coercion_ occurs so that every element in the vector is of the same class.

Vectors: Explicit Coercion
========================================================

Objects can be explicitly coerced from one class to another using the `as.*` functions, if available.

<font size = "6px">

```r
x <- 0:6
typeof(x)
[1] "integer"
x
[1] 0 1 2 3 4 5 6

y <- as.numeric(x)
typeof(y)
[1] "double"
y
[1] 0 1 2 3 4 5 6

as.logical(x)
[1] FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE

as.character(x)
[1] "0" "1" "2" "3" "4" "5" "6"
```
</font>

---

Nonsensical coercion results in `NA`s.

<font size = "6px">

```r
x <- c("a", "b", "c")
as.numeric(x)
Warning: NAs introduced by coercion
[1] NA NA NA
```
</font>

Vectors: Vectorized Operations
========================================================

The operation/ function applied to a vector is __actually individually applied to each element__ of the vectors (__default behaviour__).

Many operations in R are __vectorized__ making code more efficient, concise and easier to read (but _challenging to write_). Examples of __vectorized__ operations/ functions are the `+`, `*` and `>` operators (this applies to many other built-in R functions).

---

<font size = "6px">

```r
x <- 1:4; y <- 6:9
x + y
[1]  7  9 11 13

"+"(x,y)
[1]  7  9 11 13

x * y
[1]  6 14 24 36

x / y
[1] 0.1666667 0.2857143 0.3750000 0.4444444
```
</font>

<font size = "6px">

```r
x <- 1:4
x > 2
[1] FALSE FALSE  TRUE  TRUE
```
</font>

<font size = "6px">

```r
sqrt(1:6)
[1] 1.000000 1.414214 1.732051 2.000000 2.236068 2.449490
```
</font>


Vectors: Recycling
========================================================

When applying an operation to two vectors that requires them to be the same length, R automatically __recycles__ the shortest one. It repeats, the shorter one, until it is long enough to match the longer one (a warning could be generated in the process).

---

<font size = "6px">

```r
# longer object length multiple of shorter object length
c(1,2,3) + c(1,2,3,4,5,6)
[1] 2 4 6 5 7 9

# this is what is actually happening (recycling)
c(1,2,3,1,2,3) + c(1,2,3,4,5,6)
[1] 2 4 6 5 7 9
```
</font>

<font size = "6px">

```r
# longer object length not multiple of shorter object length
c(1,2) + c(1,2,3,4,5)
Warning in c(1, 2) + c(1, 2, 3, 4, 5): longer object length is not a
multiple of shorter object length
[1] 2 4 4 6 6

# this is what is actually happening (recycling)
c(1,2,1,2,1) + c(1,2,3,4,5)
[1] 2 4 4 6 6
```
</font>

Vectors: Subsetting
========================================================

How to retrieve elements of a vector (__subsetting__).

<font size = "6px">
```
my_vector[the_references]

the_references: the indexes/ the names of the elements
    we are interested in (e.g. 1, c(1,5,..), c(T,F,T,..))
```
</font>

<font size = "6px">

```r
x <- c(10,20,30,40,50,60,70,80,90,100)

# Using indexes
x[10] # Get the 10th element
[1] 100

x[c(4,6)] # Get the 4th and 6th elements
[1] 40 60

# Get all elements > 50
x[x > 50]
[1]  60  70  80  90 100

x[which(x > 50)]
[1]  60  70  80  90 100

# Using names
names(x) <- c("a", "b", "c", "d", "e", "f", "g", "h", "i", "l")

x["d"]
 d 
40 
```
</font>

Vectors: Testing Vector Equality
========================================================

<font size = "6px">

```r
# Testing Vector Equality Using ==
# remember that == is a vectorized operation
x <- 1:3
y <- c(1,3,4)
x == y
[1]  TRUE FALSE FALSE

all(x == y)
[1] FALSE
FALSE
[1] FALSE

x <- 1:3
y <- c(1,2,3)
all(x == y)
[1] TRUE

# Testing Vector Equality Using identical
# vector elements  must have same type and value (strict)
x <- 1:3
y <- c(1,2,3)
identical(x,y)
[1] FALSE

y <- c(1L,2L,3L)
identical(x,y)
[1] TRUE
```
</font>

Hands-On (10 minutes)
========================================================

<font size = "6px">

```r
# -----------------------------------------------
# Create a numeric vector "age"
# the age of some passengers with values
# 3, 34, 55, 1, 11, 18, 12

# Create a character vector "gender"
# the gender of the passengers with values
# "Female", "Male", "Female", "Male", "Female", "Female", "Male"

# Check which passenger is a child (less than 12)
# and store it in a variable "is_child"
# Do you expect a single logical value?
# Print "is_child"

# Check the gender of the children

# -----------------------------------------------
# Vectorized Operation
# Create a vector v_1 that contains 1,2,3,4,5
# Create a vector v_2 that contains 10,20,30,40,50 (integer)

# Check the data types associated to v_1 and v_2

# Sum v_1 and v_2, what is the expected result
# What is the resulting data type of v_1 + v_2
```
</font>

---

<font size = "6px">

```r
# -----------------------------------------------
# Vectorized Operation with Recycling
# Create a vector v_1 that contains 1,2,3,4,5
# Create a vector v_2 that contains 10

# Sum v_1 and v_2, what is the expected result & why

# -----------------------------------------------
# Create a character vector my_char that contains
# the following words: "My", "name", "is"
# Print the content of my_char
# How many elements are in it?

# Coerce my_char to a numeric. What do you expect?

# -----------------------------------------------
# Create a vector v_1 containing 1,2,1,2,1,2,1,2
# 1,2 repeated 4 times
# Subsetting: get the 2,4,6,8 elements of the vector
```
</font>

More Hands-On (Optional)
========================================================


```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Sequence of Numbers" entry [3]
# Select the "Vectors" entry [4]
# Select the "Subsetting Vectors" entry [6]
```

Lists
========================================================

Lists are a special type of vector (often referred as __recursive vector__) that can contain/ combine elements of different types (even other lists). In R (S3) classes are list with attributes.

How to create a __list__...

<font size = "6px">

```r
x <- list(1, "a", TRUE)
x
[[1]]
[1] 1

[[2]]
[1] "a"

[[3]]
[1] TRUE

# Adding component names/ tags. name, surname, salary tags are optional
j <- list(name = "John", surname = "Doe", salary = 55000)
j
$name
[1] "John"

$surname
[1] "Doe"

$salary
[1] 55000
```
</font>

Lists: Subsetting
========================================================

<font size = "6px">
```
Select one or more elements (list)

the_list[the_references] -> return elements (list)

the_references: the indexes/ the tag of the elements
    we are interested in e.g. 1, c(1,5,..),...
```
</font>

<font size = "6px">

```r
# Retrieving elements in a list using index
z <- list("abc", 1, TRUE)
z[1]
[[1]]
[1] "abc"

z[c(2,3)]
[[1]]
[1] 1

[[2]]
[1] TRUE

# Retrieving elements in a list using tags
z <- list(a = "abc", b = 1, c = TRUE)
z[c("a", "b")]
$a
[1] "abc"

$b
[1] 1
```
</font>

---

<font size = "6px">
```
Select a single element

the_list[[the_reference]] / thelist$tag -> return element

the_reference/ tag: the index/ the tag of the element
    we are interested in e.g. 1, name,...
```
</font>

<font size = "6px">

```r
# Retrieving an element in a list using index
z <- list("abc", 1, TRUE)
z[[1]]
[1] "abc"

# Retrieving an element in a list using tags
z <- list(a = "abc", b = 1, c = TRUE)
z[["c"]]
[1] TRUE

z$c
[1] TRUE
```
</font>

Lists: Adding and Deleting elements to/ from a list
========================================================

Adding Elements to a list

<font size = "6px">

```r
z <- list(a = "abc")
z
$a
[1] "abc"

# Adding an element to a list using tags
z$b <- "sailing"
z
$a
[1] "abc"

$b
[1] "sailing"

# Adding an element to a list using index
z[[3]] <- "sailing"
z
$a
[1] "abc"

$b
[1] "sailing"

[[3]]
[1] "sailing"
```
</font>

---

Deleting Elements from a list

<font size = "6px">

```r
# Deleting an element to a list using tags
# Same can be done using index notation [[i]]
# Set the element to NULL
z <- list(a = "abc", b = TRUE)
z
$a
[1] "abc"

$b
[1] TRUE

# Delete the b tag from the list
z$b <- NULL
z
$a
[1] "abc"
```
</font>

Lists: Getting the size of a list
========================================================

<font size = "6px">

```r
# Create a list of 3 elements
z <- list(a = "abc", b = TRUE, c = 12)
z
$a
[1] "abc"

$b
[1] TRUE

$c
[1] 12

# How to get the size of the list?
length(z)
[1] 3
```
</font>

Hands-On (5 minutes)
========================================================

<font size = "6px">

```r
# -----------------------------------------------
p <- c(2,7,8)
q <- c("A", "B", "C")
# Create a list with element p & q

# Find the length of the list

# Retrieve the 2nd element in the list
# as a list
# and as its original data type
# -----------------------------------------------
```
</font>

---

<font size = "6px">

```r
# -----------------------------------------------
age <- c(3, 34, 55, 1, 11, 18, 12)
gender <- c("Female", "Male", "Female", "Male",
            "Female", "Female", "Male")

# Create a list "passengers" containing age and gender

# Add an element in the list "is_child" (age < 12)
# Print "passengers"

# Add an element in the list "is_not_child" (age >= 12)
# Print "passengers"

# Remove element "is_child" from the list
# Print "passengers"
# -----------------------------------------------
```
</font>


Factors
========================================================

**Factors are used to represent categorical data.**

Factors can be unordered or ordered. One can think of a factor as an integer vector where each integer has a _label_.

Using factors with labels is _better_ than using integers because factors are self-describing; having a variable that has values “Male” and “Female” is better than a variable that has values 1 and 2.

---

<font size = "6px">

```r
x <- factor(c("yes", "yes", "no", "yes", "no"))
x
[1] yes yes no  yes no 
Levels: no yes

table(x)
x
 no yes 
  2   3 

unclass(x)
[1] 2 2 1 2 1
attr(,"levels")
[1] "no"  "yes"
```
</font>

Factors (Cont'd)
========================================================

The order of the levels can be set using the `levels` argument to `factor()`.

<font size = "6px">

```r
x <- factor(c("yes", "yes", "no", "yes", "no"),
              levels = c("yes", "no"))
x
[1] yes yes no  yes no 
Levels: yes no
```
</font>

Matrices
========================================================

Matrices are vectors with a _dimension_ attribute. The dimension attribute is itself an integer vector of length 2 (nrow, ncol).

<font size = "6px">

```r
x <- seq(1:10)
dim(x) <- c(2,5)
x
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10

# matrix(x, nrow = 2)
```
</font>

<font size = "6px">

```r
m <- matrix(nrow = 2, ncol = 3)
m
     [,1] [,2] [,3]
[1,]   NA   NA   NA
[2,]   NA   NA   NA

dim(m)
[1] 2 3

attributes(m)
$dim
[1] 2 3
```
</font>

---

Matrices (by default) are constructed _column-wise_.

<font size = "6px">

```r
m <- matrix(1:6, nrow = 2, ncol = 3)
m
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6
```
</font>

<font size = "6px">

```r
# Default behaviour can be overwritten
# using byrow
matrix(1:6, nrow = 2, byrow = T)
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
```
</font>

Matrices (Cont'd)
========================================================

Matrices can be created by _column-binding_ or _row-binding_ with `cbind()` and `rbind()`.

<font size = "6px">

```r
x <- 1:3
y <- 10:12

cbind(x, y)
     x  y
[1,] 1 10
[2,] 2 11
[3,] 3 12

rbind(x, y)
  [,1] [,2] [,3]
x    1    2    3
y   10   11   12
```
</font>

<font size = "6px">

```r
z <- matrix(1:10, nrow = 2)
rbind(z, 1)
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10
[3,]    1    1    1    1    1
```
</font>


Matrices: Getting the size of a matrix
========================================================

<font size = "6px">

```r
# Create a matrix
z <- matrix(1:100, nrow = 10) # 10-by-10 Matrix

# How to get the number of cells?
# Matrix is a vector so
length(z)
[1] 100

# Dimension of a matrix
dim(z)
[1] 10 10

nrow(z)
[1] 10

ncol(z)
[1] 10
```
</font>

Matrices: Subsetting
========================================================

```
my_matrix[row_references, col_references]

references: the indexes/ the names of the elements
    we are interested in e.g. 1, c(1,5,..), ..
```

<font size = "6px">

```r
x <- matrix(seq(1:12), nrow=3)

# Get the 2nd row
x[2,]
[1]  2  5  8 11

# Get the 1st col
x[,1]
[1] 1 2 3

# Get the 2nd and 3rd element in the 2nd row
x[2, 2:3]
[1] 5 8

# Adding colnames/ rownames
rownames(x) <- c(paste(1:3, "_row", sep = ""))
colnames(x) <- c(paste(1:4, "_col", sep = ""))
x["1_row",]
1_col 2_col 3_col 4_col 
    1     4     7    10 
```
</font>

Data Frames
========================================================

__Data frames__ are used to store tabular data.

A data frame is __a special type of list where every element of the list has to have the same length__ and __each element of the list can be thought of as a column__.

Unlike matrices, __data frames__ can store different classes of objects in each column (just like lists).

__Data frames__ also have a special attribute called `row.names`.

__Data frames__ are usually created by calling `read.table()` or `read.csv()`.


---

<font size = "6px">

```r
x <- data.frame(id = c(1001, 1002, 1003),
                is_male = c(T, T, F))
x
    id is_male
1 1001    TRUE
2 1002    TRUE
3 1003   FALSE

dim(x)
[1] 3 2
nrow(x)
[1] 3
ncol(x)
[1] 2

names(x) # Get the col names
[1] "id"      "is_male"
row.names(x) # Get (set) the col names
[1] "1" "2" "3"
row.names(x) <- paste("obs_", seq(nrow(x)), sep = "")
x
        id is_male
obs_1 1001    TRUE
obs_2 1002    TRUE
obs_3 1003   FALSE
```
</font>

Data Frames: Subsetting
========================================================

<font size = "6px">

```r
patient <- c("pat1", "pat2", "pat3", "pat4")
age <- c(10, 35, 60, 20)
gender <- c("M", "F", "F", "M")
exam_result <- c(1, 0, 0, 1)

df <- data.frame(patient = patient, age = age,
                 gender = gender, exam_result = exam_result)

df
  patient age gender exam_result
1    pat1  10      M           1
2    pat2  35      F           0
3    pat3  60      F           0
4    pat4  20      M           1
```
</font>

---

<font size = "6px">

```r
# select a specific column/ feature e.g age
df$age
[1] 10 35 60 20

df[,c("age")]
[1] 10 35 60 20

df[,2]
[1] 10 35 60 20

# select a specific observation/ row (all features)
df[1,]
  patient age gender exam_result
1    pat1  10      M           1

# select a specific observation/ row (just selected features)
df[1,c("patient", "exam_result")]
  patient exam_result
1    pat1           1
```
</font>


Hands-On (10 minutes)
========================================================

<font size = "6px">

```r
# -----------------------------------------------
# Use the iris dataset
df <- iris

# See the structure of the dataframe using str()
# What do u see?

# Get the name of the features using names()

# Get a summary of the content of the dataframe using summary()
# Any more info?

# Use the table() function on the Species feature
# What can u see?

# Select all of the obervations connected with "Setosa" Species

# -----------------------------------------------
```
</font>


More Hands-On (Optional)
========================================================


```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Matrices and Data Frames" entry [7]

# Enjoy :)
```

NULL & Missing Values
========================================================

`NULL` is actually used to state that sth is __nonexistent__.

- One use of `NULL` is to build up vectors (incrementally) in loops.
- `is.null` is used to test if an object is `NULL`.

<font size = "6px">

```r
#Build up a vector of the even numbers in 1:10
z <- NULL
for(i in 1:10) if(i %% 2 == 0) z <- c(z,i)
z
[1]  2  4  6  8 10
```
</font>

<font size = "6px">

```r
z <- NULL
length(z)
[1] 0

is.null(z)
[1] TRUE
```
</font>

---

__Missing values__ are denoted by `NA` (NotAvailable) or `NaN` (NotANumber) for undefined mathematical operations.

- `is.na()` is used to test objects if they are `NA`
- `is.nan()` is used to test for `NaN`
- `NA` values have a class also, so there are integer `NA`, character `NA`, etc.
- A `NaN` value is also `NA` but the converse is not true


<font size = "6px">

```r
x <- c(1, 2, NA, 10, 3)
is.na(x)
[1] FALSE FALSE  TRUE FALSE FALSE

typeof(x[3])
[1] "double"

is.nan(x)
[1] FALSE FALSE FALSE FALSE FALSE

x <- c(1, 2, NaN, NA, 4)
is.na(x)
[1] FALSE FALSE  TRUE  TRUE FALSE

is.nan(x)
[1] FALSE FALSE  TRUE FALSE FALSE
```
</font>

More Hands-On (Optional)
========================================================


```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Missing Values" entry [5]

# Enjoy :)
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

---

<font size = "6px">

```r
# Vectors can have element names
x <- 1:3
names(x)
NULL

names(x) <- c("foo", "bar", "norf")
x
 foo  bar norf 
   1    2    3 
```
</font>

<font size = "6px">

```r
#List
x <- list(a = 1, b = 2)
x
$a
[1] 1

$b
[1] 2
```
</font>

<font size = "6px">

```r
#Matrix
m <- matrix(1:4, nrow = 2, ncol = 2)
dimnames(m) <- list(c("a", "b"), c("c", "d"))
m
  c d
a 1 3
b 2 4
```
</font>

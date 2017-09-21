R Nuts & Bolts: Writing R functions
========================================================
author: Pier Lorenzo Paracchini
date: 20.09.2017
autosize: true
font-import: http://fonts.googleapis.com/css?family=Risque
font-family: 'Risque'

Writing R functions
========================================================

If we find ourselves running the same code over and over, it is probably a good idea to turn the code into a __function__. There are several reason for doing it, these reasons include __maintainability__ and __code-reuse__.


- Functions are __created__ using the `function()` directive and are __stored__ as R objects (class `function)`.

<font size = "6px">
```r
<arguments>: optionals

f <- function(<arguments>){
    #Body of the function
}

# Good practice to properly indent the code
# in order to increase readibility (not required)
```
</font>

- Being functions R objects
    - functions can be passed as arguments to other functions
    - functions can be nested, possible to define a function within a function



---

__"Hello, You!"__ example

<font size = "6px">

```r
hello.you <- function(firstname, surname){
    hello.msg <- sprintf("Hello %s %s!", firstname, surname)
    print(hello.msg)
}

class(hello.you)
[1] "function"

# Using my function
hello.you(firstname = "John", surname = "Doe")
[1] "Hello John Doe!"
```
</font>

Function Arguments
========================================================

Functions can have named arguments which could have _default values_.

- __Formal arguments__ are the argument included in the function definition
    - `formals()` can be used to get a list of the formal arguments of a function
- Not every function call in R makes use of all of the formal arguments
    - some arguments may be missing or might have default values

---


<font size = "6px">
```r
# a,b,c,d are the formal arguments of the function f
# a,b,c,d are named argument

# a must be provided (mandatory)
# b and c have a defaut value (optional with default)
# d is set to NULL (optional could be missing)

f <- function(a, b = 1, c = 2, d = NULL) {
    # Do something
}
```
</font>


Argument Matching
========================================================

R functions arguments can be matched __positionally__ or __by name__.

<font size = "6px">

```r
f <- function(arg1, arg2, arg3){
    msg <- sprintf("arg1: %s, arg2: %s, arg3: %s",
                   arg1, arg2, arg3)
    print(msg)
}

# Positionally: firstname, surname
f(1, 2, 3)
[1] "arg1: 1, arg2: 2, arg3: 3"

# By name
f(arg1 = 1, arg2 = 2, arg3 = 3)
[1] "arg1: 1, arg2: 2, arg3: 3"
f(arg3 = 3, arg2 = 2, arg1 = 1)
[1] "arg1: 1, arg2: 2, arg3: 3"

# Mix-mode: by name and position
f(arg3 = 3, 1,2)
[1] "arg1: 1, arg2: 2, arg3: 3"
f(arg2 = 2, 1,3)
[1] "arg1: 1, arg2: 2, arg3: 3"
```
</font>

---

It is possible to __mix positional matching with matching by name__.

When an argument is matched by name, it is “taken out” of the argument list and the remaining unnamed arguments are matched in the order that they are listed in the function definition.

<font size = "6px">

```r
f <- function(arg1, arg2, arg3){
    msg <- sprintf("arg1: %s, arg2: %s, arg3: %s",
                   arg1, arg2, arg3)
    print(msg)
}

# Mix-mode: by name and position
# Following calls are all equivalent
f(arg3 = 3, 1,2)
[1] "arg1: 1, arg2: 2, arg3: 3"
f(arg2 = 2, 1,3)
[1] "arg1: 1, arg2: 2, arg3: 3"
```
</font>

__Not recommended__ messing around with the order of the arguments too much, it can become really confusing.

Argument Evaluation: Lazy Evaluation
========================================================

Arguments to functions are evaluated __lazily__, only if needed.

---

This function never actually uses the argument `b`, so calling `f(2)` will not produce an error because the 2 gets positionally matched to `a`.

<font size = "6px">

```r
f <- function(a,b){
    a^2
}

f(2)
[1] 4
```
</font>

Let's rewrite the function in order to use the argument `b`, so calling `f(2)` will now produce an error because the 2 gets positionally matched to `a` and `b`is missing.

<font size = "6px">

```r
f <- function(a,b){
    a + b
}

f(2)
Error in f(2): argument "b" is missing, with no default
```
</font>

The "..." argument
========================================================

The `...` argument indicate a variable number of arguments that are usually passed on to other functions.

- `...` is often used when extending another function and you don’t want to copy the entire argument list of the original function

<font size = "6px">
```r
myplot <- function(x, y, type = "l", ...) {
        plot(x, y, type = type, ...)
}
```
</font>

- `...`  argument is also necessary when the number of arguments passed to the function cannot be known in advance.

<font size = "6px">
```r
> args(paste)
function (..., sep = " ", collapse = NULL)

> args(cat)
function (..., file = "", sep = " ", fill = FALSE,
    labels = NULL, append = FALSE)
```
</font>


__Important!__

One catch with `...` is that any arguments that appear _after_ `...` on the argument list must be named explicitly.


Return Values
========================================================

Functions are generally used for computing some value, so they need a __mechanism to give the value back to the caller__. There are two ways to implement this mechanism:

- the value of the last line of code in the body of a function is automatically returned (__bad practice__)

<font size = "6px">

```r
f <- function (x){
    y <- x^2
    y
}

f(2)
[1] 4
```
</font>

- the `return` command is used to specify the value returned by the funtion (__good practice__)

<font size = "6px">

```r
f <- function (x){
    y <- x^2
    return(y)
}

f(2)
[1] 4
```
</font>

Hands-On (Optional)
========================================================

```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Functions" entry [9]
```

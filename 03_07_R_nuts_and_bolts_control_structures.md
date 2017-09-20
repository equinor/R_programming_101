R Nuts & Bolts: Control structures
========================================================
author: Pier Lorenzo Paracchini
date: 20.09.2017
autosize: true


Control structures
========================================================

__Control structures__ allow to __control__ the __flow of execution__ of the program causing different things to happen based on test condition.

Common structures are:

- `if` and `else`, test a (logical) condition
- `for`, execute a loop a certain number of times
- `while`, execute a loop while a certain (logical) condition is `TRUE`
- `repeat`, execute an infinite loop
- `break`, break the execution of a loop
- `next`, skip an iteration of a loop
- `return`, exit a function

`if` and `else`
========================================================

<font size = "6px">
```r
if(condition){
    # If condition is TRUE
    # DO Something
}


if(condition){
    # If condition is TRUE
    # Do Something
} else {
    # Otherwise
    # Do something else
}

if(condition){
    # If condition is TRUE
    # Do Something
} else if(new_condition){
    # If condition is FALSE and
    # If new_condition is TRUE
    # Do something else
} else {
    # Otherwise
    # Do something else
}
```
</font>

---

<font size = "6px">

```r
x <- 5

if(x > 3){
    print("X is greater than 3.")
}else{
    print("X is not greater than 3.")
}
[1] "X is greater than 3."
```
</font>

<font size = "6px">

```r
x <- 2
y <- 10

if(x > 3){
    print("X is greater than 3.")
}else if(y > 6) {
    print("X is not greater than 3 but y is greater than 6.")
}else{
    print("X is not greater than 3 and y is not greater than 6.")
}
[1] "X is not greater than 3 but y is greater than 6."
```
</font>

`for`
========================================================

`for` loops take an iterator variable and assign it successive values from a sequence or vector. For loops are most commonly used for iterating over the elements of an object (list, vector, etc.)

<font size = "6px">
```r
# This loop takes the `i` variable and in each iteration of the loop
# gives it teh values 1, 2, 3, ..., 10, and then exits.
for(i in 1:10) {
        print(i)
}
```
</font>

`for` loops can be nested but be careful with nesting though - performance and complexity.

<font size = "6px">
```r
x <- matrix(1:6, 2, 3)

for(i in seq_len(nrow(x))) {
        for(j in seq_len(ncol(x))) {
                print(x[i, j])
        }
}
```
</font>

---

Some examples of loops with same behaviours...

<font size = "6px">

```r
x <- c("a", "b", "c", "d")

for(i in 1:length(x)) {
    print(x[i])
}
[1] "a"
[1] "b"
[1] "c"
[1] "d"

for(i in seq_along(x)) {
    print(x[i])
}
[1] "a"
[1] "b"
[1] "c"
[1] "d"

for(letter in x) {
    print(letter)
}
[1] "a"
[1] "b"
[1] "c"
[1] "d"

for(i in 1:4) print(x[i])
[1] "a"
[1] "b"
[1] "c"
[1] "d"
```
</font>

`while`
========================================================

While loops begin by testing a condition. If it is true, then they execute the loop body. Once the loop body is executed, the condition is tested again, and so forth. While loops can potentially result in infinite loops if not written properly. Use with care!

<font size = "6px">

```r
i <- 0
while(i < 10) {
        print(i)
        i <- i + 1
}
[1] 0
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
[1] 6
[1] 7
[1] 8
[1] 9
```
</font>

`repeat`
========================================================

Repeat initiates an infinite loop; these are not commonly used in statistical applications but they do have their uses. The only way to exit a `repeat` loop is to call `break`. Use with care!

<font size = "6px">

```r
i <- 0
repeat{
    if(i >= 10) break
    print(i)
    i <- i + 1
}
[1] 0
[1] 1
[1] 2
[1] 3
[1] 4
[1] 5
[1] 6
[1] 7
[1] 8
[1] 9
```
</font>

`break`, `next` and `return`
========================================================

`break` is used to break the execution of a loop.

<font size = "6px">

```r
for(i in 1:10) {
    if(i > 2) break
    print(i)
}
[1] 1
[1] 2
```
</font>

<font size = "6px">

```r
i <- 0
repeat{
    if(i > 2) break
    print(i)
    i <- i + 1
}
[1] 0
[1] 1
[1] 2
```
</font>

`next` is used to skip an iteration of a loop.

<font size = "6px">

```r
for(i in 1:10) {
        if(i >= 3 && i <= 8) {
                next
        }
        print(i)
}
[1] 1
[1] 2
[1] 9
[1] 10
```
</font>

---

`return` signals that a function should exit and return a given value.

Control structures: Warning
========================================================


When starting to use R, people use loops whenever they need to iterate over elements of a `vector`, `list` or `data.frame`. __Not a good practice__, use __vectorization__ or `apply` family of functions.

Hands-On (Optional)
========================================================

```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Logic" entry [8]
# Select the "lapply and sapply" entry [10]
# Select the "vapply and tapply" entry [11]
```

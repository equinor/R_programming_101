R Nuts and Bolts: Workspace & Files
========================================================
author:
date:
autosize: true

Workspace & Files
========================================================

R provides a common set of commands for interacting with the local environment

- Managing (in-memory) objects in the local workspace
- The working directory
- Managing files in the working directory

Managing (in-memory) objects in the local workspace
========================================================

__How to view objects/ variables created in the local environment...__


```r
#View all the objects in your local workspace
ls()
```

__How to remove objects/ variables created in the local environment...__


```r
#Remove objects from your local workspace
rm()

#example 1
## tmp <- 1
## ls()
## rm(tmp)

#example 2
## tmp1 <- 1
## tmp2 <- 1
## ls()
## rm(list = c("tmp1", "tmp2")
```


The Working Directory
========================================================

The __Working Directory__ is where R and the current session look for files when reading and writing on the local computer.

__How to get the current working directory...__


```r
#Find the current working directory
getwd()
[1] "E:/APPL/workspace_r/R_programming_101"
```

__How to change the current working directory...__


```r
#Change the working directory to a new dir
setwd(...)
```


Managing files on the local computer (working directory)
========================================================


```r
#View all dirs in your working directory (including hidden dirs)
list.dirs()

#Create a directory in the working directory
dir.create()
```


```r
#View all files/ dir in your working directory
list.files()

#Create/ Rename/ Copy/ Remove a file in the working directory
file.create(), file.rename(), file.copy(), file.remove()

file.exists() #Check if a file exists

file.info() #Info about a file

file.path() #Build a path OS agnostic
```

Hands-On (15 minutes)
========================================================


```r
library(swirl)
swirl()
#.....
# Select the "R Programming" entry
# Select the "Workspace and Files" entry [2]

# Exit swirl and return to the R prompt (>) at any time by pressing the Esc key
# type bye() to exit and save your progress
# type info() for more option.
```

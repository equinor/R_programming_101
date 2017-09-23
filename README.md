# R programming 101

__Why learning R?__ R is an extremely versatile open source programming language for statistics and data science. It is widely used in every field where there is data—business, industry, government, medicine, academia, and so on.

As Hadley Wickham [wrote](http://adv-r.had.co.nz/Introduction.html)

```
If you are new to R, you might wonder what makes learning such a quirky language worthwhile. To me, some of the best features are:

- It’s free, open source, and available on every major platform. As a result, if you do your analysis in R, anyone can easily replicate it.

- A massive set of packages for statistical modelling, machine learning, visualisation, and importing and manipulating data. Whatever model or graphic you’re trying to do, chances are that someone has already tried to do it. At a minimum, you can learn from their efforts.

- Cutting edge tools. Researchers in statistics and machine learning will often publish an R package to accompany their articles. This means immediate access to the very latest statistical techniques and implementations.

...

- A fantastic community. It is easy to get help from experts on the R-help mailing list, stackoverflow, or subject-specific mailing lists like R-SIG-mixed-models or ggplot2. You can also connect with other R learners via twitter, linkedin, and through many local user groups.

- Powerful tools for communicating your results. R packages make it easy to produce html or pdf reports, or create interactive websites.

- A strong foundation in functional programming. The ideas of functional programming are well suited to solving many of the challenges of data analysis. R provides a powerful and flexible toolkit which allows you to write concise yet descriptive code.

- An IDE tailored to the needs of interactive data analysis and statistical programming.

- Designed to connect to high-performance programming languages like C, Fortran, and C++.
```


## Getting Ready

Prerequisites for the session

- install R
- install RStudio IDE (optional but preferred)
- install 'swirl' package for hands-on activities

### Install R

The first thing you need to do is to install R on your computer from the [CRAN](https://cran.r-project.org/) site. A step-by-step tutorial on how to install R for Mac and Windows can be found in the following videos

- [Installing R on WIndows](https://www.youtube.com/watch?v=Ohnk9hcxf9M&feature=youtu.be)[1]    
- [Installing R on Mac](https://www.youtube.com/watch?v=uxuuWXU-7UQ&feature=youtu.be)[1]  


### Install RStudio IDE

There is also an integrated development environment available (free) for R that is built by [RStudio](https://www.rstudio.com/products/rstudio/download/). It is a very powerful IDE available for Windows, Mac OS X and Linux. 

A step-by-step tutorial on how to install it can be found in the following video

- [Installing RStudio](https://www.youtube.com/watch?v=bM7Sfz-LADM&feature=youtu.be)[1]

A quick overview of the RStudio IDE and how to write R code in it can be found in the following [webinar](https://www.rstudio.com/resources/webinars/rstudio-essentials-webinar-series-part-1/)[3].

### Install `swirl` and relevant interactive course

`swirl` is a package used for teaching R programming and data science interactively using the R console. To install `swirl` on your computer follows the step-by-step guide provided at this [link](http://swirlstats.com/students.html)[4].

Start `swirl` (__Step 4__) and install the relevant interactice course (__Step 5__) with 

```r
library(swirl)
install_course("R Programming")
swirl()
```

More information on how to install swirl interactive courses can be found [here](https://github.com/swirldev/swirl_courses).

# Presentation Handouts

__Note!__ Optimized for Google Chrome.

[Agenda](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/00_agenda.html#/)  
[Introducing R](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/01_introducing_R.html)  
[The R Ecosystem](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/02_the_R_ecosystem.html)  

__Nuts & Bolts__  
[Getting Started](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_01_R_nuts_and_bolts_getting_started.html)  
[Workspace](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_02_R_nuts_and_bolts_workspace.html)  
[Data Types](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_03_R_nuts_and_bolts_data_types.html)  
[Basic Operations](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_04_R_nuts_and_bolts_basic_operations.html)  
[Reading Data](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_05_R_nuts_and_bolts_reading.html)  
[Plotting](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_06_R_nuts_and_bolts_plotting.html)  
[Control Structures](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_07_R_nuts_and_bolts_control_structures.html)  
[Writing Functions](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_08_R_nuts_and_bolts_functions.html)  
[Scoping](http://htmlpreview.github.io/?https://github.com/Statoil/R_programming_101/blob/master/presentations/03_09_R_nuts_and_bolts_scoping.html)  

# References

[1] "[R Programming](https://www.coursera.org/learn/r-programming)" module in the "Data Science Specialization" Coursera  
[2] "[Mastering Software Development in R](http://rdpeng.github.io/RProgDA/)" by Roger D. Peng, Sean Cross and Brooke Anderson, 2017  
[3] "[R Studio.com](https://www.rstudio.com/)"  
[4] "[Learn R, in R](http://swirlstats.com/)" with swirl  
[5] "[R for Data Science](http://r4ds.had.co.nz/)" by Garrett Grolemund and Hadley Wickham  
[6] "[The Art of R Programming](http://shop.oreilly.com/product/9781593273842.do)" by Norman Matloff  
[7] "[R for Everyone: Advanced Analytics and Graphics](https://www.goodreads.com/book/show/20306869-r-for-everyone)" by Jared P. Lander

---
output: 
  html_document: 
    keep_md: yes
---
# R programming 101

__Why learning R?__ R is an extremely versatile open source programming language for statistics and data science. It is widely used in every field where there is data—business, industry, government, medicine, academia, and so on.

## Getting Ready

### Install R

The first thing you need to do is to install R on your computer from the [CRAN](https://cran.r-project.org/) site. A step-by-step tutorial on how to install R for Mac and Windows can be found in the following videos

[Installing R on WIndows](https://www.youtube.com/watch?v=Ohnk9hcxf9M&feature=youtu.be)  
[Installing R on Mac](https://www.youtube.com/watch?v=uxuuWXU-7UQ&feature=youtu.be)


### Install RStudio IDE

There is also an integrated development environment available (free) for R that is built by [RStudio](https://www.rstudio.com/products/rstudio/download/). It is a very powerful IDE available for Windows, Mac OS X and Linux. 

A step-by-step tutorial on how to install it can be found in the following video

[Installing RStudio](https://www.youtube.com/watch?v=bM7Sfz-LADM&feature=youtu.be)

A quick overview of the RStudio IDE and how to write R code in it can be found in the following [webinar](https://www.rstudio.com/resources/webinars/rstudio-essentials-webinar-series-part-1/).

### Install `swirl` and relevant interactive course

`swirl` is a package used for teaching R programming and data science interactively using the R console. To install `swirl` on your computer follows the step-by-step guide provided at this [link](http://swirlstats.com/students.html).

Start `swirl` (__Step 4__) and install the relevant interactice course (__Step 5__) with 

```r
library(swirl)
install_course("R Programming")
swirl()
```

More information on how to install swirl interactive courses can be found [here](https://github.com/swirldev/swirl_courses).

Reading Data into R
========================================================
author: Pier Lorenzo Paracchini
date: 20.09.2017
autosize: true
font-import: http://fonts.googleapis.com/css?family=Risque
font-family: 'Risque'


Introduction
========================================================

As with everything in R, there are numerous ways to get data into R

- the `datasets` package,
    - list datasets part of the `datasets` package: `library(help = "datasets")`

- other external packages, use `data()` function
    - list datasets part of the `dplyr` package: `try(data(package = "dplyr"))`
    - list all of the available datasets for all installed packages: `data(package = .packages(all.available = TRUE))`

- reading external files (e.g. csv, tsv, excel, xml, json and more)

In general, when using R with larger datasets, it’s useful to know a few things about your system.

- How much memory is available?
- What other applications are in use?
- Are there other users logged into the same system?
- What operating system?
    - Is the OS 32 or 64 bit?



Reading (tabular data) CSV
========================================================

The `read.table` function is one of the most commonly used function for reading data in R (__memory__) as a `data.frame`. Optionally the `read.csv` function (actually a wrapper around `read.table` with `sep = ","` and others).

<font size = "6px">

```r
file_path <- file.path("data", "TomatoFirst.csv")
# file_path can be an url like
# file_path <- "http://www.jaredlander.com/data/TomatoFirst.csv"

the_ds <- read.table(file = file_path, header = TRUE, sep = ",", stringsAsFactors = FALSE)

format(object.size(the_ds), units = "auto")
[1] "4.6 Kb"

str(the_ds) #str aka structure
'data.frame':	16 obs. of  11 variables:
 $ Round        : int  1 1 1 1 2 2 2 2 3 3 ...
 $ Tomato       : chr  "Simpson SM" "Tuttorosso (blue)" "Tuttorosso (green)" "La Fede SM DOP" ...
 $ Price        : num  3.99 2.99 0.99 3.99 5.49 4.99 3.99 3.99 4.53 NA ...
 $ Source       : chr  "Whole Foods" "Pioneer" "Pioneer" "Shop Rite" ...
 $ Sweet        : num  2.8 3.3 2.8 2.6 3.3 3.2 2.6 2.1 3.4 2.6 ...
 $ Acid         : num  2.8 2.8 2.6 2.8 3.1 2.9 2.8 2.7 3.3 2.9 ...
 $ Color        : num  3.7 3.4 3.3 3 2.9 2.9 3.6 3.1 4.1 3.4 ...
 $ Texture      : num  3.4 3 2.8 2.3 2.8 3.1 3.4 2.4 3.2 3.3 ...
 $ Overall      : num  3.4 2.9 2.9 2.8 3.1 2.9 2.6 2.2 3.7 2.9 ...
 $ Avg.of.Totals: num  16.1 15.3 14.3 13.4 14.4 15.5 14.7 12.6 17.8 15.3 ...
 $ Total.of.Avg : num  16.1 15.3 14.3 13.4 15.2 15.1 14.9 12.5 17.7 15.2 ...
```
</font>

Reading  (tabular data) CSV (Cont'd)
========================================================

__Large files__ can be __slow__ to read into memory using `read.table`, and fortunately there are alternatives available. The __two most prominent functions for reading large CSVs—and other text files__ are

- `read_delim` from the [`readr` package](https://cran.r-project.org/web/packages/readr/README.html) by Hadley Wickham and

- `fread` from the [`data.table` package](https://cran.r-project.org/web/packages/data.table/index.html) by Matt Dowle.

Reading (tabular data) Excel
========================================================

Unfortunately sometimes will be required to read Excel files. Fortunately the [`readxl` package](https://cran.r-project.org/web/packages/readxl/index.html) by Hadley Wickham makes reading excel files (.xls and .xlsx) easy.

`readxl::read_excel()` function is used to load excel files in R (as a `tibble`). It will guess column types, by default, or you can provide them explicitly via the `col_types` argument.

<font size = "6px">

```r
#install.packages("readxl")
library(readxl)

file_path <- file.path("data", "TomatoFirst.xlsx")
the_ds <- read_excel(path = file_path, sheet = 1)

format(object.size(the_ds), units = "auto")
[1] "4.8 Kb"

str(the_ds) #str aka structure
Classes 'tbl_df', 'tbl' and 'data.frame':	16 obs. of  11 variables:
 $ Round        : num  1 1 1 1 2 2 2 2 3 3 ...
 $ Tomato       : chr  "Simpson SM" "Tuttorosso (blue)" "Tuttorosso (green)" "La Fede SM DOP" ...
 $ Price        : num  3.99 2.99 0.99 3.99 5.49 4.99 3.99 3.99 4.53 NA ...
 $ Source       : chr  "Whole Foods" "Pioneer" "Pioneer" "Shop Rite" ...
 $ Sweet        : num  2.8 3.3 2.8 2.6 3.3 3.2 2.6 2.1 3.4 2.6 ...
 $ Acid         : num  2.8 2.8 2.6 2.8 3.1 2.9 2.8 2.7 3.3 2.9 ...
 $ Color        : num  3.7 3.4 3.3 3 2.9 2.9 3.6 3.1 4.1 3.4 ...
 $ Texture      : num  3.4 3 2.8 2.3 2.8 3.1 3.4 2.4 3.2 3.3 ...
 $ Overall      : num  3.4 2.9 2.9 2.8 3.1 2.9 2.6 2.2 3.7 2.9 ...
 $ Avg of Totals: num  16.1 15.3 14.3 13.4 14.4 15.5 14.7 12.6 17.8 15.3 ...
 $ Total of Avg : num  16.1 15.3 14.3 13.4 15.2 15.1 14.9 12.5 17.7 15.2 ...
```
</font>

Reading XML/ HTML files
========================================================

The [`XML` package](https://cran.r-project.org/web/packages/XML/index.html) is a tool for parsing and generating XML files within R (supporting HTML, DTDs). The `xmlTreeParse()` function can be used to parse the XML file directly or from web.

<font size = "6px">

```r
#install.packages("XML")
library(XML)

file_path <- file.path("data", "simple.xml")
# an url can be provided instead
the_ds <- xmlTreeParse(file = file_path)

format(object.size(the_ds), units = "auto")
[1] "63.6 Kb"

rootNode <- xmlRoot(the_ds)

rootNode[[2]]
<food>
 <name>Strawberry Belgian Waffles</name>
 <price>$7.95</price>
 <description>Light Belgian waffles covered with strawberries and whipped cream</description>
 <calories>900</calories>
</food>

rootNode[[2]][[1]]
<name>Strawberry Belgian Waffles</name>
```
</font>

Reading JSON files
========================================================

JSON (JavaScript Object Notation) is a popular format for data from API. JSON is stored in plain text, and well suited for nested data. A R package for reading JSON is the [`jsonlite`](https://cran.r-project.org/web/packages/jsonlite/index.html) package.

>'The jsonlite package is a JSON parser/generator optimized for the web. Its main strength is that it implements a bidirectional mapping between JSON data and the most important R data types. Thereby we can convert between R objects and JSON without loss of type or information, and without the need for any manual data munging. This is ideal for interacting with web APIs, or to build pipelines where data structures seamlessly flow in and out of R using JSON.'

<font size = "6px">

```r
#install.packages("jsonlite")
library(jsonlite)

# mtcars.json
# [{"mpg":21,"cyl":6,"disp":160,"hp":110,"drat":3.9,
#   "wt":2.62,"qsec":16.46,"vs":0,"am":1,"gear":4,
#   "carb":4,"_row":"Mazda RX4"}, ....
mtcars_data <- fromJSON(file.path("data", "mtcars.json"))


head(mtcars_data,7)
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
Duster 360        14.3   8  360 245 3.21 3.570 15.84  0  0    3    4
```
</font>

Reading JSON files (Cont'd)
========================================================

<font size = "4px">
```
# from
#https://feeds.citibikenyc.com/stations/stations.json
{"executionTime":"2017-08-28 04:37:11 AM",
"stationBeanList":[{"id":72,
                    "stationName":"W 52 St & 11 Ave",
                    "availableDocks":30,
                    "totalDocks":39,
                    "latitude":40.76727216,
                    "longitude":-73.99392888,
                    "statusValue":"In Service",
                    "statusKey":1,
                    "availableBikes":9,
                    "stAddress1":"W 52 St & 11 Ave",
                    "stAddress2":"",
                    "city":"",
                    "postalCode":"",
                    "location":"",
                    "altitude":"",
                    "testStation":false,
                    "lastCommunicationTime":"2017-08-28 04:33:21 AM",
                    "landMark":""},
                    .....
```
</font>

---

<font size = "6px">

```r
#install.packages("jsonlite")
library(jsonlite)

jsonData <- fromJSON("http://citibikenyc.com/stations/json")
class(jsonData)
[1] "list"
names(jsonData)
[1] "executionTime"   "stationBeanList"

class(jsonData$stationBeanList)
[1] "data.frame"
head(jsonData$stationBeanList[,1:3])
   id                   stationName availableDocks
1  72              W 52 St & 11 Ave             27
2  79      Franklin St & W Broadway             29
3  82        St James Pl & Pearl St              6
4  83 Atlantic Ave & Fort Greene Pl             34
5 116               W 17 St & 8 Ave             37
6 119      Park Ave & St Edwards St              8
```
</font>

Reading from Other Sources
========================================================

### Databases

Databases arguably store the vast majority of the world’s data. Most of these, whether they be PostgreSQL, MySQL, Microsoft SQL Server or Microsoft Access, can be accessed either through various drivers, typically via an ODBC connection.

The most popular open-source databases have packages such as `RPostgreSQL` and `RMySQL`. Other databases without a specific package can make use of the more generic, and aptly named, `RODBC` package. Database connectivity can be difficult, so the __`DBI`__ package was written to create a uniform experience while working with different databases.

---

### Other statistical tools

Data are sometimes locked in a proprietary format such as those from SAS, SPSS or Octave. The `foreign` package provides a number of functions similar to `read.table` to read in data from other tools.

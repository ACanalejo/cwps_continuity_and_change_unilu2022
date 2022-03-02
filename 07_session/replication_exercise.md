Changing party-systems? Replication exercise on electoral volatility
================
Álvaro Canalejo-Molero
/ March 2022

------------------------------------------------------------------------

First, we have to **set up the basis** of our analysis. The first chunk
of code is opened by default. There, we define *knitr* parameters,
install and load the necessary packages.

``` r
# Setting the compiling options
knitr::opts_chunk$set(echo = TRUE)

# Cleaning the environment
#rm(list = ls())

# Installing packages
#install.packages("kableExtra")
#install.packages("tidyverse")
#install.packages("XML")
#install.packages("readxl")

# Loading packages
library(knitr) # for compiling the document in pdf
library(kableExtra) # for LaTeX based tables
library(tidyverse) # load the tidyverse programming environment
library(XML) # for importing xlsx files from the web
library(readxl) # for importing xlsx files
```

Second, we must **get the data**. We will download it directly from the
internet through R.We start by defining the URL where the data is
hosted.

By default RMarkdown documents set our working directory on the folder
where you have downloaded the .Rmd file. We will get this path and add
the name of the file that contains the data to it. Therefore, you must
substitute the path in *dest* by the path of your working directory and
leave the file name at the end unchanged.

Finally, we download the data.

``` r
# Defining the data URL 
data_url <- "https://cise.luiss.it/cise/wp-content/uploads/downloads/2019/03/Dataset-of-Electoral-Volatility-and-its-internal-components-in-Western-Europe-1945-2015.xlsx"

# Get working directory path
getwd()
```

    ## [1] "C:/Users/acana/Dropbox/Research/GitHub/teaching/cwps_continuity_and_change_unilu2022/07_session"

``` r
# Create the destine file in your working directory
## in my case
dest <- "C:/Users/acana/Dropbox/Research/GitHub/teaching/cwps_continuity_and_change_unilu2022/07_session/volatility_data.xlsx"

# Download the data to the working directory
download.file(data_url, dest, mode="wb")
```

The next step is **opening the data** contained in the .xlsx file.

``` r
# Open the data
volatility_data <- read_excel("C:/Users/acana/Dropbox/Research/GitHub/teaching/cwps_continuity_and_change_unilu2022/07_session/volatility_data.xlsx")
```

Check at the environment tab below. Can you find the volatility_data
object there? Great! That means that we have the data already!

Ok, so the show must go on. **The first thing to do whenever we analyse
a new dataset is taking a first look**. We will use the tidyverse
environment instead of R base packages for most of it.

``` r
# Checking the data structure
glimpse(volatility_data)
```

    ## Rows: 347
    ## Columns: 8
    ## $ Country       <chr> "Austria", "Austria", "Austria", "Austria", "Austria", "~
    ## $ Election_Year <dbl> 1949, 1953, 1956, 1959, 1962, 1966, 1970, 1971, 1975, 19~
    ## $ Election_date <dttm> 1949-10-09, 1953-02-22, 1956-05-13, 1959-05-10, 1962-11~
    ## $ RegV          <dbl> 5.85, 0.00, 0.00, 0.00, 0.00, 1.30, 0.30, 0.00, 0.00, 0.~
    ## $ AltV          <dbl> 6.00, 3.55, 5.45, 2.95, 1.50, 3.20, 6.25, 1.80, 0.45, 1.~
    ## $ OthV          <dbl> 0.35, 0.45, 0.20, 0.05, 0.30, 0.25, 0.05, 0.20, 0.00, 0.~
    ## $ TV            <dbl> 12.20, 4.00, 5.65, 3.00, 1.80, 4.75, 6.60, 2.00, 0.45, 1~
    ## $ ...8          <chr> "Emanuele, V. (2015), Dataset of Electoral Volatility an~

So what do we have here?

Changing party-systems? Wrapping-up workshop on electoral volatility
================
Álvaro Canalejo-Molero
Spring Term 2021-2022

``` r
# Setting the compiling options
knitr::opts_chunk$set(echo = TRUE)

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

-   Getting the data

``` r
# Defining the dta URL 
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

# Open the data
volatility_data <- read_excel("C:/Users/acana/Dropbox/Research/GitHub/teaching/cwps_continuity_and_change_unilu2022/07_session/volatility_data.xlsx")
```

# COURSE 7 : R Programming

# Programming languages and environment covered in this course
* R packages
* R functions, variables, data types, pipes, and vectors
* R data frames
* Bias and credibility in R
* R visualization tools
* R Markdown for documentation, creating structure, and emphasis

# Skill sets learnt  in this course:

Coding in R
* Writing functions in R
* Accessing data in R
* Cleaning data in R
* Generating data visualizations in R
* Reporting on data analysis to stakeholders

# Basic Programming Concepts
To check installed packages

* installed.packages()

List of packages can be seen on the bottom right pane. 

To load the class and list of other uninstalled packages:

* library(class)

# R Sandbox Activity
STEP 1: USING 'R PACKAGES'
To install the `tidyverse` package:

* install.packages("tidyverse")

Load it:
* library(tidyverse)

STEP 2: VIEWING DATA

Dataset named 'diamonds' is already loaded from the package, lets work on it:

To preview the data:

* head(diamonds)

To summarise or preview the data:

* str(diamonds) 
    or 

* glimpse(diamonds)

To get list of column names from the dataset:

* colnames(diamonds)

STEP 3: CLEANING DATA

To rename the columns:

* rename(diamonds, carat_new = carat)

(old name of the column was carat, which is changed to carat_new)

To generate a wide range of summary statistics for the data:

* summarize(diamonds, mean_carat = mean(carat))

STEP 4: CREATE VISUALIZATION

`R` empowers to present the same data in so many different ways, which can help to create new insights or highlight important data findings.

To build a visualization with `ggplot2` you layer plot elements together with a `+` symbol.

* ggplot(data = diamonds, aes(x = carat, y = price)) + geom_point()

To change the color of each point so that it represented another variable:

* ggplot(data = diamonds, aes(x = carat, y = price, color = cut)) + geom_point()

To create a different plot for each type of cut:

* ggplot(data = diamonds, aes(x = carat, y = price, color = cut)) + geom_point() + facet_wrap(~cut)

# 8 core tidyverse packages
* ggplot2: used for data visualizations
* tidyr (R): packaged used for data cleaning to make tidy data
* readr (R): used for importing data
* dplyr (R): offers a consistent set of functions that helps to complete some common data manupulation tasks
* tibble: works for dataframes
* purr: works with functions and vectors helping code make more expressive
* stringr: makes it easier to work with strings
* forcats: helps to solve common problems with vectors

# Factors (R)

Store categorical data in R where the data values are limited and usually based on a finite group like country or a year.

# Pipe (R)

A tool in R expressing a sequence of multiple operations, represented with "%>%".

Nested: 

In pregramming, describes code that performs a particular function and is contained within code that performs a borader function

* Call up data (and then)
* Group the data (and then)
* Summatize the grouped data using a mean function

# Working with a ToothGrowth dataset:
Note: Make sure to code in Script pane so we can save the data
Load the dataset:
 * data("ToothGrowth")
 * View(ToothGrowth)
 * install.packages("dplyr")


  


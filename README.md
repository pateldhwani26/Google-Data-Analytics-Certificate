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

In programming, describes code that performs a particular function and is contained within code that performs a borader function.

* Call up data (and then)
* Group the data (and then)
* Summarize the grouped data using a mean function

# Working with a ToothGrowth dataset:
Note: Make sure to code in Script pane so we can save the data.


Load the dataset:

 * data("ToothGrowth")

View:

 * View(ToothGrowth)

Install the package:

 * install.packages("dplyr")

This function comes as a part of 'dplyr' package:

* library(dplyr)

Assign a name to the new dataset and apply the filter function:

* filtered_tg <- filter(ToothGrowth,dose==0.5)

Filter the data, and show only the data where the dose of Vitamin C is exactly '0.5'
* View(filtered_tg)
  
Sort the data with arrange function:

* arrange(filtered_tg,len)

# Nested Function
A function that is completely contained within another function.

arrange(filter(ToothGrowth,dose==0.5),len)

# Insert a Pipe
filtered_toothgrowth <- ToothGrowth %>% 

 
  filter(dose==0.5) %>%
  
 
  arrange(len)
  

Pipes help programming more efficient and less cluttered, hence fewer chances of mistakes and better readability.

# Group By Function
Lets find a result together with both the vitamins and summarise it.

* filtered_toothgrowth <- ToothGrowth %>%
 

   filter(dose==0.5) %>%
  

   group_by(supp) %>%
  

  summarize(mean_len = mean(len,na.rm = T), .groups = "drop")

# Lets get the average length of tooth when both the doses are '0.5'
* filtered_toothgrowth

Note:
* Add the pipe operator at the end of each line of the piped operation except the last one.
* Check your code after you've programmed your pipe.
* All the lines of the pipes are automatically indented, if the line doesnt get indented itself, probably its not been added to the pipe, which might create error.

# R data frames

A data frame is a collection of columns.


Remember:
* Columns should be named.
* Data stored can be many different types like numeric, factor or character.
* Each column should contain same number of data items.

# Tibbles

In tidyverse, tibbles are like streamlined data frames.

* They never change the data types of the inputs.
* They are easy to use and time savers.
* They never change the names of the variables.
* They never create row names.
* They make printing easier.

# Working with data frames

Let's work with pre-installed Diamonds dataset

* install.packages("tidyverse")
* library(ggplot2)

Load the dataset:

* data("diamonds")

Add the dataframe to our data viewer:

* View(diamonds)

head() to get the first 6 rows, to get the quick preview of the dataset:

* head(diamonds)

To see the structure of the dataset use:

* str()
* colnames()

To make changes to our dataframe:
( mutate() is part of dyplyr package, which is tidyverse, so make sure to load it)


Input mutate and tell R to add column (carat_2) to the diamonds dataframe and multiple column carat with 100
* mutate()

# Tidy Data (R)

A way of standardizing the organization of data within R.

Tidy Data standards:

* Variables are organized into columns.
* Observations are organized into rows.
* Each value must have its own cell.

# Importing .csv file

STEP 1: LOAD THE PACKAGE

* install.packages("tidyverse")
* library(tidyverse)
  
STEP 2: IMPORT THE DATA

Use the read_csv() function to import data from a .csv in the project folder called "hotel_bookings.csv" and save it as a data frame called `bookings_df`:

* bookings_df <- read_csv("hotel_bookings.csv")
  
STEP 3: INSPECT AND CLEAN DATA

Preview the data:

* head(bookings_df)

To check the column names:

* colnames(bookings_df)

To create new variables in your data frame, you can use the `mutate()` function.

* mutate(new_df, total = `adr` / adults)

STEP 4: IMPORT OWN DATA

Using the RStudio Cloud interface, import and save the file in the same folder as this R Markdown document.

* own_df <- read_csv("<filename.csv>")

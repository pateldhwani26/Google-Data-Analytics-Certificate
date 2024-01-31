                                                                        **COURSE 7 : R Programming**
                                                                ---------------------------------------------
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

# R Sandbox Activity
STEP 1: USING 'R PACKAGES'
To install the `tidyverse` package:
-> install.packages("tidyverse")

Load it:
library(tidyverse)

STEP 2: VIEWING DATA
Dataset named 'diamonds' is already loaded from the package, lets work on it:
To preview the data:
-> head(diamonds)

To summarise or preview the data:
-> str(diamonds) 
    or 
-> glimpse(diamonds)

To get list of column names from your dataset:
-> colnames(diamonds)

STEP 3: CLEANING DATA
To rename the columns:
-> rename(diamonds, carat_new = carat)
(old name of the column was carat, which is changed to carat_new)

To generate a wide range of summary statistics for your data:
-> summarize(diamonds, mean_carat = mean(carat))

STEP 4: CREATE VISUALIZATION
`R` empowers to present the same data in so many different ways, which can help to create new insights or highlight important data findings.
To build a visualization with `ggplot2` you layer plot elements together with a `+` symbol.

-> ggplot(data = diamonds, aes(x = carat, y = price)) + geom_point()

To change the color of each point so that it represented another variable:
-> ggplot(data = diamonds, aes(x = carat, y = price, color = cut)) + geom_point()

To create a different plot for each type of cut:
-> ggplot(data = diamonds, aes(x = carat, y = price, color = cut)) + geom_point() + facet_wrap(~cut)


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

* install.packages()

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

# Simplyfy data cleaning tasks using here, skimr, and janitor packages using 'palmerpenguins' dataset:

'here' package makes referencing file easier.
* install.packages("here")
* library("here")
  
'Skimr' package makes summarizing easy and lets data skim through quickly.

* install.packages("skimr")
* library("skimr")

'janitor' package has functions for cleaning data.

* install.packages("janitor")
* library("janitor")

We will need to some some features of 'dplyr' package, hence load it too.

* install.packages("dplyr")
* library("dplyr")

To get the summaries of our dataframe we will use the following functions: 

skim_without_charts() will give us a comprehensive summary about our dataset.

* skim_without_charts(penguins)

glimpse() will provide us a really quick idea about the dataset.

* glimpse(penguins)

head() will provide with quick preview of the data and first few rows of the dataset.

* head(penguins)

select() will allow us to pull the subset of variables from a large dataset. Its useful to specify certain columns, or excludes columns we dont need. 
i.e we only want the species column, lets input penguins use pipes to indicate another command and our select().

* select(species)

If we want everything , but not species column then:

* penguins %>%
      select(-species)

To edit the column names:

* penguins %>%
      rename(island_new=island)

# Organize data using arrange(), group_by(), filter()

Like earlier, we need all the packages loaded to use the dataset.
* install.packages("tidyverse")
* library(tidyverse)

* install.packages("dplyr")
* library("dplyr")

* install.packages("palmerpenguins")
* library("palmerpenguins")

To choose which variable to sort by:
i.e Sorting penguin data by bill length
(by default the result is in ascending order)
* penguins %>% arrange(bill_length_mm)

To arrange it in desc order:
* penguins %>% arrange(- bill_length_mm)

To save this data as dataframe:
First name it:
* penguins2 <- penguins %>% arrange(-bill_length_mm)
* View(penguins2)

Filter data:
* penguins %>% filter(species == "Adelie")
  
# Group_by()

Using group_by statement, excluding NA values, summarize and built the mean statement.
* penguins %>% group_by(island) %>% drop_na() %>% summarize(mean_bill_length_mm= mean(bill_length_mm))

To get penguins with the max bill length:
* penguins %>% group_by(island) %>% drop_na() %>% summarize(max_bill_length_mm= max(bill_length_mm))

Group by both island and specis and summarize both min and max:
* penguins %>% group_by(secies, island) %>% drop_na() %>% summarize(max_bl= max(bill_length_mm), mean_bl=mean(bill_length_mm))

# Transforming data

Install and load packages:

* install.packages("tidyverse")
* library(tidyverse)
* install.packages("dplyr")
* library(dplyr)
* install.packages("skimr")
* library(skimr)
* install.packages("janitor")
* library(janitor)

Create variables:
* id <- c(1:10)
* name <- c("John Mendes", "Rob Stewart", "Rachel Abrahamson", "Christy Hickman", "Johnson Harper", "Candace Miller", "Carlson Landy", "Pansy Jordan", "Darius Berry", "Claudia Garcia")
* job_title <- c("Professional", "Programmer", "Management", "Clerical", "Developer", "Programmer", "Management", "Clerical", "Developer", "Programmer")

Create dataframe:

* employee <- data.frame(id, name, job_title)
* print(employee)

To split the first and last names, lets use the separate(name_of_dataframe, column_name_to_separate, name_to split_the col_into, from_where_to_split_the_column):
* separate(employee, name, into=c('first_name', 'last_name'), sep=' ')

Unite()
first_name <- c("John", "Rob", "Rachel", "Christy", "Johnson", "Candace", "Carlson", "Pansy", "Darius", "Claudia")

last_name <- c("Mendes", "Stewart", "Abrahamson", "Hickman", "Harper", "Miller", "Landy", "Jordan", "Berry", "Garcia")

job_title <- c("Professional", "Programmer", "Management", "Clerical", "Developer", "Programmer", "Management", "Clerical", "Developer", "Programmer")

employee <- data.frame(id, first_name, last_name, job_title)

print(employee)

To do the opposite, combine the columns:
asgts6h
* unite(employee, 'name', first_name, last_name, sep=" ")

(Note: No quotation marks needed here)

# Anscombe's quartet:

# Four datasets that have nearly identical summary statistics.

Firstly, let's install and load packages:

* install.packages('tidyverse')
* library(tidyverse)
* install.packages('dplyr')
* library(dplyr)
* install.packages('Tmisc')
* library(Tmisc)
* data(quartet)
* View(quartet)

Group_by the data by set to get a summary table:

* quartet %>% 
  group_by(set) %>%
  summarise(mean(x),sd(x),mean(y),sd(y),cor(x,y))

Let's put some simple graphs to visualiza this data, as just the statistics can sometimes be misleading.

* ggplot(quartet,aes(x,y)) + geom_point() + geom_smooth(method=lm,se=FALSE) + facet_wrap(~set)

# DatasauRus package creates plots with the Anscombe data in different shapes.

* install.packages('datasaRus')
* library('datasaRus'')

* ggplot(datasaurus_dozen,aes(x=x,y=y,colour=dataset)) + geom_point()+theme(legend.position="none")+facet_wrap(~dataset,ncol=3)

# The bias function

This finds the average amount that the actual outcome is greater than the predicted outcome. It's included in the sim design package.If the outcome is unbiased, the outcome should be pretty close to zero. A high result means the data might be biased.

Let's work with the weather data:

* install.packages("SimDesign")
* library(SimDesign)

* actual_temp <- c(68.3, 70, 72.4, 71, 67)
* predicted_temp <- c (67.9, 69, 71.5, 70, 67)
* bias(actual_temp, predicted_temp)

# Creating Visualizations in R

Important packages for visualizations are:

* ggplot2
* Plotly
* Lattice
* RGL
* Dygraphs
* Leaflet
* Highcharter
* Patchwork
* gganimate
* ggridges

Benefits of ggplot2:

* Create different type of plots i.e: scatter plots, bar charts, line diagrams
* Customize the look and feel of plots i.e: titles, captions and labels
* Create high quality  
* Combine data manipulation and visualization using Pipe operator

Core concepts on ggplots2:

* Aesthetics (R)
  A visual property of an object in the plot
  
* Geoms (R)
  A geometric object used to represent the data
  
* Facets (R)
  Let us display the smaller group, or subsets, of the data
  
* Labels and Annotations (R)
  Let's us customise the plots

# Enhancing Visualizations

# Aesthetic = Color

library(ggplot2)

library(plamerpenguins)

ggplot(data=penguins)+geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species))

# Aesthetic = Size

* ggplot(data=penguins)+geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species,shape=species,size=species))

# Aesthetic = Shape

* ggplot(data=penguins)+geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,color=species,shape=species))

# Aesthetic = Alpha

* ggplot(data=penguins)+geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g,alpha=species))

# Changing color of the whole plot

* ggplot(data=penguins)+geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g),color="purple")

# More with ggplot2

Using Geom Functions with "penguins" dataset:

* geom_point():

  Helps us to make scatter plot.
  
* geom_bar():

  Uses bars to create bar chart.

  Let's create a bar chart using "diamonds" dataset.

  ggplot(data=diamonds)+
  geom_bar(mapping=aes(x=cut))

  Using Aesthetic-color:
  
  * ggplot(data=diamonds)+geom_bar(mapping=aes(x=cut,color=cut))

  But 'color=cut' will only color the border of the bars, to make the bars more noticable with colors, use 'fill'.

  * ggplot(data=diamonds)+geom_bar(mapping=aes(x=cut,fill=cut))

  To understand more combinations of cut and clarity, try the following.

  * ggplot(data=diamonds)+geom_bar(mapping=aes(x=cut,fill=clarity))

* geom_line():

  Uses line to create line chart.
  
* geom_smooth():

  Insted of points it represents visual with smooth line. 

  ggplot(data=penguins)+geom_smooth(mapping=aes(x=flipper_length_mm,y=body_mass_g))

  There are two types of smoothning.

  a) Loes Smoothning:

  Ideal for smoothning plots with less then 1000 points.

  ggplot(data, aes(x= , y= )) + geom_point() + geom_smooth(method="loess")
  
  b) Gam Smoothning or Generalized Additive Model Smoothning:

  Useful with large number of points.

  ggplot(data, aes(x= , y= )) + geom_point() + geom_smooth(method="gam", formula=y~s()x)
  

Combining geom_point & geom_smooth

* ggplot(data=penguins)+
  geom_smooth(mapping=aes(x=flipper_length_mm,y=body_mass_g))+
  geom_point(mapping=aes(x=flipper_length_mm,y=body_mass_g))

If we want separate line for each species:

* ggplot(data=penguins)+geom_smooth(mapping=aes(x=flipper_length_mm,y=body_mass_g,linetype=species))

* geom_gitter():

  ggplot(data=penguins)+geom_jitter(mapping=aes(x=flipper_length_mm,y=body_mass_g,linetype=species))

  It creates a scatter plot and then adds a small amount of random noise to each point in the plot. It helps us deal with overplotting, which happens when points overlap. Jittering makes it easier to find each point.

# Facets (R)

Let's us display smaller groups, or subsets, of the data.

* install.packages("ggplot2")
* install.packages("tidyverse")
* library(tidyverse)
* library(ggplot2)

Facet functions:

* facet_wrap()

  *  ggplot(data=penguins) + geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species)) + facet_wrap(~species)

  Let's use the 'diamonds' dataset to check out each cut category.

  * ggplot(data=diamonds) + geom_bar(mapping=aes(x=color,fill=cut))+ facet_wrap(~cut)

* facet_grid()

  This function will split the plot into facets vertically by the values of first variable and horizonltally by the values of second variable.
  
   * ggplot(data=penguins) + geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))+ facet_grid(sex~species)

     or
     
   * gplot(data=penguins) + geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))+ facet_grid(~sex)

# Annotate

To add notes to a document or diagram to explain or comment upon it.

 * Titles

   ggplot(data=penguins) +geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))+
   labs(title="Palmer Penguins: Body Mass vs. Flipper Length")

 * Subtitles

   ggplot(data=penguins) +geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))
   +labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle="Sample of three Penguin Species")

 * Captions

   ggplot(data=penguins) + geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))+
   labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle="Sample of three Penguin Species",
   caption="Data collected by Dr. Kristen Gorman")

 
 Annotation Function:

 To write a text label and place it at the specific location of the plot.

 
* ggplot(data=penguins) + 
  geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))+
  labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle="Sample of three Penguin Species",
  caption="Data collected by Dr. Kristen Gorman") +
  annotate("text", x=220,y=3500,label="The Gentos are the largest", color="purple",fontface="bold", size=4.5,angle=25)

To avoid rewriting the long code, we can assign a variable and and annotation to it.

Assign the variable:

* p <- ggplot(data=penguins) + 
  geom_point(mapping=aes(x=flipper_length_mm, y=body_mass_g, color=species))+
  labs(title="Palmer Penguins: Body Mass vs. Flipper Length", subtitle="Sample of three Penguin Species",
  caption="Data collected by Dr. Kristen Gorman")
      
Add the annotation:

* p+annotate("text", x=220,y=3500,label="The Gentos are the largest", color="purple",fontface="bold", size=4.5,angle=25)

# To share and reproduce the work with the team mates:

* Export option

  * Plots
  * export
  * save as image
  * file name

* ggsave() function

  ggsave("Three Penguin Species.png")

# Additional resources:
* https://www.rdocumentation.org/packages/SimDesign/versions/2.2/topics/bias
* https://datasciencebox.org/02-ethics.html
* https://ggplot2.tidyverse.org/
* https://www.rdocumentation.org/packages/ggplot2/versions/3.3.3/topics/aes
* https://datacarpentry.org/dc_zurich/R-ecology/05-visualisation-ggplot2.html
* https://rladiessydney.org/courses/ryouwithme/03-vizwhiz-1/#1-4-putting-it-all-together-dplyr-ggplot
* https://r4ds.had.co.nz/transform.html
* https://www.r-bloggers.com/2017/02/how-to-annotate-a-plot-in-ggplot2/
* https://r-graph-gallery.com/233-add-annotations-on-ggplot2-chart.html
* https://ggplot2-book.org/annotations.html
* https://ggplot2.tidyverse.org/reference/annotate.html
* https://www.datanovia.com/en/blog/how-to-save-a-ggplot/
* https://www.datamentor.io/r-programming/saving-plot
* https://ggplot2.tidyverse.org/reference/ggsave.html#saving-images-without-ggsave-
  


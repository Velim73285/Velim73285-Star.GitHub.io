---
layout: post
title: Numerical Analysis
subtitle: Each post has a subtitle
categories: Modules
tags: [Github, Modules, Python, R]
---

## 1. A summary of the learning outcomes of the module
•	Develop a systematic understanding of foundational mathematical principles and methods, as well as core and specialised concepts underpinning computing logic in Data Science and AI.

•	Understand the foundation for the development and application of programming and data-driven techniques using R, from both a theoretical and practical viewpoint.

•	Facilitate the ability to interpret the results generated when using these data science and AI tools.

•	Gain an understanding of the real-world applications of these computational tools, and contemporary issues related to these computational techniques.

•	The opportunity to take a reflective and independent approach to the learning process.

## 2.	The artefacts created during the module
### 2.1 Unit 1
This unit explored the importance of statistics, which are found everywhere in business, in sports, in health, in law, and other sectors. Statistics are often included in reports to add credibility, but sometimes the numbers could be presented in such a way that they are misleading. The unit focused on knowing about different interfaces and packages used in R, importing and saving data in R, explaining the importance of statistics to business, exploring how data can be summarised in different formats, understanding different types of measurement scales, determining levels of measurement, and performing descriptive statistics analysis using R.

### Data activity 1
Dataset: COVID-19 India Cases (January 2020 - March 2020)Source: This dataset contains early COVID-19 case data from India covering the initial months of the pandemic from January to March 2020. The data includes confirmed cases (both Indian and foreign nationals), recovered cases, and deaths across different states and union territories of India.

### Instructions
1.	Download and save the Covid19 India Jan 20 Mar 20.csv.xls file to your R working directory
   
2.	Load the dataset into RStudio using appropriate functions for Excel file
   
3.	Conduct an initial exploration of the dataset structure

### Task 2.1.1: Basic dataset information
### R code to answer the questions below

#### Upload dataset called Covid19_India_Jan20_Mar20.csv in R
  Covid19_India_Jan20_Mar20 <- read.csv("Covid19_India_Jan20_Mar20.csv")

#### List the variables in a dataset
names(Covid19_India_Jan20_Mar20)

#### Getting the number of observations in a dataset
nrow(Covid19_India_Jan20_Mar20)

#### To check the variables format in a dataset
str(Covid19_India_Jan20_Mar20)

#### To check how many unique states/union territories are represented in the dataset
length(unique(Covid19_India_Jan20_Mar20$State.UnionTerritory))

unique(Covid19_India_Jan20_Mar20$State.UnionTerritory)

#### Convert factor Date variable to a date format variable in the dataset
Covid19_India_Jan20_Mar20$Date <- as.Date( as.character(Covid19_India_Jan20_Mar20$Date),

  format = "%d-%m-%Y"   # or "%Y-%m-%d" 
  
)

#### To check date range covered by this dataset
range(Covid19_India_Jan20_Mar20$Date)

#### To check which state appears most frequently in the dataset using frequency table
table(Covid19_India_Jan20_Mar20$State.UnionTerritory)

#### Find the state with the maximum frequency
which.max(table(Covid19_India_Jan20_Mar20$State.UnionTerritory))

### Using R commands, determine and record the following
•	How many total variables (columns) are in this dataset?

There are 7 variables

•	How many total observations (rows) are in this dataset

There are 270 observations

•	What are the names of all variables in the dataset?

The names of the variables in the dataset are: Sno, Date, State.UnionTerritory, ConfirmedIndianNationa, ConfirmedForeignNational, Cured, and Deaths.

•	How many variables are in numeric format?

There are 5 variables that are numeric (Sno, ConfirmedIndianNationa, ConfirmedForeignNational, Cured, and Deaths.

•	How many variables are in character/text format?

There are 2 variables that are character (Date, State.UnionTerritory)

•	How many variables are in date format?

There are 0 variables that are date format because the date variable in the dataset is classified as factor in R.

### Task 2.1.2 Data related information	
•	How many unique states/union territories are represented in the dataset?

There are 27 unique states/union territories in the dataset

•	What is the date range covered by this dataset?

The date range is 2020-01-30 to 2020-03-21

•	Which state appears most frequently in the dataset?

The state that appears most frequently in the dataset is Kerala with 52 observations

### Unit 2: Data activity 2
Using the COVID-19 India Dataset (January 2020 - March 2020), perform the following frequency analysis activities to understand patterns in early pandemic reporting across Indian states. 

### 2.1	Questions and answers
1.	Create a frequency table to count how many daily reports showed recoveries versus no recoveries during this period. Use the table() command. 

#### Load the dataset into R
> Covid19_India_Jan20_Mar20 <- read.csv("Covid19_India_Jan20_Mar20.csv")

> View(Covid19_India_Jan20_Mar20)

#### Create a frequency table: TRUE if recoveries > 0, FALSE otherwise
> freq_table <- table(Covid19_India_Jan20_Mar20$Cured > 0)

> cat("\n\nFrequency of Daily Reports (Recoveries vs No Recoveries):\n")
 
print(freq_table)

 <img width="756" height="74" alt="image" src="https://github.com/user-attachments/assets/adec6296-b3c3-40cc-8e8e-1781bfde2201" />

2.	Calculate percentages to understand what proportion of daily state reports included recovery cases. 
#### Convert to proportions (percentages) 
> percent_table <- prop.table(freq_table) * 100

> cat("\n\nPercentage of Daily Reports (Recoveries vs No Recoveries):\n")

print(percent_table)

<img width="770" height="70" alt="image" src="https://github.com/user-attachments/assets/1b3b1616-c81f-4937-870e-65ba35e49735" />

3.	Create a binary variable called has_recovery that indicates whether any recoveries (cured cases) were reported. 
#### Creating a variable has_recovery from a variables cured
>  Covid19_India_Jan20_Mar20$has_recovery <- Covid19_India_Jan20_Mar20$Cured > 0

#### Convert logical TRUE/FALSE into a binary of 1/0
> Covid19_India_Jan20_Mar20$has_recoverybinary <- as.integer(Covid19_India_Jan20_Mar20$Cured > 0)

Table output for the binary variable called has_recovery

<img width="940" height="570" alt="image" src="https://github.com/user-attachments/assets/29488a9d-34fd-45e3-8b5b-e5460069fd3b" />

Notes: (0 = No recoveries reported and 1 = Recoveries reported)

#### 2.2.2	Seminar 2 on 10 February 2026
#### 2.2.2.1 An article by Dong, Y. (2023)
Using the article by Dong, Y. (2023) ‘Descriptive statistics and its applications’, Highlights in Science, Engineering and Technology, 47, pp. 16–23 to answer the following questions.





## 3.	What exactly have I learnt and how?
To be completed

### 3.1 What have I learnt from this module?
To be completed

### 3.2 The how part of learning the above
To be completed

## 4.	Professional skills gained and enhanced as a result of the module 
To be completed


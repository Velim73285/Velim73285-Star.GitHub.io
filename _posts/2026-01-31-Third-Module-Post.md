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

### 2.2.2	Seminar 2 on 10 February 2026
### 2.2.2.1 An article by Dong, Y. (2023)
Using the article by Dong, Y. (2023) ‘Descriptive statistics and its applications’, Highlights in Science, Engineering and Technology, 47, pp. 16–23 to answer the following questions.

a)	What is the primary purpose of descriptive statistics, and how does it differ from other statistical methods?

The primary purpose of descriptive statistics is to provide a clear, concise summary of a dataset’s main features. Instead of working with raw numbers, descriptive statistics organise and present data using measures like mean, median, mode, standard deviation, frequency tables, and graphs. This makes complex datasets easier to understand and communicate to others. Descriptive statistics focuses only on describing and summarising the data at hand and does not attempt to generalise beyond the dataset or make any predictions. It uses sample data to make inferences about a larger population, and it also involves hypothesis testing, confidence intervals, and regression analysis.

b)	According to the paper's analysis of housing prices in Beijing (Table 2), what were the key factors that contributed to the increase in housing prices between 2012 and 2015? Explain how the descriptive statistics helped identify these factors.

In the paper’s analysis of housing prices in Beijing (Table 2), the descriptive statistics highlighted the following factors that contributed to the increase in housing prices between 2012 and 2015:

• Average Price Increase: The mean housing price rose from 336.727 in 2012 to 477.521 in 2015, showing a significant upward trend.

• Living Space Growth: The average area of homes increased from 102.523  to 123.94, indicating larger housing units were being built and sold.

• More bedrooms and dining rooms: The mean number of bedrooms rose from 2.126 to 2.415, and dining rooms from 1.34 to 1.559, suggesting improved housing quality and facilities.

• Taller buildings: The average floor number increased from 14.099 to 15.342, reflecting a trend toward high-rise construction, which correlated with rising prices.

Descriptive statistics provided a straightforward way to identify which variables were changing significantly and how those changes aligned with the observed increase in housing prices.

c)	Explain the difference between mean, median, and mode. Given the sample: 13, 15, 17, 15, 20, 15, 18, calculate all three measures of central tendency.

#### Difference between Mean, Median, and Mode
1.	Mean: The arithmetic average and is calculated by adding all values together and divide by the number of observations.
   
2.	Median: The middle value when the data is ordered either in an ascending order or descending order. If there’s an even number of values, the median is the average of the two middle ones.
   
3.	Mode: The value that occurs most frequently in the dataset.
Sample data is: 13,15,17,15,20,15,18

#### Calculations
1.	Mean = 16.14
   
2.	Median = 15 when the data ordered in an ascending order: 13,15,15,15,17,18,20
   
3.	Mode = 15  since the value 15 appears 3 times.

d)	What are the main limitations of descriptive statistics as identified in the paper? Why is descriptive statistics alone not sufficient for comprehensive statistical analysis?

In the paper, the author highlights several limitations of descriptive statistics and explains why they are not sufficient on their own for comprehensive statistical analysis:

•	No predictive power: Descriptive statistics can only summarise existing data; they cannot forecast future values or trends. For example, they can show that housing prices rose between 2012 and 2015, but they cannot predict what will happen in 2016.

•	Restricted scope: They provide a snapshot of the dataset but cannot establish causal relationships or deeper insights. For instance, descriptive measures can show averages and variability but not explain why those changes occurred.

•	Time consuming data collection: The paper notes that gathering raw data for descriptive statistics can be lengthy and complex, especially when multiple sources are involved.

•	Insufficient for comprehensive analysis: A single descriptive table is never enough to fully understand a dataset. Researchers often need to move beyond descriptive summaries to inferential methods (like regression models) to draw broader conclusions.

e)	Based on Table 3 and Table 4 in the stock market analysis section, explain how descriptive statistics (particularly mean values) helped researchers determine the relationship between trust levels and stock market volatility during COVID-19.

#### Insights from table 3
•	Table 3 presents descriptive statistics for variables such as market volatility, case growth rate, and trust (both societal and governmental). For example, the mean trust score was 31.09 for societal trust and 39.31 for government trust. These averages provided a baseline understanding of how trust levels varied across countries during the pandemic.

#### Insights from table 4
•	Table 4 compares countries with high trust versus low trust. The mean market volatility was 0.0179 in high-trust countries and 0.0176 in low-trust countries, showing only a small difference. However, the mean case growth rate was 0.0420 in high-trust countries versus 0.0674 in low-trust countries. This difference suggested that countries with higher trust experienced lower growth in COVID-19 cases, which in turn correlated with lower volatility in their stock markets.

Descriptive statistics helped where the mean values acted as a tool to highlight differences between high-trust and low-trust countries, showing that higher trust was associated with lower case growth and steadier markets during COVID-19.

### 2.2.2.2 Data analysis activity
Using this small covid-19 dataset, perform the following activities:

a.	Calculate and interpret measures of central tendency and dispersion for COVID-19 cases across Indian states during January-March 2020.

#### R code to calculate the measures of measures of central tendency and dispersion

#### Read the dataset
covid_data <- read.csv("Covid19_India_Jan20-Mar20.csv")

#### Extract Confirmed Indian National cases
confirmed_cases <- covid_data$ConfirmedIndianNational

#### Measures of central tendency
mean_cases <- mean(confirmed_cases, na.rm = TRUE)

median_cases <- median(confirmed_cases, na.rm = TRUE)

mode_cases <- as.numeric(names(sort(table(confirmed_cases), decreasing = TRUE)[1]))

#### Measures of dispersion
range_cases <- range(confirmed_cases, na.rm = TRUE)

variance_cases <- var(confirmed_cases, na.rm = TRUE)

sd_cases <- sd(confirmed_cases, na.rm = TRUE)

#### Print results
cat("Mean:", mean_cases, "\n")

cat("Median:", median_cases, "\n")

cat("Mode:", mode_cases, "\n")

cat("Range:", range_cases[1], "to", range_cases[2], "\n")

cat("Variance:", variance_cases, "\n")

cat("Standard Deviation:", sd_cases, "\n")

#### Measures of central tendency
a)	Mean =  5.6 cases

On average, each state entry reported about 6 confirmed cases. This is inflated by hotspots like Maharashtra and Kerala states.

b)	Median = 3 cases

Half of the entries reported 3 or fewer cases. This reflects the long level in Kerala and isolated detections elsewhere.

c)	Mode = 1 cases 

The most common value was 1 across all the states.

#### Measures of dispersion
a)	Variance = 69.5

High variance due to clustering since most states had very few cases, but Kerala, Maharashtra, and Delhi had much higher counts.

b)	Standard Deviation = 8.3

Standard deviation is higher relative to the mean, indicating uneven spread of the cases across the states.

c)	Range = 60 

The maximum = 60 in which is in Maharashtra and the minimum = 0 in several states. This shows the wide disparity between hotspots and states with no or minimal cases.

b.	Create appropriate visualizations:

#### Histograms with density curves for each variable
#### R code to create histograms with density curves
#### Read the dataset
covid_data <- read.csv("Covid19_India_Jan20-Mar20.csv")

#### Identify numeric columns
numeric_vars <- c("ConfirmedIndianNational", "ConfirmedForeignNational", "Cured", "Deaths")

####  Loop through each numeric variable and plot histogram with density curve
for (var in numeric_vars) {

  ####  Extract data
    data <- covid_data[[var]]
  
  ####  Open PNG device (optional: saves plots as files)
  png(paste0("hist_density_", var, ".png"))
  
  ####  Create the histogram
  hist(data,
  
       main = paste("Histogram with Density Curve for", var),
       
       xlab = var,
       
       col = "lightblue",
       
       breaks = 20,
       
       probability = TRUE)  # scale to probability for density
  
  ####  Add density curve
  lines(density(data, na.rm = TRUE), col = "red", lwd = 2)
  
  ####  Close PNG device
  
  dev.off()
  
}

<img width="750" height="593" alt="image" src="https://github.com/user-attachments/assets/ebf66b14-f582-4a0f-9d3c-3f214a947ba6" />

<img width="750" height="690" alt="image" src="https://github.com/user-attachments/assets/8d30f5b2-5b4a-4f0c-b53e-b9277b1dd2c7" />

<img width="796" height="696" alt="image" src="https://github.com/user-attachments/assets/e74988e5-9ac7-4f12-8c71-135c1ad8b8f8" />

<img width="851" height="693" alt="image" src="https://github.com/user-attachments/assets/afa3a294-b6a9-48f0-96f0-4d6e7bfaa3ff" />

#### Boxplots to identify outliers
#### R code to create boxplots
#### Read the dataset
covid_data <- read.csv("Covid19_India_Jan20-Mar20.csv")

#### Numeric variables to visualize
numeric_vars <- c("ConfirmedIndianNational", "ConfirmedForeignNational", "Cured", "Deaths")

#### Save all boxplots in one PNG file
png("covid_boxplots.png", width = 1000, height = 800)

#### Arrange plots in 2x2 grid
par(mfrow = c(2, 2))

#### Loop through variables
for (var in numeric_vars) 

  data <- covid_data[[var]]
  
  #### Create boxplot
  boxplot(data,
  
          main = paste("Boxplot of", var),
          
          ylab = var,
          
          col = "lightgreen")
  
  #### Add grid for readability
  grid()
  
}

#### Close PNG device
dev.off()

<img width="991" height="750" alt="image" src="https://github.com/user-attachments/assets/7be46d47-bd2a-49f9-96b5-80391ca62a5f" />

#### Violin plots to show distribution shape
#### R code to create violin plots
#### Install vioplot if not already installed
if(!require(vioplot)) install.packages("vioplot")

library(vioplot)

#### Read the dataset
covid_data <- read.csv("Covid19_India_Jan20-Mar20.csv")

#### Numeric variables
numeric_vars <- c("ConfirmedIndianNational", "ConfirmedForeignNational", "Cured", "Deaths")

#### Save violin plots in one PNG file
png("covid_violinplots.png", width = 1000, height = 800)

#### Arrange plots in 2x2 grid
par(mfrow = c(2, 2))

#### Loop through variables
for (var in numeric_vars) {

  data <- covid_data[[var]]
  
  #### Create violin plot
  vioplot(data,
  
          names = var,
          
          col = "lightblue",
          
          main = paste("Violin Plot of", var))
          
    grid()
    
}

dev.off()

<img width="940" height="880" alt="image" src="https://github.com/user-attachments/assets/430e6b6d-75be-4ff6-b19b-52e50aae1aef" />

a)	ConfirmedIndianNational plot is strong right skew, with most values clustered at low counts but a long tail up to 60.

b)	ConfirmedForeignNational plot is mostly zeros, with isolated spikes from Rajasthan and Haryana.

c)	Cured plot is sparse distribution, concentrated at 0 with occasional clusters.

d)	Deaths plot is almost entirely 0, with rare non-zero values showing as thin tails.

### 2.3	Unit 3: Data Management in R
#### 2.3.1 Data analysis and results
Using the COVID-19 India Dataset (January 2020 - March 2020), perform the following activities.

1. Create a binary variable called has_deaths that indicates whether any deaths were reported:  

•	Value = 1 (or TRUE) if Deaths > 0

•	Value = 0 (or FALSE) if Deaths = 0 

#### Load the dataset
covid_data <- read.csv("Covid19_India_Jan20_Mar20.csv", header = TRUE)

#### Create the binary variable
covid_data$has_deaths <- ifelse(covid_data$Deaths > 0, 1, 0)

#### Inspect the first few rows
head(covid_data[, c("Deaths", "has_deaths")])

#### Opens spreadsheet in a viewer style in RStudio 
View(covid_data)

#### Table showing the new binary variable called has_deaths

<img width="940" height="609" alt="image" src="https://github.com/user-attachments/assets/02f84528-616c-41e0-a01b-68854a72baca" />

2. Create a frequency table using the table() command to analyse death reporting patterns.

#### Load the dataset
covid_data <- read.csv("Covid19_India_Jan20_Mar20.csv", header = TRUE)

#### Create the binary variable
covid_data$has_deaths <- ifelse(covid_data$Deaths > 0, 1, 0)

#### Frequency table of death reporting
table(covid_data$has_deaths)

#### Table showing death reporting patterns
<img width="402" height="70" alt="image" src="https://github.com/user-attachments/assets/e146289f-a544-4cce-8225-294fcc6d04fc" />

3. Convert to a factor variable with appropriate labels ("No Deaths", "Deaths Reported").
   
#### Load the dataset
covid_data <- read.csv("Covid19_India_Jan20_Mar20.csv", header = TRUE)

#### Create the binary variable
covid_data$has_deaths <- ifelse(covid_data$Deaths > 0, 1, 0)

#### Convert to factor with labels
covid_data$has_deaths <- factor(

  covid_data$has_deaths,
  
  levels = c(0, 1),
  
  labels = c("No Deaths", "Deaths Reported")
  
)

#### Inspect the result
table(covid_data$has_deaths)

head(covid_data[, c("Deaths", "has_deaths")])

#### Spreadsheet-style viewer (RStudio only) 
View(covid_data)

#### Table showing factor variable with levels ("No Deaths", "Deaths Reported"). 
<img width="940" height="565" alt="image" src="https://github.com/user-attachments/assets/81a53aaa-72e9-4d3a-a647-4a7f64688ae3" />

4. Create a categorical variable called case_level based on total confirmed cases (Indian + Foreign nationals):  
•	No Cases = 0 cases

•	Low Cases = 1-5 cases 

•	Medium Cases = 6-15 cases

•	High Cases = 16+ cases 

#### Load the dataset
covid_data <- read.csv("Covid19_India_Jan20_Mar20.csv", header = TRUE)

#### Create a total confirmed cases variable
covid_data$total_confirmed <- covid_data$ConfirmedIndianNational + covid_data$ConfirmedForeignNational

#### Create the categorical variable case_level
covid_data$case_level <- cut(

  covid_data$total_confirmed,
  
  breaks = c(-Inf, 0, 5, 15, Inf),
  
  labels = c("No Cases", "Low Cases", "Medium Cases", "High Cases")
  
)

#### Inspect the result
head(covid_data[, c("ConfirmedIndianNational", "ConfirmedForeignNational", "total_confirmed", "case_level")])

table(covid_data$case_level)

#### Table showing categorised case levels 
<img width="853" height="78" alt="image" src="https://github.com/user-attachments/assets/8569b725-1f66-4405-9fd4-5c238186a2be" />

5. Create a frequency table for the State/Union Territory variable to see which states had the most frequent reporting.

#### Load the dataset
covid_data <- read.csv("Covid19_India_Jan20_Mar20.csv", header = TRUE)

#### Frequency table for State/UnionTerritory
state_freq <- table(covid_data$State.UnionTerritory)

#### View the results
state_freq

#### Sort the table in descending order to see the most frequent states first
sort(state_freq, decreasing = TRUE)

#### Convert frequency table to dataset format 
state_freq_df <- as.data.frame(state_freq) 

#### View the dataset 
head(state_freq_df) 

     View(state_freq_df)

#### Table showing frequencies per state 
<img width="928" height="621" alt="image" src="https://github.com/user-attachments/assets/e054e828-eff7-423c-848d-ef6150a714b7" />

6. Identify the top 10 states with the highest number of daily reports in the dataset.

####  Load the dataset
covid_data <- read.csv("Covid19_India_Jan20_Mar20.csv", header = TRUE)

####  Create frequency table for State/UnionTerritory
state_freq <- table(covid_data$State.UnionTerritory)

####  Convert to dataset format
state_freq_df <- as.data.frame(state_freq)

####  Sort by frequency in descending order
state_freq_sorted <- state_freq_df[order(-state_freq_df$Freq), ]

####  Select top 10 states
top10_states <- head(state_freq_sorted, 10)

####  View the result
top10_states

#### Table with states with the top 10 highest number of daily reports
<img width="549" height="281" alt="image" src="https://github.com/user-attachments/assets/a3af7559-a4b1-4b77-b114-f3fefbd72fd5" />

### 2.4	Unit 5: Producing plots and introducing calculus
#### 2.4.1 Plotting activities to learn basic data visualization techniques  
1.	Create a bar chart showing the frequency of COVID-19 reports by state/union territory. 

#### R code to create the bar chart
####  Load the dataset
covid_data <- read.csv("Covid19_NewIndia_(Jan20 - Mar20).csv")
####  Create a frequency table of reports by State/Union Territory
state_counts <- table(covid_data$State.UnionTerritory)
####  Plot a bar chart
barplot(state_counts,

        main = "Frequency of COVID-19 Reports by State/Union Territory",
        
        xlab = "State/Union Territory",
        
        ylab = "Number of Reports",
        
        las = 2,            # Rotate axis labels for readability
        
        col = "steelblue")  # Add some color

        
<img width="876" height="706" alt="image" src="https://github.com/user-attachments/assets/ec3ca131-9ec7-4f4a-8dc6-d14d154c7e70" />

2.	Using variables ConfirmedIndianNational and ConfirmedForeignNational, create a pie chart showing the distribution of case severity levels based on total confirmed cases.

#### R code to create the pie chart
#### Load the dataset
covid_data <- read.csv("Covid19_NewIndia_(Jan20 - Mar20).csv")
#### Calculate total confirmed cases by nationality
total_indian <- sum(covid_data$ConfirmedIndianNational, na.rm = TRUE)

total_foreign <- sum(covid_data$ConfirmedForeignNational, na.rm = TRUE)
#### Create a vector of totals
cases <- c(total_indian, total_foreign)
#### Define labels
labels <- c("Indian Nationals", "Foreign Nationals")
#### Create pie chart
pie(cases,

    labels = paste(labels, cases),
    
    main = "Distribution of Confirmed COVID-19 Cases by Nationality",
    
    col = c("skyblue", "orange"))

<img width="847" height="593" alt="image" src="https://github.com/user-attachments/assets/1b26817a-76ac-4461-8ac3-d3036412b4fe" />

3.	Create a histogram showing the distribution of recovery numbers. 

#### R code to create a histogram 
#### Load the dataset
covid_data <- read.csv("Covid19_NewIndia_(Jan20 - Mar20).csv")
#### Create histogram of recovery numbers
hist(covid_data$Cured,

     main = "Distribution of COVID-19 Recoveries",
     
     xlab = "Number of Recoveries",
     
     ylab = "Frequency",
     
     col = "lightgreen",
     
     border = "black")

<img width="873" height="626" alt="image" src="https://github.com/user-attachments/assets/b38729f2-dc09-4abc-86a7-19a6d69da39f" />

4.	Create a line chart showing the trend of total cases over time.

#### R code to create a histogram 

#### Load the dataset
covid_data <- read.csv("Covid19_NewIndia_(Jan20 - Mar20).csv")
#### Convert Date column to proper Date format
covid_data$Date <- as.Date(covid_data$Date, format = "%d-%m-%Y")
#### Calculate total confirmed cases (Indian + Foreign)
covid_data$TotalConfirmed <- covid_data$ConfirmedIndianNational + covid_data$ConfirmedForeignNational
#### Aggregate totals by date
daily_totals <- aggregate(TotalConfirmed ~ Date, data = covid_data, sum)
#### Create line chart
plot(daily_totals$Date, daily_totals$TotalConfirmed,

     type = "l",                # Line chart
     
     col = "blue",              # Line color
     
     lwd = 2,                   # Line width
     
     main = "Trend of Total COVID-19 Cases Over Time",
     
     xlab = "Date",
     
     ylab = "Total Confirmed Cases")

#### Add points for clarity
points(daily_totals$Date, daily_totals$TotalConfirmed, col = "red", pch = 16)

<img width="838" height="655" alt="image" src="https://github.com/user-attachments/assets/840f863b-3156-49a2-bb53-95d76d01ff88" />

### 2.4.2 Collaborative discussion
#### Discussion Topic
Imagine you have submitted a paper for publication (see Brown, 1994 in this week’s reading list). The editor has returned his comments saying that he is willing to accept the paper for publication on condition that Table 2 (see Brown, 1994) is changed. He feels that ‘it is difficult for the reader to understand, contains too much information and is too large.’ You now have to redo the table 2 and present some of the findings using plots and present your results in the forum. Reflect also upon your experiences of undertaking this task and what you have learnt. Share these reflections with your fellow students (no more than 500 words).

#### Initial Post
Divecha et al., 2023 argue that reading text matter can often get monotonous for the readers as well as the editors and reviewers. Using tables/charts or graphs effectively provides a break from textual content monotony as an opportunity to process and connect information between text and images. Based on this argument it is evident that graphs, charts, and tables can save readers’ time and energy, aid their understanding of an article, and reduce the word count of the main text. However, many graphics submitted and published in scientific journals fail to meet their potential and include mistakes that risk their clarity. 

To meet the editor’s request, I restructured table 2 by grouping the 24 statements into themes and presenting the most striking findings with plots rather than a dense table. For example, discouraging factors such as workload (83% agreement), disruption of personal life (75%), and fear of litigation (69%) can be shown in a bar chart, immediately highlighting the strongest barriers to intrapartum care. Likewise, philosophical views such as support for community-based maternity care (71%) and enabling GPs to provide care throughout pregnancy and labour (92%) can be visualised in a pie chart or stacked bar chart, making the consensus clear at a glance. Undertaking this task taught me the importance of clarity and focus in data presentation. While the original table was comprehensive, it overwhelmed the reader with detail. By condensing the information into thematic categories and using visualisations, the key messages became far more accessible. I learned that effective communication in research is not just about completeness but about highlighting patterns and insights in ways that readers can quickly grasp. This exercise reinforced the value of graphical representation in conveying consensus and disagreement, and it reminded me that editorial feedback often pushes us toward more impactful storytelling with data. 

<img width="804" height="352" alt="image" src="https://github.com/user-attachments/assets/7fbc56d8-c9ba-408f-99eb-34931eb244f1" />

<img width="979" height="736" alt="image" src="https://github.com/user-attachments/assets/d6a17a94-fdc2-4302-9f43-9f3ababb7cf7" />

In conclusion, condensing table 2 and presenting the findings with plots made the results far clearer and easier to interpret. Instead of overwhelming readers with 24 detailed statements, grouping them into themes and visualising the strongest patterns highlighted the key issues from the table. This task taught me that effective research communication requires balancing completeness with readability, and that visualisation is a powerful way to emphasise consensus and disagreement. Finally, simplifying the table and using plots improved clarity, impact, and accessibility of the findings.

#### References
Divecha, C.A., Tullu, M.S. and Karande, S., 2023. Utilizing tables, figures, charts and graphs to enhance the readability of a research paper. Journal of postgraduate medicine, 69(3), pp.125-131. 

Hogan, A., Blomqvist, E., Cochez, M., d’Amato, C., Melo, G.D., Gutierrez, C., Kirrane, 
S., Gayo, J.E.L., Navigli, R., Neumaier, S. and Ngomo, A.C.N., 2021. Knowledge graphs. ACM Computing Surveys (Csur), 54(4), pp.1-37. 

Kabacoff, R., 2022. R in action: data analysis and graphics with R and Tidyverse. Simon and Schuster. 

Siedlecki, S.L., 2023. Tables, Figures, and Graphs: How to Best Display Data. Clinical Nurse Specialist, 37(4), pp.160-163.

Wong, D.M., 2023. The Wall Street Journal guide to information graphics: The dos and don'ts of presenting data, facts, and figures. WW Norton & Company.

#### Peer Response to Paul Sanderson
Thank you Paul for producing a detailed post that walks the reader through the process step by step,  from preparing the data in Google Sheets, exporting to CSV, and importing into RStudio, to filtering and plotting. This transparency makes the post educational and informative.

Wong, D.M., 2023 makes a case that “We live in a data driven world where the ability to create effective charts and graphs has become almost as indispensable as good writing.” This statement is true because with computer technology, anyone can create graphics, but a few know how to do it well and right. Most of the time we present a chart with visual tricks such as clashing colours thinking it will look pretty while not paying enough attention to passing the correct message to the reader.

The inclusion of the exact formulas in the post used in Sheets and the R code snippets adds credibility and helps others replicate the process and you did not stop at the first plots, but you continued by refining labels, wrapping text, and adding values, which shows thoughtful engagement with data visualisation best practices. You explicitly tied the visualisation back to its purpose and supported decision-makers identify areas of improvement which grounds the technical work in real-world impact.

In summary, your post demonstrates strong technical competence and a clear workflow, making it a solid piece for peers learning R and ggplot2. To elevate it further, you should generate in more narrative context and expand on the meaning of the results. This would transform the post from a technical walkthrough into a more impactful, stakeholder-ready analysis.

#### References
Divecha, C.A., Tullu, M.S. and Karande, S., 2023. Utilizing tables, figures, charts and graphs to enhance the readability of a research paper. Journal of postgraduate medicine, 69(3), pp.125-131.

Hogan, A., Blomqvist, E., Cochez, M., d’Amato, C., Melo, G.D., Gutierrez, C., Kirrane, S., Gayo, J.E.L., Navigli, R., Neumaier, S. and Ngomo, A.C.N., 2021. Knowledge graphs. ACM Computing Surveys (Csur), 54(4), pp.1-37.

Lim, D., Hohne, F., Li, X., Huang, S.L., Gupta, V., Bhalerao, O. and Lim, S.N., 2021. Large scale learning on non-homophilous graphs: New benchmarks and strong simple methods. Advances in neural information processing systems, 34, pp.20887-20902.

Wong, D.M., 2023. The Wall Street Journal guide to information graphics: The dos and don'ts of presenting data, facts, and figures. WW Norton & Company.

#### Peer Response to Tamim Al-Mutawa 
Thank you Tamim for correctly identifying that the issue with table 2 is not the data itself but the way it was presented. Narrowing down to three core statistics (mean, n, p-value) makes the analysis much more digestible. 

Data visualisation such as using bar charts and line charts have become popular in analysing data and making informed decisions. To analyse data, often people ask complex reasoning questions about charts involving arithmetic and logical operations (Kim et al, 2020). What I find particularly interesting in Kim et al. (2020) is the emphasis on how these visuals do not just present information, they invite complex reasoning. Readers often need to perform arithmetic (e.g., comparing values, calculating differences) and logical operations (e.g., identifying trends, evaluating significance) to interpret the charts correctly. This means that effective visualisation design is not only about aesthetics, but also about reducing cognitive load and guiding the reader toward accurate conclusions.

In your post you did not oversimplify the analysis to the point of losing accuracy. Instead, you balanced accessibility with precision, which is exactly what editors and readers value.  Your reflection shows strong awareness of the editorial feedback loop where it is clear that editors often push for clarity and accessibility, not just statistical completeness, visuals can carry analytical weight more effectively than oversized tables, and simplification does not mean loss of consistency, but it means prioritising what the reader needs to know.

While the analysis is strong, consider adding a short narrative paragraph that guides the reader through the key findings. For example: “Regions 1 and 5 consistently outperform the national average, while Region 4 lags slightly but not significantly.” This helps readers interpret the analysis much simpler.

Overall, your revision of table 2 demonstrates a thoughtful response to editorial critique. The balance between simplification and statistical integrity is well struck, and the use of statistical tools make the findings more engaging. With a bit more narrative framing and attention to design details, the presentation could be even stronger.

#### References
Kabacoff, R., 2022. R in action: data analysis and graphics with R and Tidyverse. Simon and Schuster.

Lim, D., Hohne, F., Li, X., Huang, S.L., Gupta, V., Bhalerao, O. and Lim, S.N., 2021. Large scale learning on non-homophilous graphs: New benchmarks and strong simple methods. Advances in neural information processing systems, 34, pp.20887-20902.

Masry, A., Do, X.L., Tan, J.Q., Joty, S. and Hoque, E., 2022, May. Chartqa: A benchmark for question answering about charts with visual and logical reasoning. In Findings of the association for computational linguistics: ACL 2022 (pp. 2263-2279).

Nguyen, T., Le, H., Quinn, T.P., Nguyen, T., Le, T.D. and Venkatesh, S., 2021. GraphDTA: predicting drug–target binding affinity with graph neural networks. Bioinformatics, 37(8), pp.1140-1147.

Zhu, Y., Xu, Y., Yu, F., Liu, Q., Wu, S. and Wang, L., 2020. Deep graph contrastive representation learning. arXiv preprint arXiv:2006.04131.

#### Summary Post 
Based on all the posts from the collaboration discussion, it is notable that table II is rich with information, but the presentation raises challenges. Vessey I, 2021 reasons that “The fundamental aspect of the theory is that graphical and tabular representations may contain the same information, but they present that information in fundamentally different ways. Graphical representations emphasize spatial information while tables emphasize symbolic information.” My initial post pointed out  that condensing a dense table into thematic categories and visualising results with charts improves clarity, accessibility, and impact. It also highlighted how bar and pie charts can quickly show consensus or disagreement, saving readers time and reducing textual monotony. 

One peer response was received from Julio Espinosa Rifelf for the collaboration discussion. Julio agreed with the value of graphics but raised methodological concerns about grouping 24-items into 5-themes without transparent mapping which risks subjectivity and violates reporting standards (STROBE). The visualization design that incudes issues like colour duplication, floating baselines, percentages not summing to 100% compromise interpretability and credibility of the data. Julio also stressed that accessibility must align with strict statistical reporting protocols to avoid misleading readers.

I agree with Julio’s concerns about transparency and methodological rigor while my initial approach was about improved readability, Julio’s critique highlights the danger of oversimplification of data tables. To strengthen my original post, I will provide a clear mapping of which statements fall under each theme, ensuring reproducibility and compliance with reporting standards. I also need to refine chart design by using 100% stacked bar charts or consistent baselines, with a well-defined legend to avoid confusion. Lastly, I need to balance completeness with clarity where visuals complement, not replace, the full dataset, so that readers can trace back to the original detail if needed.

Both my post and Julio’s emphasise the importance of clarity and accessibility in research communication. They also agree that visualizations are powerful tools for highlighting consensus and disagreement and the critique from Julio’s feedback reinforces my own reflection that editorial feedback pushes researchers toward more impactful storytelling.

In conclusion, the discussions highlighted dual importance of clarity and rigor in research communication. I note and agree with the point that grouping items must be clearly explained to avoid subjectivity, and that chart design should follow strict reporting standards to ensure interpretability. All the perspectives from the discussion reinforce the fact that effective communication requires both engaging visuals and methodological precision and visual storytelling should enhance, not compromise, the accuracy of data.

#### References
Chen, C. and Ong, S.P., 2022. A universal graph deep learning interatomic potential for the periodic table. Nature Computational Science, 2(11), pp.718-728.

Liu, Z., Zhang, H., Chen, Z., Wang, Z. and Ouyang, W., 2020. Disentangling and unifying graph convolutions for skeleton-based action recognition. In Proceedings of the IEEE/CVF conference on computer vision and pattern recognition (pp. 143-152).

Pollock, D., Peters, M.D., Khalil, H., McInerney, P., Alexander, L., Tricco, A.C., Evans, C., de Moraes, É.B., Godfrey, C.M., Pieper, D. and Saran, A., 2023. Recommendations for the extraction, analysis, and presentation of results in scoping reviews. JBI evidence synthesis, 21(3), pp.520-532.

Vessey, I., 2021. Cognitive fit: A theory‐based analysis of the graphs versus tables literature. Decision sciences, 22(2), pp.219-240.

You, Y., Chen, T., Sui, Y., Chen, T., Wang, Z. and Shen, Y., 2020. Graph contrastive learning with augmentations. Advances in neural information processing systems, 33, pp.5812-5823.

### 2.5	Unit 7: Parametric Tests (Using the Health_Data), to perform the following functions in R.

1.	Find out mean, median and mode of variables sbp, dbp and income.
#### R code to load the dataset 
#### Install and load haven if not already installed
install.packages("haven")

library(haven)

#### Read the SPSS .sav file
Health_Data <- read_sav("Health_Data.sav")
#### Inspect the dataset
head(Health_Data)

str(Health_Data)

#### Mean
mean_sbp <- mean(Health_Data$sbp, na.rm = TRUE)

mean_dbp <- mean(Health_Data$dbp, na.rm = TRUE)

mean_income <- mean(Health_Data$income, na.rm = TRUE)

#### Median
median_sbp <- median(Health_Data$sbp, na.rm = TRUE)

median_dbp <- median(Health_Data$dbp, na.rm = TRUE)

median_income <- median(Health_Data$income, na.rm = TRUE)

#### Mode function (since R doesn’t have a built-in mode for numeric data)
get_mode <- function(x) {

  uniq_vals <- unique(x)
  
  uniq_vals[which.max(tabulate(match(x, uniq_vals)))]
  
}

mode_sbp <- get_mode(Health_Data$sbp)

mode_dbp <- get_mode(Health_Data$dbp)

mode_income <- get_mode(Health_Data$income)

#### Summarize results in a table
results <- data.frame( 

  Variable = c("SBP", "DBP", "Income"),
  
  Mean = c(mean_sbp, mean_dbp, mean_income),
  
  Median = c(median_sbp, median_dbp, median_income),
  
  Mode = c(mode_sbp, mode_dbp, mode_income)
  
)

print(results)

#### Table 1: Basic statistics results 
Variable;  	    Mean;	        Median;	      Mode

SBP;            127.73;    	  123.0;        	120

DBP;	          82.77;        82.0;         	80

Income;	        85 194.49;   	86 560.5;      79 774

2.	Find out the five-figure summary of income variable and present it using a Boxplot.
#### Five-number summary of income
summary(Health_Data$income)
#### Alternatively, explicitly:
fivenum(Health_Data$income)
#### Boxplot of income
boxplot(Health_Data$income,

        main = "Boxplot of Income",
        
        ylab = "Income",
        
        col = "lightblue",
        
        border = "darkblue")

![Boxplot of income](https://raw.githubusercontent.com/Velim73285-Star/Velim73285-Star.GitHub.io/main/assets/images/banners/Boxplot%20of%20income.PNG)
   
3.	Run a suitable hypothesis test to see if there is any association between systolic blood pressure and presence and absence of peptic ulcer.
   
#### Step 1: Clarify the variables
•	sbp: Continuous variable (systolic blood pressure).

•	pepticulcer: Categorical variable with two groups (Yes = presence, No = absence).

This is essentially a comparison of mean systolic blood pressure between two independent groups.

#### Step 2: Choose the hypothesis test
•	Null hypothesis (H₀): There is no difference in mean systolic blood pressure between those with and without peptic ulcer.

•	Alternative hypothesis (H₁): There is a difference in mean systolic blood pressure between the two groups.

#### The suitable test depends on assumptions:

•	If sbp is approximately normally distributed in each group and variances are equal → Independent samples t-test.

•	If normality or equal variance assumptions are violated → Mann–Whitney U test (non-parametric alternative).

#### R code to do the test hypothesis
library(haven)

#### Read SPSS file correctly
Health_data <- read_sav("Health_data.sav")

Health_data <- read.sav("Health_data.sav")

#### Independent samples t-test
t.test(sbp ~ pepticulcer, data = Health_data, var.equal = TRUE)

#### If variances are unequal
t.test(sbp ~ pepticulcer, data = Health_data, var.equal = FALSE)

#### Non-parametric alternative (Mann-Whitney U test)
wilcox.test(sbp ~ pepticulcer, data = Health_data)

#### Results
#### Two Sample t-test
Data is based on sbp (systolic blood pressure) by pepticulcer

t = 1.2772,         df = 208,       p-value = 0.203

Alternative hypothesis: true difference in means between group 1 and group 2 is not equal to 0

At 95 percent confidence interval: -2.89    to      11.80

#### Sample estimates:
mean in group 1;      mean in group 2 

    131.3171;            126.8639 

#### Welch Two Sample t-test

Data is based on sbp (systolic blood pressure) by pepticulcer

t = 1.2142,             df = 57.562,            p-value = 0.2296

Alternative hypothesis: true difference in means between group 1 and group 2 is not equal to 0

At 95 percent confidence interval:  -2.89   to     11.80

#### Sample estimates:
mean in group 1;             mean in group 2  

131.3171;                    126.8639 

####  Wilcoxon rank sum test with continuity correction
Data is based on sbp (systolic blood pressure) by pepticulcer

W = 3975.5,                         p-value = 0.1434

Alternative hypothesis: true location shift is not equal to 0

In conclusion, since the confidence interval spans both negative (-2.89) and positive (11.80) values, the evidence is inconclusive and the data do not show a clear association. The sample suggests that there might be a small difference, but statistically, we cannot rule out the possibility that there is no difference at all.

### 2.6	Unit 8: Nonparametric tests

#### 2.6.1	Data activity 6

Using the Health_Data, please perform the following functions in R:

1.	Find out the mean, median and mode of ‘age’ variable.
   
#### R code to answer the question.
####  Load required packages
library(haven)   # for importing SPSS .sav files

library(dplyr)   # for data manipulation

#### Import the SPSS dataset
health_data <- read_sav("Health_data.sav")

#### Inspect the structure to confirm variable names
str(health_data)

#### Calculate mean and median
mean_age <- mean(health_data$age, na.rm = TRUE)

median_age <- median(health_data$age, na.rm = TRUE)

#### Mode function (since R has no built-in mode for numeric data)

get_mode <- function(x) {

  uniq_vals <- unique(x)
  
  uniq_vals[which.max(tabulate(match(x, uniq_vals)))]
  
}

mode_age <- get_mode(na.omit(health_data$age))

#### Display results
cat("Mean Age:", mean_age, "\n")

cat("Median Age:", median_age, "\n")

cat("Mode Age:", mode_age, "\n")

#### Table 1: mean, median and mode for age
Mean = 26.51

Median = 27

Mode = 26

2.	Find out whether median diastolic blood pressure is same among diabetic and non-diabetic participants.

#### R code to answer the question
#### Load required packages
library(haven)   # import SPSS .sav files

library(dplyr)   # data manipulation

library(coin)    # non-parametric median test

#### Import dataset
health_data <- read_sav("Health_data.sav")

#### Inspect variable names to confirm
str(health_data)

#### Assuming variables are named:
"dbp"      = diastolic blood pressure

"diabetes" = 1 for diabetic, 0 for non-diabetic

#### Step 1: Compare group medians
health_data %>%

  group_by(diabetes) %>%
  
  summarise(median_dbp = median(dbp, na.rm = TRUE))
  
#### Step 2: Formal median test
median_test_result <- median_test(dbp ~ factor(diabetes),

                                  data = health_data,
                                  
                                  distribution = "exact")
                                  
median_test_result

Wilcoxon rank sum test with continuity correction

Data is dbp by diabetes

W = 3804.5, p-value = 0.7999

alternative hypothesis: true location shift is not equal to 0

Yes =	83

No = 82

Wilcoxon Test Statistic

W = is 3804.5  and p-value is = 0.7999284

Conclusion, the p value is very high, above 0.05  and this means that there is no statistically significant difference in diastolic blood pressure between diabetic and non diabetic participants in your dataset

3.	Find out whether systolic BP is different across occupational group.

#### R code to answer the question.
#### Load required packages

library(haven)   (import SPSS .sav files)

library(dplyr)   (data manipulation)

#### Import dataset
health_data <- read_sav("Health_data.sav")

#### Inspect variable names (optional)
str(health_data)

#### Step 1: Descriptive medians/means by occupation
group_summary <- health_data %>%

  group_by(occupation) %>%
  
  summarise(
  
    mean_sbp   = mean(sbp, na.rm = TRUE),
    
    
    median_sbp = median(sbp, na.rm = TRUE),
    
    sd_sbp     = sd(sbp, na.rm = TRUE),
    
    n          = n()
    
  )
  
print(group_summary)

#### Step 2: Formal test
#### If SBP is approximately normal, use one-way ANOVA
anova_result <- aov(sbp ~ factor(occupation), data = health_data)

summary(anova_result)

#### Step 3: Non-parametric alternative (Kruskal-Wallis test)
kruskal_result <- kruskal.test(sbp ~ factor(occupation), data = health_data)

print(kruskal_result)

![Boxplot of income](https://raw.githubusercontent.com/Velim73285-Star/Velim73285-Star.GitHub.io/main/assets/images/banners/Kruskal_Wallis_test_result.PNG)
  
Kruskal-Wallis rank sum test

Data is sbp by factor (occupation)

Kruskal-Wallis chi-squared = 0.77906, df = 3, p-value = 0.8545

Conclusion, using the ANOVA output where the F value = 0.233 and p = 0.873, this means that when comparing mean systolic blood pressure (SBP) across the four occupational groups, the differences are not statistically significant. Using the Kruskal Wallis output, where the Chi squared = 0.779, df = 3, and p = 0.8545, this non parametric test does not assume normality and it also shows a very high p value, confirming that the median of SBP does not differ significantly across occupational groups.

#### 2.6.2	Scenario-Based Exercise – 95% Confidence Interval

An HR organisation wishes to introduce a new set of training programs to increase the work efficiency of their employees. To do this, the organisation hires 3 vendors such that each vendor will train a group of employees with a one-week program. It is assumed that the employees across the three groups have same work efficiencies before the start of the program. The following table summarises the scores obtained post the one-week training. Each group has 8 employees.

Now, find out the mean efficiency of each vendor and determine which vendor shows a higher significance of improvement in employee efficiency statistically at the 95% level.

![Boxplot of income](https://raw.githubusercontent.com/Velim73285-Star/Velim73285-Star.GitHub.io/main/assets/images/banners/Group_scores_per_vendor.PNG)

#### Calculate mean efficiency per vendor
Vendor 1 mean = 44.71 

Vendor 2 mean = 51.00 

Vendor 3 mean = 27.71 

Critical value at 95% level

F0.02.2.18 = 3.55

Since the F= 20.11 which is > 3.55  we then we reject the null hypothesis and conclude that at the 95% confidence level, the ANOVA shows a significant difference in efficiency. Vendor 2 demonstrates the highest and statistically significant improvement in employee efficiency.

### 2.7	Unit 9: Creating cross-tabulations and performing Chi-square analysis
#### 2.7.1	Data Activity 7

1.	Using variables State/UnionTerritory (grouped into regions) and ConfirmedIndianNational + ConfirmedForeignNational (grouped into case levels) create a cross-table showing the relationship between Region and Case Severity Level.

#### R code to answer the question   

covid <- read.csv("COVID_19_Indi_ataset_(January_2020_March_2020).csv")

#### Define regions

region_map <- list(

  North = c("Delhi","Haryana","Punjab","Uttar Pradesh","Uttarakhand","Himachal Pradesh","Jammu and Kashmir","Chandigarh"),
  
  South = c("Kerala","Tamil Nadu","Karnataka","Andhra Pradesh","Telengana","Puducherry"),
  
  West = c("Rajasthan","Gujarat","Maharashtra","Goa"),
  
  East = c("West Bengal","Odisha","Bihar","Jharkhand"),
  
  Central = c("Madhya Pradesh","Chhattisgarh"),
  
  UnionTerritories = c("Union Territory of Ladakh","Union Territory of Jammu and Kashmir",
  
                       "Union Territory of Chandigarh","Pondicherry","Puducherry")
                       
)

#### Add Region variable
covid$Region <- sapply(covid$StateUnionTerritory, function(x) {

  for (r in names(region_map)) {
  
    if (x %in% region_map[[r]]) return(r)
    
  }
  
  return("Other")
  
})

#### Compute total cases
covid$TotalCases <- covid$ConfirmedIndianNational + covid$ConfirmedForeignNational

#### Categorize severity levels
covid$Severity <- cut(covid$TotalCases,

                      breaks = c(-Inf,5,15,Inf),
                      
                      labels = c("Low","Medium","High"))

#### Cross-tabulation
table_result <- table(covid$Region, covid$Severity)

print(table_result)    

![Boxplot of income](https://raw.githubusercontent.com/Velim73285-Star/Velim73285-Star.GitHub.io/main/assets/images/banners/Cross_tabulation_table_for_case_severity.PNG)  

2.	Using variables ConfirmedIndianNational + ConfirmedForeignNational (grouped into case levels) and variable: Cured (grouped into recovery status) create a cross-table showing the relationship between Case Severity Level and Recovery Status.

#### R code to answer the question   

#### Load dataset 
covid <- read.csv("COVID_19_Indi_ataset_(January_2020_March_2020).csv")

#### Compute total cases
covid$TotalCases <- covid$ConfirmedIndianNational + covid$ConfirmedForeignNational

#### Categorize case severity
covid$CaseSeverity <- cut(covid$TotalCases, breaks = c(-Inf,5,15,Inf), labels = c("Low","Medium","High"))

#### Categorize recovery status
covid$RecoveryStatus <- cut(covid$Cured, breaks = c(-Inf,0,5,Inf), labels = c("None","Some","Many"))

#### Cross‑tabulation
table_result <- table(covid$CaseSeverity, covid$RecoveryStatus)

print(table_result)

![Boxplot of income](https://raw.githubusercontent.com/Velim73285-Star/Velim73285-Star.GitHub.io/main/assets/images/banners/Cross_tabulation_table_for_recovery_status.PNG)

### 2.8	Unit 10: Correlation 
#### 2.8.1	Data Activity 8
Using the Health_Data, perform the following functions in R and the questions.

1.	Find out correlation between systolic and diastolic BP.
   
#### R code to answer the question
#### Install required packages if not already installed

install.packages("readxl")

#### Load library
library(readxl)

#### Read the Excel file
health_data <- read_excel("Health_Data.xlsx")

#### Inspect column names to confirm exact labels
names(health_data)

#### Extract systolic and diastolic BP columns
systolic <- health_data$sbp

diastolic <- health_data$dbp

#### Compute Pearson correlation
correlation <- cor(systolic, diastolic, method = "pearson")

#### Print result
print(correlation)

#### Results
Correlation coefficient between systolic BP and diastolic BP = 0.846808

Conclusion: A correlation coefficient of 0.8468 between systolic blood pressure (SBP) and diastolic blood pressure (DBP) means there is a very strong positive linear relationship between the two variables.

2.	Produce a scatter plot between systolic and diastolic BP.

#### R code to answer the question
#### Install required packages if not already installed

install.packages("ggplot2")

install.packages("readxl")

#### Load libraries
library(ggplot2)

library(readxl)
#### Read the Excel file
health_data <- read_excel("Health_Data.xlsx")

#### Create scatter plot
ggplot(health_data, aes(x = sbp, y = dbp)) + geom_point(color = "blue", alpha = 0.6) + 

geom_smooth(method = "lm", se = TRUE, color = "red") + labs(title = "Scatter Plot: Systolic vs Diastolic BP",

       x = "Systolic BP (mmHg)",
       
       y = "Diastolic BP (mmHg)") +
       
  theme_minimal()

![Boxplot of income](https://raw.githubusercontent.com/Velim73285-Star/Velim73285-Star.GitHub.io/main/assets/images/banners/Scatter_plot_for_Systolic_Vs_Diastolic_BP.PNG)

## 3.	What exactly have I learnt and how?
To be completed

### 3.1 What have I learnt from this module?
To be completed

### 3.2 The how part of learning the above
To be completed

## 4.	Professional skills gained and enhanced as a result of the module 
To be completed


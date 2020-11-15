# Salaries-Prediction-Portfolio-Project
This portfolio project uses job openings data to explore the variables that relates to the salary of a job, and creates a predictive model to predict salaries.

## Introduction

In the process of recruitment, one of the most important topic is allocating the right salary for a job role. Whether you're a hiring manager or a candidate applying for a job, the conversation on salary always come up. 

For recruiters, it's important to allocate a specific salary range for a job opening that ensures market competitivness while keeping within the budget. In contrast, for candidates, a reasonable target is needed to make sure they are being compensated for what they are truly worth of. Both parties seldom start with the same target salary. Therefore, most of the time, the last step of recruitment is salary negotiation. But even before the negotiations start, how can we ensure that we are offering or asking the right salary for a certain job opening?

For most people, the frame of reference is the current job market. Multiple platforms collect and provide salary data including what's the mean or median salary for a certain job position in a particular location. The variables that determine the salary are much more than the job title. A Data Analyst working at a startup in Kuala Lumpur is highly likely to be earning significantly less than a Data Analyst in a major finance firm in Hong Kong. 

In this project, we will explore a dataset of thousands of job positions with their "attributes" as well as the salary for each of them. These attributes include job title, degree required, years of Experience, distance from city centre, job industry, etc. We will explore and analyze the dataset to see what factors show correlation with salary and whether these correlations are positive or negative. The second part of the project is to use the dataset to build a predictive model that takes in job openings' attributes and requirements, and predict the salaries. 

## Data

The dataset includes the followin three CSV files:

1. **train_features.csv:** Each row represents metadata for an individual job posting.
2. **train_salaries.csv:** Each row associates a “jobId” with a “salary”.
3. **test_features.csv:** Similar to train_features.csv, each row represents metadata for an individual job posting.

The 'jobId' column is a unique idenitifier for each job opening. The first row of each file contains headers for the columns. The data may contain errors and invalid values. 

### Loading the Data

We will load the data from all three CSVs into two dataframes. **train_features.csv** and **tran_salaries.csv** files will be concatenated together into a single dataframe. **train_df**. **test_features.csv** will be loaded as a separate dataframe, **test_df**.

The dataset contains the following features:

- **jobId** - A unique identifier for each job position in the dataset.
- **companyId** - A company identifier unique to each company.
- **jobType** - job role labelled under different categories (Janitor, Junior, Senior, Manager, CFO, CTO, Vice President, and CEO)
- **degree** - Type of degree (None, High School, Bachelors, Masters, and Doctoral)
- **major** - Major if there's a degree (None, Chemistry, Literature, Engineering, Business, Physics, CompSci, Biology, and Math)
- **industry** - Job industry (Web, Auto, Finance, Education, Oil, Health, and Service)
- **yearsExperience** - Years of experience of the candidate 
- **milesFromMetropolis** - Job location's distance from metropolis

The target feature is:
- **salary** - annual compensation for a job position in US dollars 

## Data Cleaning

Before starting with EDA, we will make sure that the datasets are complete without missing and invalid values. All three files contain 1 million rows. 

At this point we will also separate columns into numerical and categorical columns. yearsExperience, milesFromMetropolis and salary are the only numerical columns, the rest are categorical columns. 

#### Finding Missing Values

No Null/NaN values were found in the dataset. The None values in degree and major columns refer to candidates without a degree and major. Therefore, these none values are not considered missing values. 

#### Finding invalid data

In order to find invalid data in the categorical columns, we looked at the unique values of each feature along with their counts. No invalid data was found. 

For numerical columns, the describe() function was used to look for invalid data points in yearsExperience, milesFromMetropolis and salary features. 

![train_df Describe](https://github.com/ali-javaid93/Salaries-Prediction-Portfolio-Project/blob/main/images/train_df_describe.jpg)

For Years of Experience, the min and max values are 0 and 24 years respectively, while the mean is 11.9 years. 
For Miles from Metropolis, the min and max values are 0 and 99 miles respectively, while the mean is 49.5 miles. 
For Salary, the min and max values are $0 and $301K respecitvely, while the mean is $116.1. 

While both Years of Experience and Miles from Metropolis can be 0, a salary for a paid job cannot be 0. Therefore, one or more job positions have $0 for salary. We found that only 5 rows had $0 salary, which can be easily dropped from the dataframe. However, this solution may not fully remove invalid data in the salary column. 

#### Removing Outliers in Salary column

To ensure we get rid of all invalid data in the salary column, we first have to plot the distribution of salary to find the outliers. 

![Salary_distribution](https://github.com/ali-javaid93/Salaries-Prediction-Portfolio-Project/blob/main/images/salary_distribution.jpg)

The boxplot above shows outliers in the lower and upper bands of the distribution. The salary column is normaly distributed. Using the boxplot, we defined the Inter-Quartile range of salary column with the upper and lower bounds to be 220.5 and 8.5 respectively. Values below $8.5K and above $220.5K are outliers and can be considered as invalid data. 
On further expection, the outliers in the lower band are all $0 values that were then dropped from the dataframe.

The outliers in the upper band, however, don't appear to be extreme values. It's not unusual for a CEO or other executive roles to earn up to $300K annually. Out of 7117 outliers in the upper band, only 20 jobs were of Junior positions. However, all these junior positions were either in Finance or Oil industries which are known to offer higher salaries. In addition, most of the outliers belong to jobs with CEO, CFO and CTO positions. Thus, we do not have enough evidence to label these outliers as invalid data points. These outliers were kept in the data. 

## Exploratory Data Analysis

After cleaning the data by removing missing, duplicated, and invalid values, we will proceed with exploring each feature in comparison with salary column. The purpose of this section is to see which feature correlates more with the salary and whether the correlation is a positive or a negative correlation. The final step is to create a correlation matrix to quanitfy the correlation among all features. 

### Summarizing Each Feature

A function was created that:
- plot the distribution of samples on the feature
- visualize the dependance of salary on the feature

#### companyId



#### jobType

#### degree

#### major

#### yearsExperience

#### milesFromMetropolis

#### industry

### Correlation Matrix


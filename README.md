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

#### Finding Missing Values

#### Finding invalid data

#### Removing Outliers in Salary column

## Exploratory Data Analysis

### Summarizing Each Feature

#### companyId

#### jobType

#### degree

#### major

#### yearsExperience

#### milesFromMetropolis

#### industry

### Correlation Matrix


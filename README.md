# Capstone Partner Project: Mental Health in Tech
This repository contains my contributions to a capstone project I completed during my Data Science Master's program. 

## Project Goals
The main goal of this project was to determine ways employers can reduce the impact of mental health issues on their employees.  
  
This project also aimed to examine circumstances both in and out of company control to find possible indicators of whether an employee seeks treatment for mental health and whether an employee feels comfortable discussing mental health issues with a supervisor.

## Project Significance
Mental health issues can affect anyone, making it a global issue.  
Poor mental health and lack of treatment can negatively impact all aspects of life.  
Improving employee mental health and quality of life has been shown to increase productivity, work quality, and job satisfaction.

## The Data
Dataset: [Kaggle](https://www.kaggle.com/datasets/osmi/mental-health-in-tech-survey/data)  

This data comes from a 2014 survey created by OSMH (Open Sourcing Mental Health).  
It contains demographic information and attitudes towards mental health in the workplace . 

## Data Prep & Cleaning
[Data Prep & Cleaning Notebook](https://github.com/SarahMillard98/Capstone_Project_Mental_Health_in_Tech/blob/main/Capstone_Final_Project_DataCleaning.ipynb)   

 Data cleaning/preparation for this project included:
 - Removing unnecessary columns
   - Dropping 'Timestamp', 'comments', and 'state' columns
   - Filtering out self-employed instances, then dropping the 'self-employed' column
   - Dropping instances of companies with fewer than 6 employees
   - Filtering out instances not working in tech, then dropping the 'tech_company' column
 - Cleaning messy text data in the 'gender' column
   - Capitalizing all strings in column
   - Replacing misspellings to create 3 categories: 'Female', 'Male', 'Trans/NB'
   - Dropping the remaining instances after confirming they did not hold useful information
 - Removing potentially misimputed numerical data from the 'age' column
   - Transforming all values in 'age' column using abs() to remove negative values 
   - Filtering to only include ages less than 100 and greater than 18
- Solving issue causing null values in 'work_interfere' column
  - Inferring that nulls were most likely caused by question not being applicable to those without mental health issues
  - Replacing null values with 'NotApplicable'
 
## Exploratory Data Analysis
[EDA & Feature Selection Notebook](https://github.com/SarahMillard98/Capstone_Project_Mental_Health_in_Tech/blob/main/Capstone_Final_Project_EDA_Feature_Selection.ipynb)  



## Feature Selection & Importance

## Final Suggestions


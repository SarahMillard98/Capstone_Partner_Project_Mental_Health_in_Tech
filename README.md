# Capstone Partner Project: Mental Health in Tech
This repository contains only my contributions to a capstone project I completed with a partner during my Data Science Master's program. 

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
It contains demographic information and attitudes towards mental health in the workplace. 

## Data Prep & Cleaning
[Data Prep & Cleaning Notebook](https://github.com/SarahMillard98/Capstone_Project_Mental_Health_in_Tech/blob/main/Capstone_Final_Project_DataCleaning.ipynb)   

 Data cleaning/preparation for this project included:
- Removing unnecessary columns
- Cleaning messy text data in the 'gender' column
- Removing potentially misimputed numerical data from the 'age' column
- Solving issue causing null values in 'work_interfere' column

 
## Exploratory Data Analysis
[EDA & Feature Selection Notebook](https://github.com/SarahMillard98/Capstone_Project_Mental_Health_in_Tech/blob/main/Capstone_Final_Project_EDA_Feature_Selection.ipynb)  

I performed EDA on this dataset through summary statistics, visualizations, and contingency tables.   

First, I confirmed that our predicted variables, 'treatment' and 'supervisor, were evenly distributed.   
![image](https://github.com/user-attachments/assets/ead15c71-ebbf-4c1c-8706-4f683aecef1d)  ![image](https://github.com/user-attachments/assets/cfa0ca37-bea4-4e03-92e0-6d5f6f2b1f95)


I was also curious about the distribution of the gender and age variables.  
![image](https://github.com/user-attachments/assets/f3f63e10-d8ee-4a62-8c11-50c255369fd6)  ![image](https://github.com/user-attachments/assets/6636ece5-1c9b-4855-8856-cf2a02353f30)  
As you can see, the repondents were mostly male. This most likely reflects the gender distribution of tech in 2014, though it may also be indicative of how the survey was distributed.  
The age variable seems to be distributed as I would expect, with most workers between 25 and 35 years of age. There is a general increase from 18-25, and a general decrease from 35 - 65.  

Through my EDA, I was also able to identify several possible indicators of seeking treatment:
- Employer-provided mental health benefits
- Employee knowledge of care and treatment options
- Employee knowledge of anonymity while using mental health resources/treatment  

 I also identified several possible indicators of employee comfort level discussing mental health with a supervisor
 - Gender
   - Males may be more likely to be comfortable discussing mental health with a supervisor
 - Employee level of comfort discussing mental health with coworkers
 - Anticipated negative consequences for discussing mental health
 - Observed negative consequences for discussing mental health

## Feature Selection & Importance  
For feature selection, I wanted to compare a Random Forest Classifier model and an XGBoost Classifier model. I started by completing two final preprocessing steps: one-hot encoding categorical variables and scaling 'age', the only numeric variable. I then began building models to find feature importance for both the 'treatment' variable (whether or not an employee sought treatment for mental health issues) and the 'supervisor' variable (level of comfort discussing mental health with a supervisor)  

### Feature Importance for 'treatment'   

After splitting the data into train and test sets, I started by building a Random Forest model, fitting it on the training data, and visualizing the feature importance. After viewing the first set of feature importance, I was able to remove several low-importance variables from the dataset to get better results. I also noticed that 'work_interfere_NotApplicable' had an unusually high feature importance. I decided to remove this variable as well, deducing that the reason it was so high was because it was an indicator of an individual with no mental health issues.   

After re-fitting the RF model, I was able to get a nice visualization of the feature importance.  
![image](https://github.com/user-attachments/assets/11dd492b-1006-40d8-83e3-720bb9b871bb)  

Then using the split data with low importance features already removed, I built and trained an XGBoost Classifier model. The initial feature importance listed the 'age' variable as having an unbelievably high feature importance. I decided to tune the model using gridsearch cv to see if that improved the feature importance. After fitting the tuned model, I was able to get a much better feature importance.  
![image](https://github.com/user-attachments/assets/a4563ff1-2b14-4986-a25d-786798792c1a)  

Comparing the feature importances from the RFClassifier and the XGBoostClassifier, both were very similar. The main difference between the two was the order or level of importance for some features.  

Overall, the main important features identified by both RF and XGBoost were:  
+ Whether or not a mental health issue impacts work
+ Family history of mental health issues
+ Anonymity in seeking help
+ Employer-provided mental health care benefits
+ Knowledge of the mental health care options provided by employer
+ Gender
+ Age

### Feature Importance for 'supervisor'

I followed the same procedure for the 'supervisor' variable as I did above for the 'treatment variable.  

The low-importance variables dropped after the first round of the Random Forest Classifier were all country variables. After refitting the RF model, I once again visualized the feature importance.  
![image](https://github.com/user-attachments/assets/886f7b89-a057-421e-a996-e1f0ea3a28dd)  

Then I used the trimmed data to fit an XGBoost Classifier. Once again, the 'age' variable was extremely high in importance. After tuning the model, 'age' was still the highest importance, but it fit in nicely with the other important variables. It does make sense that age might have an impact on someone's comfort level speaking to a supervisor about mental health. Generally speaking, younger individuals are more open about mental health. However, it is worth noting that the age variable is the only numerical variable in the dataset and although I did scale it to fit within the encoded categorical variables, it could still be skewing the results.   

Here is the final XGBoost feature importance visualization.  
![image](https://github.com/user-attachments/assets/2f773698-793f-4aea-be2e-3bcc5f44eec2)  

Once again, the feature importance was fairly similar between the two models.

Overall, the main important features identified by both RF and XGBoost were:
+ Age
+ Level of comfort speaking with coworkers about mental health
+ Whether the individual anticipates negative consequences for speaking about mental health issues with their employer
+ Whether the individual anticipates negative consequences for speaking about physical health issues with their employer
+ Level of comfort bringing up mental health in an interview with a potential employer
+ Knowledge of the mental health care benefits provided by their employer

## Final Reccomendations

Final recommendations for what employers should do to reduce the impact of mental health issues on employees:
- Provide health care benefits that include mental health care
- Ensure that all employees are made aware of available benefits and care options through email reminders or in-office materials
- Implement employee wellness programs & include mental wellness options
- Encourage employees to feel safe accessing mental health resources by guaranteeing anonymity to those who do so
- Encourage a mindset of treating mental health as being as important as physical health
  - Implement policies that encourage taking time off for mental health as well as physical health issues
  - Encourage leadership to be mindful of the mental health of their subordinates, possibly through trainings/workshops

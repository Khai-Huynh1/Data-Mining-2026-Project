# Impact of AI on jobs in different sectors

### Link to the Project File: https://github.com/Khai-Huynh1/Data-Mining-2026-Project/blob/main/data_mining_project_spring_2026.ipynb

## Deliverable 1 (Problem Definition and Data Acquisition) Summary:
This project analyzes the impact of AI on employment across different industries and job sectors. 
The goal is to classify the status of a given employee's job, whether it was unchanged, modified, or replaced.

## Deliverable 2 (Exploratory Data Analysis (EDA) & Data Preparation) Summary:
### Data Exploration Overview
The AI impact on jobs dataset consists of 2000 rows and 17 columns in a tabular format. The dataset contains a mix of object and integer data types which were transformed into numeric format for modeling. No missing values were found across any column. The target variable Job_Status is class-imbalanced, consisting of 54.65% Unchanged, 40.05% Modified, and 5.30% Replaced, this will be addressed at the modeling stage via class_weight='balanced' in the Random Forest. Preliminary AutoViz visualizations suggest that higher AI adoption levels correlate with greater likelihood of job modification or replacement.
### Data Preparation
Three columns were removed prior to modeling: Employee_ID was dropped as a unique identifier with no predictive value, Age was dropped due to a high correlation with Years_Experience, and Salary_Before_AI was dropped due to a high correlation with Salary_After_AI. Ordinal encoding was applied to Education_Level, AI_Adoption_Level, Job_Status, and Automation_Risk to preserve their natural or assigned ranking. Binary encoding was applied to Upskilling_Required and Remote_Work. One-hot encoding with was applied to Gender, Industry, and Job_Role to handle nominal categories without implying order. The dataset was split 80/20 into training and test sets using stratified sampling to preserve class proportions across both sets.

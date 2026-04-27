# Impact of AI on jobs in different sectors

### Link to the Project File: https://github.com/Khai-Huynh1/Data-Mining-2026-Project/blob/main/data_mining_project_spring_2026.ipynb

## Section 1: Problem Definition and Data Acquisition Summary:
- This project analyzes the impact of AI on employment across different industries and job sectors. 
The goal is to classify the status of a given employee's job, whether it was unchanged, modified, or replaced.

## Section 2: Exploratory Data Analysis (EDA) & Data Preparation Summary:
### Data Exploration Overview
- The AI impact on jobs dataset consists of 2000 rows and 17 columns in a tabular format. The dataset contains a mix of object and integer data types which were transformed into numeric format for modeling. No missing values were found across any column. The target variable Job_Status is class-imbalanced, consisting of 54.65% Unchanged, 40.05% Modified, and 5.30% Replaced, this will be addressed at the modeling stage via class_weight='balanced' in the Random Forest. Preliminary AutoViz visualizations suggest that higher AI adoption levels correlate with greater likelihood of job modification or replacement.
### Data Preparation
- Three columns were removed prior to modeling: Employee_ID was dropped as a unique identifier with no predictive value, Age was dropped due to a high correlation with Years_Experience, and Salary_Before_AI was dropped due to a high correlation with Salary_After_AI. Ordinal encoding was applied to Education_Level, AI_Adoption_Level, Job_Status, and Automation_Risk to preserve their natural or assigned ranking. Binary encoding was applied to Upskilling_Required and Remote_Work. One-hot encoding with was applied to Gender, Industry, and Job_Role to handle nominal categories without implying order. The dataset was split 80/20 into training and test sets using stratified sampling to preserve class proportions across both sets.

## Section 3: Model Development, Evaluation & Interpretation

- Four Random Forest Models were trained and evaluated, with two being a baseline random forest model along with a tuned model, and the other two models being similar but using the dataset with synthetic records added using SMOTE.

- All four models achieved consistent overall accuracy of 94% and Cohen's Kappa scores around 0.88, though this is largely driven by strong performance on the Unchanged and Modified classes rather than the model being uniformly strong across all three.

- Predicting Replaced remained the central challenge throughout. The baseline started at an F1 of 0.21, and the tuned original model made the biggest leap to 0.61, catching 95% of actual Replaced cases. SMOTE did not improve on this, with the tuned SMOTE version actually regressing to 0.36, suggesting the Replaced/Modified overlap is a genuine feature space problem rather than simply a data volume issue.

- Automation Risk and AI Adoption Level dominated feature importance in both tuned models by a wide margin, with all other features being marginal by comparison. This ranking was stable across both the original and SMOTE versions, confirming the model's decision logic is consistent regardless of training data composition.

- From a real-world standpoint, the model has practical value as an early warning tool for labor organizations to identify AI-disrupted roles, with the caveat that distinguishing Modified from Replaced remains its weakest point. Incorporating more granular task-level features or interaction terms between the two dominant predictors would be the most promising path toward improving Replaced detection.

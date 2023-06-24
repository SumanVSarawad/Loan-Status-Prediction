# Loan-Status-Prediction

### Code and Resources Used
Python Version: 3.11 Packages Used:Pandas, Numpy, Seaborn, matplotlib, scipy, scikit-learn, xgboost

This Project consists of:
 - Data Exploration, Cleaning and Imputation
 - Feature Engineering
 - Model Selection - Hyperparameter Tuning
 - Model Assessment
 - Proposal of a classification model for predicting whether the loan is approved

### FEATURES
The various features of the dataset are explained below:

1) Loan Id:
2) Gender
3) Marital status
4) Dependents
5) Education
6) Self Employed
7) Applicant Income
8) Coapplicant Income
9) LoanAmount
10) Loan Amount Term
11) Credit History
12) Property Area
13) Loan Status

**NOTE:** <br>
* We have a balanced distribution of loan approved vs denied of 68% vs 32%
* ![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/c8ebd259-639c-483a-a7b8-6cf83d0a6b90)

### Exploratory Data Analysis

![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/5c1dc794-b46b-4441-9a10-efe49509fb95)

#### Percent wise plots of loan status with different variables
![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/15e76ad9-abec-4b73-a2f8-591095205f8c)
**Comments:** <br>
- Married vs Loan status - If you are married, then chances of getting loan approved are more (71.8%) than if you are not married (62.9%).
- Education vs Loan status - If you are married, then chances of getting loan approved are more (70.8%) than if you are not married (61.19%).

![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/d573e7a5-e5d6-463e-bf39-ca36b4e25715)
**Comments:** <br>
- If you are self employed then loan amount is HIGHER for both approved and denied loan

![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/82bfad39-76ff-430c-9e62-b18ac8f8ac78)
 **Notes:** <br>
- Most of the Applicant income vs Loan Amount is almost symmetrical for both denied and approved loan with the major difference being the credit history

Heatmap describing correlation
![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/e2674021-ad81-47a9-bfd6-f656f3cd0cf9)

### Feature Engineering
#### Functions to add new feature to our model
* Total income - combined income of applicant and coapplicant
* Mean EMI per dependents
* Ratio of Loan Amount to Total Income
* Balance Income - Income left after paying EMI
* Ratio of Loan Amount/Total Income in different property area

### Matrix comparision of the 3 models used
* Logistics Regression
* Support vector classifier
* XG Boost

![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/fe4574cf-399a-456e-bb8c-59ed798faaa0)

![image](https://github.com/SumanVSarawad/Loan-Status-Prediction/assets/118813644/31196823-7b19-4ec1-a79b-1c595aa12f55)

### Discussion on Model Selection and Results: Proposed Classifier for loan status prediction

As stated in the previous sections, the main points found during the analysis are the following:
- In terms of data pre-processing, the dataset resulting from replacing missing data with the median for numeric and most frequent for categorical.
- Analyzing the data using EDA and visualizing the relationship between the given variables provides credit history, property area and graduate as the major contributing factors to loan status. 
- SVC with optimal hyperparameter tuning is outperforming XGB and logistic regression in the given dataset, this is due to the SVC's ability to perform better than most algorithms for smaller dataset. Low complexity and simple models like SVC generalize the best with smaller datasets.
- It was found that only 10 features (out of the intial 12 + added 7) are sufficient to confidently predict the response variable. These features are: **'Credit_History', 'Dependents', 'CoapplicantIncome',  'LoanAmount_per_Total_Income', 'EMI_per_LoanAmount', 'Balance_Income', 'Property_Area_LoanAmount_per_Total_Income_mean', 'x0_Female', 'x2_Graduate', 'x4_Rural'.**

- Assessing the different kinds of classifiers, **the best performance was obtained by training a SVC Classifier**.
- This can be observed when comparing SVC, Logistic regression and the XGB Classifiers in the ROC/AUC analysis.

- The trained SVC Classifier, is characterized by the following hyperparameters:
    - SVC Kernel - Sigmoid
    - C - 10
    - Degree - 2
    - Gamma - 0.01

- The perfomance is at:
    - Accuracy of 81.3% on training set,
    - Accuracy of 78.8% on test set.
    - F1 Score of 86.59%
- According to the results, the classifier don't exhibit overfitting, and the variance-bias is well traded.
- **This SVC-Based classifier is recommended to be deployed, and be used into predicting whether the loan is approved**.

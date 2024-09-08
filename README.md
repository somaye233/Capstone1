## Bank Marketing
=========================
Overview
I will use a real-world bank marketing dataset. This dataset is related to direct marketing campaigns (phone calls) of a Portuguese banking institution. The dataset contains information about customers contacted as part of a telephone marketing campaign trying to get customers to sign up for a term deposit product. The dataset also contains information about whether the customer has been contacted as part of the current marketing campaign or has been as part of a previous campaign. 
The objective is to predict whether a client will subscribe to a term deposit (the y variable). 
Business Objectives
1- Cost Reduction:
Telemarketing Cost: Bank pays internal employees or 3rd party call centers to conduct the marketing calls, therefore it is essential to target customer with higher chance of opening deposit Reducing the number of calls made to uninterested or unsuitable prospects Minimizing the number of unproductive calls helps in reducing wastage of human and financial resources.
2- Increased Conversion Rates | Increase ROI (Return On Investment)
3- Enhanced Customer Experience (CX):
Increase customer satisfaction rate (CSAT) Customers more likely to respond positively to calls that address their needs and interests
4- Strategic Alignment
Market Positioning
Enhance The Efficiency and Effectiveness of Telemarketing Campaigns
- Develop a predictive model using historical data.
- Identify key factors that influence customer decisions.
  - Provide actionable insights to marketing and sales teams.

Dataset Source
Original Source: Bank Marketing - UCI Machine Learning Repository
Dataset Name: banking target.csv

Dataset Structure
Number of Rows: 45,211
Number of Columns (Features): 17 (including the target variable)
Target Variable: y (has the client opened a Deposit account?)
Features Description
 
Demographic Data for Client:
1- age (numeric)
2- job (categorical)
3- marital: marital status (categorical, note: 'divorced' means divorced or widowed)
4- education: Education Level (categorical)
Banking Data for client
5- default: Failed to make a payment? (categorical)
6- balance: average yearly balance ( numerical)
7- housing: Own vs Rent (Do they have a housing loan)? (categorical)
8- loan: Do they have a loan with the bank or not? (categorical)
Field of Interest for client
Data about the calls from  this campaign:
9- contact: contact communication type, Contact Method, last contact (categorical)
10- month: last contact month of the year, Last Date of contact with the client (Month) (categorical)
11- day: last contact day of the week, Last Date of contact with the client (day) (categorical)
12- duration: last contact duration, last contact duration in seconds (numeric)
13- campaign:  number of contacts performed during this campaign and for this client (includes the last contact) (numeric)
Data about calls from *previous* campaigns:
14- previous:  number of contacts performed before this campaign and for this client. 0 means this client was not contacted in the previous campaign(numeric)
15- poutcome: outcome of the previous marketing campaign, previous campaign outcome (categorical) 
16- Pday:  number of days that passed by after the client was last contacted from a previous campaign(-1 means the client was not previously contacted)(categorical)
17- y:  Client opened a Deposit Account(categorical) (yes/no)

Target Variable
y: This is the target variable for this dataset, The Client opened a Deposit Account(categorical) (yes/no)
Data Cleaning
 Loading the Dataset: Load the dataset into your Python environment using pandas
Handling Missing(null) Values: Categorical features with the value "unknown" can be treated as missing values. These can either be imputed or treated as a separate category.
Check the datatypes: datatype and formatting need to be corrected in dataset.
Dealing with duplicated values:  Duplicated values need to be remove.

Exploratory Data Analysis (EDA)
The EDA isnthe  key insights into the distribution and relationships between features in the 'Bank Marketing' dataset. The findings will guide the model selection.
1. Data Distribution and Summary Statistics
….
2. Categorical Feature Analysis
Categorical variables like job, marital, education, contact, month, poutcome, etc., should be convert to numerical values to be able to  proceed with machine learning modeling.
3. Dummy Variables:  To numerically represent categorical variables with many nominal distinct values we can use dummy variables. A dummy variable is a binary variable that takes values of 0 and 1, where the values indicate the presence or absence of something. A categorical variable that has more than two categories can be represented by a set of dummy variables, with one variable being used to indicate the presense/absence for each category. 
4. Target Variable Distribution
y (Target Variable): …
5. Correlation Analysis and Relationship Between Features
 Collinearity and Multicollinearity: Collinearity refers to the situation when two independent variables are correlated with one another. Multicollinearity is the situation where one independent variable can be expressed as a linear combination of two or more other independent variables (in other words, the independent variables are in a linear relationship with each other).
6. Outlier Detection
Some numeric features like balance and duration may contain outliers that should be addressed during preprocessing.
7. Feature Transformation Suggestions

Numerical EDA:

Impact of  Duration feature:
the length of the last call with the customer) is highly correlated with the campaign's outcome. Longer call durations tend to have a much higher likelihood of success.
Previous Campaign Outcome (poutcome):
Customers who had a successful previous campaign outcome are more likely to subscribe to a term deposit again in the current campaign.
Effect of balance:
Customers with a higher account balance are more likely to subscribe to a term deposit. The relationship between account balance and term deposit subscription is positive.


Categorical EDA:

Majority of people who opened deposits are in management and technical positions.
Within each job category, students and retired people showed the highest deposit subscription rate (29% and 23%)
Blue-collar have lower deposit subscription rates.


For instance, targeting the "retired" group might be a good strategy to increase the success rate of a marketing campaign, while the "blue-collar" group may need a different approach to increase the subscription rate.


EDA 

Cellular contact is more effective in reaching customers than telephone contact.

Customers with a successful outcome in previous campaigns are much more likely to subscribe again.

Single individuals and those without loans (both personal and housing loans) are more likely to subscribe to term deposits.

Housing Loan and Personal Loan Influence:
Customers who do not have a housing loan are more likely to subscribe to a term deposit


Even though majority are calls are conducted in summer, looks like March, December and September can also be good considerations for calling clients. 

Correlation 
Pearson Correlation: Measures the linear relationship between two continuous variables.

Test Score (Accuracy):~79.6%
the model correctly predicted whether a customer would subscribe to a term deposit around 79.6% of the time.
Confusion Matrix: shows the actual vs. predicted class counts.
True Negatives (TN): 3,840 (Clients who were correctly predicted to not subscribe to a term deposit.)
False Positives (FP): 925 (Clients who were incorrectly predicted to subscribe, but did not.)
False Negatives (FN): 1,061 (Clients who were incorrectly predicted to not subscribe, but actually did.)
True Positives (TP): 3,802 (Clients who were correctly predicted to subscribe to a term deposit.)
The matrix shows a balance between true positives and true negatives, indicating that the model is reasonably balanced in predicting both classes. However, it still has some room to improve on false negatives (11.02%) and false positives (9.61%).
Classification Report :table shows metrics for each class (0 = no-deposit, 1 = deposit) and overall averages
Precision:
Class 0 (no-deposit): 0.78
Class 1 (deposit): 0.80
This means that 80% of the time when the model predicted a deposit, it was correct. A high precision for class 1 is important since the goal is to correctly identify deposit subscribers.

Recall:
Class 0: 0.81
Class 1: 0.78
Recall measures how well the model identifies all the actual positives. In this case, the model recalls 78% of the deposit subscribers, meaning 22% of actual deposit subscribers were missed (False Negatives).
F1-score:
Class 0: 0.79
Class 1: 0.79
The F1-score is the harmonic mean of precision and recall, balancing both. The equal F1-scores for both classes suggest that the model is handling both classes equally well.
Support:
The support represents the number of instances in each class. The dataset has 4,765 "no-deposit" and 4,863 "deposit" instances in the test set, showing a relatively balanced test set for evaluation
Overall Model Performance:
Accuracy (79.6%) indicates that the model is making correct predictions most of the time
Precision and Recall for the minority class (deposit) are fairly balanced, but there is still room to improve the recall (currently at 78%).
False Negatives are more problematic than false positives in this business case. Missing a potential client who is likely to make a deposit can be costly, so the focus should be on improving recall for the deposit class.


Recommendations for Improvement:
-Handling False Negatives
-other Models: Consider testing non-linear models like Random Forest or Gradient Boosting to improve performance on complex relationships in the data.
Modeling
Use various machine learning algorithms like Logistic Regression to predict the target variable y.


Evaluation: Evaluate model performance using metrics such as accuracy, recall, score


### Organization
#### Repository
* `data`
    - contains link to copy of the dataset (stored in a publicly accessible cloud storage)
    - saved copy of aggregated / processed data as long as those are not too large (> 10 MB)
* `model`
    - `joblib` dump of final model(s)
* `notebooks`
    - contains all final notebooks involved in the project
* `docs`
    - contains final report, presentations which summarize the project
* `references`
    - contains papers / tutorials used in the project
* `src`
    - Contains the project source code (refactored from the notebooks)
* `.gitignore`
    - Part of Git, includes files and folders to be ignored by Git version control
* `conda.yml`
    - Conda environment specification
* `README.md`
    - Project landing page (this page)
* `LICENSE`
    - Project license
#### Dataset
... Google Drive links to datasets and pickled models
### Credits & References
... Include any personal learning

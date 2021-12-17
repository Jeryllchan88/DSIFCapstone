# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) GA Capstone Project: Predicting P2P loan default to maximise risk adjusted ROI


### Background

Peer-to-peer (P2P) lending enables individuals to obtain loans directly from other individuals, cutting out the financial institution as the middleman and this sometimes known as "social lending". One of such companies is LendingClub in United States where they connect borrowers directly to investors. Borrowers would fill out an application detailing their credit history, loan details, employment status and other self-reported information by which Lending Club would assign a loan grade reflecting the quality of a loan. Potential investors would be able to view the details of various loan applications and make a final decision to invest in the loan.

### Problem Statement

The main object of P2P lenders are individual investors who want to get the best risk-reward return for their investment. Our aim for this project is to help P2P lenders decide on the which loans to invest in their portfolio to obtain the best risk-reward (Sharpe Ratio) return. 

### Datasets

The dataset used is from LendingClub [`LendingClub Website`](https://www.lendingclub.com/). The dataset is extracted from Kaggle and the data dictionary can be obtained from kaggle as well. [`LendingClub Dataset and Dictionary`](https://www.kaggle.com/ethon0426/lending-club-20072020q1)

### Data Dictionary

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Features</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>loan_amnt</td>
      <td>The listed amount of the loan applied for by the borrower. If at some point in time, the credit department reduces the loan amount, then it will be reflected in this value.</td>
    </tr>
    <tr>
      <th>1</th>
      <td>term</td>
      <td>The number of payments on the loan. Values are in months and can be either 36 or 60.</td>
    </tr>
    <tr>
      <th>2</th>
      <td>int_rate</td>
      <td>Interest Rate on the loan</td>
    </tr>
    <tr>
      <th>3</th>
      <td>installment</td>
      <td>The monthly payment owed by the borrower if the loan originates.</td>
    </tr>
    <tr>
      <th>4</th>
      <td>grade</td>
      <td>LC assigned loan grade</td>
    </tr>
    <tr>
      <th>5</th>
      <td>sub_grade</td>
      <td>LC assigned loan subgrade</td>
    </tr>
    <tr>
      <th>6</th>
      <td>emp_title</td>
      <td>The job title supplied by the Borrower when applying for the loan.*</td>
    </tr>
    <tr>
      <th>7</th>
      <td>emp_length</td>
      <td>Employment length in years. Possible values are between 0 and 10 where 0 means less than one year and 10 means ten or more years.</td>
    </tr>
    <tr>
      <th>8</th>
      <td>home_ownership</td>
      <td>The home ownership status provided by the borrower during registration or obtained from the credit report. Our values are: RENT, OWN, MORTGAGE, OTHER</td>
    </tr>
    <tr>
      <th>9</th>
      <td>annual_inc</td>
      <td>The self-reported annual income provided by the borrower during registration.</td>
    </tr>
    <tr>
      <th>10</th>
      <td>verification_status</td>
      <td>Indicates if income was verified by LC, not verified, or if the income source was verified</td>
    </tr>
    <tr>
      <th>11</th>
      <td>issue_d</td>
      <td>The month which the loan was funded</td>
    </tr>
    <tr>
      <th>12</th>
      <td>loan_status</td>
      <td>Current status of the loan</td>
    </tr>
    <tr>
      <th>13</th>
      <td>purpose</td>
      <td>A category provided by the borrower for the loan request.</td>
    </tr>
    <tr>
      <th>14</th>
      <td>title</td>
      <td>The loan title provided by the borrower</td>
    </tr>
    <tr>
      <th>15</th>
      <td>zip_code</td>
      <td>The first 3 numbers of the zip code provided by the borrower in the loan application.</td>
    </tr>
    <tr>
      <th>16</th>
      <td>addr_state</td>
      <td>The state provided by the borrower in the loan application</td>
    </tr>
    <tr>
      <th>17</th>
      <td>dti</td>
      <td>A ratio calculated using the borrower’s total monthly debt payments on the total debt obligations, excluding mortgage and the requested LC loan, divided by the borrower’s self-reported monthly income.</td>
    </tr>
    <tr>
      <th>18</th>
      <td>earliest_cr_line</td>
      <td>The month the borrower's earliest reported credit line was opened</td>
    </tr>
    <tr>
      <th>19</th>
      <td>open_acc</td>
      <td>The number of open credit lines in the borrower's credit file.</td>
    </tr>
    <tr>
      <th>20</th>
      <td>pub_rec</td>
      <td>Number of derogatory public records</td>
    </tr>
    <tr>
      <th>21</th>
      <td>revol_bal</td>
      <td>Total credit revolving balance</td>
    </tr>
    <tr>
      <th>22</th>
      <td>revol_util</td>
      <td>Revolving line utilization rate, or the amount of credit the borrower is using relative to all available revolving credit.</td>
    </tr>
    <tr>
      <th>23</th>
      <td>total_acc</td>
      <td>The total number of credit lines currently in the borrower's credit file</td>
    </tr>
    <tr>
      <th>24</th>
      <td>initial_list_status</td>
      <td>The initial listing status of the loan. Possible values are – W, F</td>
    </tr>
    <tr>
      <th>25</th>
      <td>application_type</td>
      <td>Indicates whether the loan is an individual application or a joint application with two co-borrowers</td>
    </tr>
    <tr>
      <th>26</th>
      <td>mort_acc</td>
      <td>Number of mortgage accounts.</td>
    </tr>
    <tr>
      <th>27</th>
      <td>pub_rec_bankruptcies</td>
      <td>Number of public record bankruptcies</td>
    </tr>
  </tbody>
</table>


### Summary of Analysis

During the initial EDA analysis, we noted and took actions for the following:

1. There are features which have null values. We dropped features which have more than 70% null values as we deemded such features with minimal value add to our model. For the rest of the features with null values, we replaced these null values based on our best understanding of the data. For those features with less than 10% null values, we delete those rows instead.

2. There are some forward looking features like next payment date, reocoveries and collection status which we have to delete as we generally will not have these features when selecting the loan for investment and removing these features will help prevent data leakage.

3. There are features with the wrong data type and thus we have to clean such features and convert to the right data type.

4. For ordinal features, we have to map to its numerical value. For nominal features, we perform one hot encoding.

5. As there are too many features and there are features which are highly correlated with one another, we used PCA to reduce the dimensions to speed up the ML algo without sacrificing much of the explanability. In this case, we retained 90% of the explanability.

6. The dataset is highly inbalanced as it contains more non defaulted loan than defaulted ones. Thus, we will used 'balance' weightage which uses the values of y to automatically adjust weights inversely proportional to class frequencies in the input data. We used gridsearch to select the best hyperparameters for each model selected.

### Model Evaluation

We trained and created 3 models (logistic regression, light GBM classifier, catboost classifier) based on the best hyperparameters for each model. The results for the 3 models are as follows:

|Model|Train AUC|Test AUC|Train_test AUC variance|Train precision|test Precision|Train recall|Test recall
|---|---|---|---|---|---|---|---|
|Logistic Regression|0.729|0.731|0.004|0.377|0.377|0.663|0.665
|CatBoostClassifier|0.735|0.731|0.005|0.373|0.369|0.693|0.687
|Light GBM Classifier|0.735|0.729|0.008|0.371|0.368|0.694|0.689

Based on the model evaluation above, the train and test AUC are very similar and all 3 models generalised quite well (no overfitting) based on the auc variance between the train and test data. 

However, we selected Light GBM Classifier as it is the fastest and has the best recall score (TP/(TP+FN)). We want the best recall score as we aimed to reduce the number of false negative (ie actual defaulted loan but predict as non-default) due to the high cost of false negative (investing in defaulted loan) which will affect our risk adjusted return (sharpe ratio). 

### Business Case

Without a model (baseline), we randomly selected 10,000 loans (assuming we want to invest in 10,000 loans in the portfolio) from the test dataset for investment. This selection process was iterated over 1000 times to obtain the annual return distribution, standard deviation and sharpe ratio.

We repeated the above process with the model selected and compare the results as below:

|Type|ROI|Standard Deviation|Sharpe Ratio
|---|---|---|---|
|Without model|2.31%|0.2|4.05
|with model|4.54%|0.14|21.71

From the results above, we can see that investors can significantly increase their risk adjusted annual returns (by around 5 times!) by using the model to select the P2P loans to invest.

### Conclusion

Due to time and power limitation of a personal latop, there are definitely much more work and improvement which can be done to the model.

1. We can try using longer time period and more features to train the model better. We can also run more grid search to better tune the hyperparameters for each model. 

2.  In this model, we did not take into account how time period will affect the features (such as annual income which will increases over time due to inflation) which are used to train the model. In addition, features such as grading and FICO score are highly dependent on how they are calculated where the methodology might change over time. Thus it will be useful to consider and study all these factors when building the model.

3. Similar to point 1, we can try using external features such as macoeonomic and market data which are known to be great predictor of bond default rate. This can be used to predict loan default as well.

4. Lastly, we should try using time series split and check if the model generalise well with future loans. Afterall, the main purpose of this model is to have the ability to predict future loan default rate.
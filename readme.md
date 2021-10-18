## Titanic Classification Model

**Data preparation, exploration, visualization**

Training data and test datasets are loaded. There are 12 columns in the training dataset.

Then I used isnull function to review how many values are missing in both datasets. There are a lot of null entries in age, and way too many in Cabin column (687/891 for training set). For that reason, the age data will need to be imputed later to fillna, and the Cabin column will be dropped for training.

I also grouped the data by gender and calculate mean survival, it is obvious that gender has large impact on whether one survived. Two histograms were made to display number of people in each Pclass and their age distribution as well as survival status (color coded). Three line-plots were also generated to display survival numbers for different passenger classes and embarked places. These plots show that there is a correlation between passenger class and survival, and embarked places and age are also related to survival.

A few unrelated or severely incomplete features were dropped: 'Ticket', 'Cabin', 'Name', 'PassengerId'. The Sex feature is transformed to numerical data by mapping Female:0 and Male:1. The null values in Age column are replaced by mean age and the empty Embarked entries are filled using the mode. The embarked feature is also mapped to integers, 'S': 0, 'C': 1, 'Q':2.

Finally, I used standard scaler to transform both training and testing datasets.

**Review research design and modeling methods**

The cleaned and transformed training dataset is used to train two different classification models: Logistic regression and Naïve Bayes classification. Sklearn module is imported and predictions were made using the trained models for the test dataset.

**Review results, evaluate models**

The cross-validation is applied, with 5-fold, and the scoring method is "roc_auc" -- area under the ROC curve. The mean score is calculated for both models. The logistic regression model's cross-validation mean AUC is 0.851 and the Bayes classification yield AUC 0.831, lower than the regression results. I also evaluated the coefficients in the logistic regression model for each feature. The coefficients show Pclass, Gender and Age are most important factors affecting survival. Gender is the most important factor.

I will recommend the logistic regression model, as it is straightforward to understand, and yield better prediction accuracies than the Bayes model. The coefficients can be directly associated with each evaluated factor (scaled) - the characteristics with larger abs(coefficient) have larger impact on chance of survival.

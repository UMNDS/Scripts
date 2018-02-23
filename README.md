# Scripts
## Pre-processing
First run the pre-processing script to load in the datasets (you might need to change the path to your own files).
As the data dictionary has variables that do not appear in the training dataset and vice versa, I only selected the columns from the training dataset that match the data dictionary. 
This script gets rid of columns in the training dataset that has more than 80% of the data missing (NA).
The rest of the missing data was imputed with the most frequently appeared value for each column, but feel free to try other methods of imputation (clustering, for example).
For the test dataset, I only selected the columns that were previously selected in the final training dataset.
The final training and test sets were written to csv files ('trainingpp.csv' and 'testpp.csv').

## Algorithms
Load in the pre-processed training and test datasets.
I split the training dataset into the training and test subsets for validation (30/70, feel free to try other ratios).
I've tried 3 classifiers (so far), Logistic Regression, Random Forest (500 trees) and SVM (RBF, parameters not tuned yet).
For each method, I first test the prediction error (using AUC as the metric) on the splitted training and test set, then test again using 5-fold cross-validation.

### AUC Results (so far)
- Logistic Regression: 0.8? 0.9? (not so good)
- Random Forest: 0.956

### Next steps
- Tune parameters for SVM
- Fit SVM model and get AUC score
- Can Logistic Regression be improved by feature selection? (took a lot of time, >400 predictors) Default regularization L2, how about L1?
- Try other classifier (XGBoost, maybe Neural Net?)
- Try ensembling
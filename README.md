# catboost_insurance_churn_rate

This repo is a complement to [my other git repository](https://github.com/ErfanEbrahimiBazaz/boosting_methods_insurance_dataset) where I trained models with XGBoost and lightgbm to predict churn rate of sample insurance clients. In this repo the same data set has been used to train a model with catboost.

## Catboost

1. Catboost has been used together with cross-validation.
2. scikit-learn's train_test_split is used to make 70% train, 15% validation and 15% test data. 
3. A model is trained with catboost for each kfold cross-validation.
4. f1_score is used to check model accuracy for each fold.
5. Feature importance is calculated for all the folds together.
6. With seaborn the features are sorted based on importance on target value and visualized.
7. Each trained model in each fold is saved seperately with pickle.
8. All saved models are loaded back and used to predict target value of test data set.
9. All models' predictions are averaged together and rounded to 0 if the average value is less than equal to 0.5 and 1 if otherwise is true.

## Results

1. A single catboost performed more accurately than the ensemble of 5 catboosts each trained by a different kfold.
2. Training a catboost model with all trained data with not split, improved the performance by testing it on the df_test data frame. The priblem with this method is, there is no way to be sure the final model is not overfit.

## Impact of different encodings on catboost model

Catboost can handle categorical data and does not require encoding. Still we check the impact of different encodings on catboost.
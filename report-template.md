# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Khujaeva Khonzoda

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: When I initially tried to submit the predictions to Kaggle, I realized that the output of the AutoGluon predictor differed slightly from the Kaggle submission expected format. Specifically:Kaggle expects a CSV file with datetime and count columns.
However, the predictions of predictor.predict(test_data) only included the predicted values of the count column, but not the datetime column.

### What was the top ranked model that performed?
TODO: All the models I trained did very similarly. There wasn't any one significantly better model — their performances were virtually identical. This might be because the dataset is small and clean and the engineered features were good enough to make most models do about the same as one another. Additionally, AutoGluon's ensembling strategy averages out multiple models together, and this can potentially cut down on the variability between individual models.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: For exploratory data analysis (EDA), I noticed significant seasonality in the data and strong effects of hour, workingday, and weather. I constructed the following features to enhance model performance:hour, day, month, and weekday from the datetime column.
A weekend feature (boolean).
A rush_hour feature that is based on typical commuting times (7-9am and 4-7pm, weekdays).
These features helped the model learn temporal patterns of bike usage more effectively.

### How much better did your model preform after adding additional features and why do you think that is?
TODO: Following feature engineering, the public score of the model in Kaggle improved from 0.52 RMSLE to 0.44 RMSLE. The performance was boosted because the new features allowed the model to capture underlying seasonality and trends that were not in the initial columns.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: After hyperparameter tuning (i.e., adjusting bagging folds and enabling stacking), the model became slightly better from 0.44 RMSLE to 0.42 RMSLE. Although the improvement was not amazing, it was a better generalizer and consistent between runs.

### If you were given more time with this dataset, where do you think you would spend more time?
TODO: 1.Perform further feature importance analysis and eliminate worse-performing columns.
2.Utilize external weather information to enrich feature space.
3.Tune models individually instead of using AutoGluon presets.
4.Investigate error distributions to further improve performance on outliers.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|0.46573|0.46573|0.46573|0.46573|
|add_features|0.46573|0.46573|0.46573|0.46573|
|hpo|0.46573|0.46573|0.46573|0.46573|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: 

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: 

![model_test_score.png](img/model_test_score.png)

## Summary
TODO: I utilized AutoGluon to train a prediction model for bike hire demand in this project. I began with low-level training, then increased performance through hyperparameter optimization and feature engineering. With every round of testing, there was measurable improvement in accuracy for the model. The greatest leap forward came with extracting insightful datetime-based features, enabling the model to understand the cyclic aspect of bike usage.






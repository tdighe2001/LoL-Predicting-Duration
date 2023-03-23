# LoL-Predicting-Duration
We examine the 2022 League of Legends data set and aim to predict the duration of a game. We generate 2 models: a simple baseline model that uses 2 features, a final model that incorporates feature engineering. We also conduct a fairness analysis test to check the parity of our model. 

##Framing the Model

##Baseline Model

Our model is a regression model that predicts the duration of a game. The data set is split into an 80:20 train and test split. For our baseline model, we considered the features league and goldspent. This is because we found them to have the highest correlation with game duration. Since league is a categorical variable, we one hot encoded it. The RMSE of the baseline model on the train set was 84.9 while the R^2 was 0.92. Meanwhile, on the test set, the RMSE was: 84.707 and the R^2 of the model was: 0.94. Since the two pairs of values are very similar with high R^2 values, we can conclude that the model is reliable and not an overfit/underfit

##Final Model

##Fairness Analysis

For our fairness analysis, we chose to compare how the model performed for games belonging to league ‘LCK CL’ vs other leagues. For our evaluation metric, we chose RMSE values and our test statistic is the difference between the RMSE values for the two groups. Thus, we have:

Null hypothesis: Our model is fair. The RMSE for LCK CL and other leagues are roughly the same, and any differences are due to random chance.
Alternative Hypothesis: Our model is unfair. The RMSE for LCK CL league is lower than for other leagues

For a significance level of 0.05, the p value we obtained was 0.6 (or consistently higher than 0.4). Thus, we fail to reject the null hypothesis and claim that our model is indeed fair!

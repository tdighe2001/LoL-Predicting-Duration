# LoL-Predicting-Duration

## Framing the Problem

We examine the 2022 League of Legends data set and aim to predict the duration of a game with a regression model. Our response variable is the duration of a game as we found it interesting to be able to predict a game's length based on factors in-game. At the time of prediction we have all the information of the game played except for the explicit gamelength. In this process, we generate 2 models: a simple baseline model that uses 2 features, a final model that incorporates feature engineering. We also conduct a fairness analysis test to check the parity of our model. To evaluate our model, we used the metrics of: [root squared mean error (https://en.wikipedia.org/wiki/Coefficient_of_determination) and [coefficient of determination (R^2)](https://en.wikipedia.org/wiki/Coefficient_of_determination). We chose RMSE to determine accuracy while heavily punishing larger errors and R^2 to determine how data foits the model, preventing overfitting.
 
## Baseline Model

For both models, the data set was split into an 75:25 train and test split. Our baseline model is a linear regression model that predicts the duration of a game. For our baseline model, we considered the features league(nominal) and goldspent(quantitative). This is because we found them to have the highest correlation with game duration. Since league is a categorical variable, we one hot encoded it. The RMSE of the baseline model on the train set was 84.9 while the R^2 was 0.92. Meanwhile, on the test set, the RMSE was: 84.707 and the R^2 of the model was: 0.94. Since the two pairs of values are very similar with high R^2 values, we can conclude that the model is reliable and not an overfit/underfit

## Final Model

For our final model, we used the features: patch, league, goldspent, monsterkills, damagetochampions. The reasoning for adding these features are listed below:
patch - The meta or strategy of League of Legends is constantly being changed by updates and patches and with the change of strategies games may be slower or quicker to end.
league - Strategies differ region to region so we want to keep that in account for our model.
goldspent - A general metric correlated to gamelength - Gold amount in a game increases over time.
monsterkills -  A general metric correlated to gamelength - Monsters are a resource and killed periodically in each game.
damagetochampions -  A general metric correlated to gamelength - Damage exponentially increases as players are able to buy more items later in the game.



## Fairness Analysis

For our fairness analysis, we chose to compare how the model performed for games belonging to league ‘LCK CL’ vs other leagues. For our evaluation metric, we chose RMSE values and our test statistic is the difference between the RMSE values for the two groups. Thus, we have:

Null hypothesis: Our model is fair. The RMSE for LCK CL and other leagues are roughly the same, and any differences are due to random chance.
Alternative Hypothesis: Our model is unfair. The RMSE for LCK CL league is lower than for other leagues

For a significance level of 0.05, the p value we obtained was 0.6 (or consistently higher than 0.4). Thus, we fail to reject the null hypothesis and claim that our model is indeed fair!

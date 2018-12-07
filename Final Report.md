# Generalized Linear Regression to Predict NFL Team Wins
### Introduction to your project, such as background and identified problems

We used a Generalized Linear Regression Model to predict the number of games won by different NFL teams in different seasons based on various statistics with data taken from the ESPN website. We chose this topic because we are both interested in sports and the increasing prevalence of analytics used in professional sports. Our initial problem was to find out which factors and which models best predict a team's performance, measured in the amount of games won, meaning our problem is a regression problem.



### Description of your data with necessary visualizations;

Data can be accessed [here](https://github.com/johnsaliba/480/blob/master/NFL%20TEAM%20DATA.xlsx)
<img src="https://github.com/cwolf51/480/blob/master/points%20scored%20and%20wins.png" width="800">
<img src="https://github.com/cwolf51/480/blob/master/distribution%20of%20wins.png" width="800">



### Trained model with necessary visualizations;

We used RapidMiner to create a Generalized Linear Regression Model, which can be accessed [here](https://github.com/johnsaliba/480/blob/master/Final%20Project%20Model.xml). We used the 'loop parameters' operator to run it with differing alphas and lambdas. The alphas ranged from 0 to 1, with the zero value representing ridge regression, the one value representing lasso regression, and the numbers in between representing a combination of the two. The lambdas ranged from 0.00000001 to 5 with the lower values representing less regularization and higher values representing more regularization.

<img src="https://github.com/johnsaliba/480/blob/master/outside%20loop.PNG" width="800">
<img src="https://github.com/johnsaliba/480/blob/master/insideloop.PNG" width="800">

### Justification of the selection of models and parameters;
gave us highest r2 value and was the most accurate regression model

### Conclusions

With our data, the Generalized Linear Regression Model is the best model. As the visualization below shows, the squared correlation values on both the testing and training data drop as lambda (penalty) increases. When alpha is closer to zero (ridge regression), this drop occurs more gradually and overfitting increases, and when alpha is closer to 1 (lasso regression), the drop occurs more quickly and overfitting decreases. The X axis value is alpha, the Y axis value is lambda, and the Z axis values are the squared correlations of the model's performances on the testing and training data. Refer the the legend below the visualization.

<img src="https://github.com/johnsaliba/480/blob/master/lambda%20alpha%20r%20square.PNG" width="800">
<p align="center">
<img align="center" src="https://github.com/johnsaliba/480/blob/master/lambda%20alpha%20r%20square%20legend.PNG" width="150">
</p>

Even when the model is performing at its best, it still overfits, but in some instances the squared correlations of the training and testing data were both close to 0.8, and in these instances the model was performing quite well, as you can see in the screenshot below. The left column shows the actual number of games the team won, and the right column shows the model's predicted number of wins. Many of me very close, but there were some outliers. One of them can be seen in the third row from the bottom. That team won six games, but the model's prediction was around 11.3, which is a huge disparity considering the teams play 16-game seasons. Conversely, there are many instances where the model is off only by a few decimal points. Additionally, the table in the screenshot below is sorted by which teams the model predicted to win the most games, so the team at the top is the one the model considered to be the best (in the test data set). Even though the model underestimated the amount of games that team would win, it predicted that it would win more games than any other team in the dataset, which turned out to be correct.
<p align="center">
  <img align="center" src="https://github.com/johnsaliba/480/blob/master/model%20predicted%20values.PNG">
</p>

### Limitations and Ways to Improve
There is no subset of factors that best predicts the number of games a team will win, because with linear regression, more factors make the model more accurate. This means that the best way to improve the performance of this model would be to add more features to the dataset. This solution would increase the squared correlation of the testing and training data, but it might not improve the overfitting problem. Our theory is that there are many events that occur in a football game that have a significant impact on the end result, but do not show up or are underrepresented in the statistics. Because of this, our model attributes too much value to the statistics included in our dataset, and it overfits when applied to new data. If somebody were to find a way to quantify those events that occur in football games that affect the outcome but do not heavily influence the statistics, they may be able to create a model that does not overfit. Some websites, such as [ProFootballFocus](https://www.profootballfocus.com/) conduct advanced analytics and predictions for NFL teams, and may have solved this problem, but their datasets and websites are not free, so we could not access them.


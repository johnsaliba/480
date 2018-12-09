# Generalized Linear Regression to Predict NFL Team Wins
### Project Introduction

We used a Generalized Linear Regression Model to predict the number of games won by different NFL teams in different seasons based on various statistics with data taken from the ESPN website. We chose this topic because we are both interested in sports and the increasing prevalence of analytics used in professional sports. Our initial problem was to find out which factors and which models best predict a team's performance, measured in the amount of games won, making our problem a regression problem.



### Description of Data

For our project we took the data from the ESPN website and looked and offensive and defensive statistics from all teams dating back to 2002. We only have data for the previous fifteen years because ESPN does not have the data for years prior on their website. We are not including statistics from the current year 2018 because the season is incomplete and we want the data to accurately reflect the predicted outcomes. We chose these statistice because they reflect a team's performance in a game and they are not derived from the number of wins they got in a season. A team could have good stats but lose many games and vice versa. 

For offensive statistics we looked at as points scored, rushing yards gained, passing yads gained, interceptions thrown, number of times sacked, and fumbles.  The offensive stats look at how well the offensive line of each team did in a season by points, rushing yards, and passing yards. The offensive stats also looked where the offense fell short by the number of sacks allowed and interceptions thrown. For defensive stats we looked at points allowed, rushing yards allowed, passing yards allowed, interceptions caught, sacks against the other team, and number of fumbles forced. The defensive stats analyze the strengths and weakness as well, with strengths being low rush and passing yards allowed, forced fumbles, and interceptions caught.

The following figures look at the statistics of points scored, passing yards gained, rushing yards gained, and how many wins a team had. We also have a histogram that looks at the number of wins a team got in any season and the how often a team got that many wins, showing that the number of wins is normally distributed. The data can be accessed [here](https://github.com/johnsaliba/480/blob/master/NFL%20TEAM%20DATA.xlsx).
<p align="center">
 <img src="https://github.com/cwolf51/480/blob/master/points%20scored%20and%20wins.png" alt="test" width="800">
 <img src="https://github.com/cwolf51/480/blob/master/pass%20yards%20allowed%20and%20wins.PNG" width="800">
 <img src="https://github.com/cwolf51/480/blob/master/rush%20yards%20allowed%20and%20wins.PNG" width="800">
 <img src="https://github.com/cwolf51/480/blob/master/distribution%20of%20wins.png" width="800">
</p>


### Trained Model

We used RapidMiner to create a Generalized Linear Regression Model, which can be accessed [here](https://github.com/johnsaliba/480/blob/master/Final%20Project%20Model.xml). We used the 'loop parameters' operator to run it with differing alphas and lambdas. The alphas ranged from 0 to 1, with the zero value representing ridge regression, the one value representing lasso regression, and the numbers in between representing a combination of the two. The lambdas ranged from 0.00000001 to 5 with the lower values representing less regularization and higher values representing more regularization.
<p align="center">
 <img src="https://github.com/johnsaliba/480/blob/master/outside%20loop.PNG" width="800">
 <img src="https://github.com/johnsaliba/480/blob/master/insideloop.PNG" width="800">
</p>
### Justification of the selection of models and parameters;
For our project we used the Generalized Linear Regression Model. When we first looked at the data we saw linear trends in the data, as seen in the models above, so we explored different types of linear regression to see which gave us the best test data results. The attribute we focused on was wins.  Through testing it gave us the highest squared correlation value on our testing data. Other regression models were significantly less effective. It was able to handle all of the different attributes we had and was the most accurate in predicting the number of wins based on the offensive and defensive data. 

For the model's parameters, we used a loop to run the model with alphas ranging from 0 to 1, and lambdas ranging from 0.00000001 to 5. We chose that range for the alphas because we wanted to use both lasso and ridge regression along with the values in between. We chose those lambda values because we wanted to see the model perform with different levels of regularization. We chose that range because it showed how the model's performance changes with different alphas and lambdas. We tried including lambda values above 5 in the range as well, but this did not show any new trends in the model's performance, and just made the chart more difficult to read, so it made the most sense to use lambda values only from 0.00000001 to 5.



### Conclusions

The Generalized Linear Regression model is the best to use with the type of data we collected. As the visualization below shows, the squared correlation values on both the testing and training data drop as lambda (regularization penalty) increases. When alpha is closer to zero (ridge regression), this drop occurs more gradually and overfitting increases, and when alpha is closer to 1 (lasso regression), the drop occurs more quickly and overfitting decreases. The X axis value is alpha, the Y axis value is lambda, and the Z axis values are the squared correlations of the model's performances on the testing and training data. Refer the the legend below the visualization.
<p align="center">
 <img src="https://github.com/johnsaliba/480/blob/master/lambda%20alpha%20r%20square.PNG" width="800">
 <img align="center" src="https://github.com/johnsaliba/480/blob/master/lambda%20alpha%20r%20square%20legend.PNG" width="150">
</p>



Even when the model is performing at its best, it still overfits, but in some instances the squared correlations of the training and testing data were both close to 0.8, and in these instances the model was performing quite well, as you can see in the screenshots below. The one immediately below this text shows that the average number of games teams in the test data set won is around 7.8, and the average number of wins the model predicted is around 8.06. This discrepancy is not a huge one, and since average amount of games won for all teams in the dataset is 8 (Each team plays 16 games in a season), 8.06 is not a bad average.
<p align="center">
  <img src="https://github.com/johnsaliba/480/blob/master/averages.PNG" width="800">
</p>
The image below this text shows a squared correlation table. It shows that in some of the iterations of the model the squared correlation of the testing and training data were both close to 0.8, which is a pretty good performance. It is not at all perfect, and the overfitting is still a problem, however.
<p align="center">
  <img src="https://github.com/johnsaliba/480/blob/master/r%20square%20matrix.PNG" width="800">
</p>

On the visualization below this paragraph, the left column shows the actual number of games the team won, and the right column shows the model's predicted number of wins. Many of them are very close, but there were some outliers. One of them can be seen in the third row from the bottom. That team won six games, but the model's prediction was around 11.3, which is a huge disparity considering the teams play 16-game seasons. Conversely, there are many instances where the model is off only by a few decimal points. The table in the screenshot below is sorted by which teams the model predicted to win the most games, so the team at the top is the one the model considered to be the best (in the test data set). Even though the model underestimated the amount of games that team would win, it predicted that it would win more games than any other team in the dataset, which turned out to be correct.

<p align="center">
  <img align="center" src="https://github.com/johnsaliba/480/blob/master/model%20predicted%20values.PNG">
</p>

### Limitations and Ways to Improve
There is no subset of factors that best predicts the number of games a team will win, because with linear regression, more factors make the model more accurate. This means that the best way to improve the performance of this model would be to add more features to the dataset. This solution would increase the squared correlation of the testing and training data, but it might not improve the overfitting problem. Our theory is that there are many events that occur in a football game that have a significant impact on the end result, but do not show up or are underrepresented in the statistics. Because of this, our model attributes too much value to the statistics included in our dataset, and it overfits when applied to new data. If somebody were to find a way to quantify those events that occur in football games that affect the outcome but do not heavily influence the statistics, they may be able to create a model that does not overfit. Some websites, such as [ProFootballFocus](https://www.profootballfocus.com/) conduct advanced analytics and predictions for NFL teams, and may have solved this problem, but their datasets and websites are not free, so we could not access them.


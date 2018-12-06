# Generalized Linear Regression to Predict NFL Team Wins
Introduction to your project, such as background and identified problems

We used a Generalized Linear Regression Model to predict the number of games won by different NFL teams in different seasons based on various statistics with data taken from the ESPN website. We chose this topic because we are both interested in sports and the increasing prevalence of analytics used in professional sports. Our initial problem was to find out which factors and which models best predict a team's performance, measured in the amount of games won.

Click the link to load a photo that illustrates the relationship between points scored and wins (https://github.com/cwolf51/480/blob/master/distribution%20of%20wins.png)


Click the [link] (https://github.com/cwolf51/480/blob/master/distribution%20of%20wins.png)
to load a photo that illustrates the distribution of wins by frequency 


Description of your data with necessary visualizations;

Trained model with necessary visualizations;

We used RapidMiner to create a Generalized Linear Regression Model. We used the 'loop' operator to run it with differing alphas and lambdas. The alphas ranged from 0 to 1, with the zero value representing ridge regression, the one value representing lasso regression, and the numbers in between representing a combination of the two. The lambdas ranged from 0.00000001 to 5 with the lower values representing less regularization and higher values representing more regularization.

<img src="https://github.com/johnsaliba/480/blob/master/outside%20loop.PNG" width="500">
<img src="https://github.com/johnsaliba/480/blob/master/insideloop.PNG" width="500">

Justification of the selection of models and parameters;

Conclusion and limitation of your research, and suggestions for improving your


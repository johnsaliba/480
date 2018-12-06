# Generalized Linear Regression to Predict NFL Team Wins
### Introduction to your project, such as background and identified problems

We used a Generalized Linear Regression Model to predict the number of games won by different NFL teams in different seasons based on various statistics with data taken from the ESPN website. We chose this topic because we are both interested in sports and the increasing prevalence of analytics used in professional sports. Our initial problem was to find out which factors and which models best predict a team's performance, measured in the amount of games won.



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

### Conclusion, Limitations, Ways to Improve

With our data, the Generalized Linear Regression Model is the best model.
As the visualization below shows, the squared correlation values on both the testing and training data drop as lambda (penalty) increases. When alpha is closer to zero (ridge regression), this drop occurs more gradually and overfitting increases, and when alpha is closer to 1 (lasso regression), the drop occurs more quickly and overfitting decreases.

<img src="https://github.com/johnsaliba/480/blob/master/lambda%20alpha%20r%20square.PNG" width="800">
<img src="https://github.com/johnsaliba/480/blob/master/lambda%20alpha%20r%20square%20legend.PNG" width="150">

The model at its best performance still overfits the data, but in some instances the squared correlations of the training and testing data were both close to 0.8, and in these instances the model was performing quite well.
 
<img src="https://github.com/johnsaliba/480/blob/master/model%20predicted%20values.PNG">
There is no subset of factors that best predicts the number of games a team will win, because with linear regression, more factors make the model more accurate.


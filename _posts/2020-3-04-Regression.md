---
published: true
title: Regression Analysis
category: Statistics
tags:
  - Statistics
  - Machine Learning
layout: post

---

**2020.03.04 Review for Regression:**
Statistical-Method/Regression;
**Programming**: Python

**Analyzing Diamonds Using Regression Models**

**I.         Abstract**

**1. Introduction**

Diamonds are the Precious stone consisting of a clear and colorless Crystalline
form of pure carbon. They are rare so they are considered to be very costly.
Moreover, the processing methods contributes a lot to their price as well. It is
an interesting topic to look into the price components and their relationships.

**2. Objective Statement**

In this topic, we are going to find out the relationships between the diamond
price and its attributes including but not limited to its carat, cut, color,
clarity and dimensions using various regression models.

First, we are going to look into the inter-relationship between each potential
variable from the given datasets. Then, we will test and find the suitable
independent variables to be set in the regression model. Finally, we intend to
figure out a regression model has the best performance on the price prediction.


**3. Statistical Procedure**

- Data virtualization for inspection (including data statistics and covariance
analysis)

-  Clean and modify the data for model input (including null data drop, outlier
detection and categorical data preprocessing)

- Set regression model (including data separation for training set and testing
set, multi regression models fitting)

- Test for goodness of fit.

- Test for model assumption (normality)

- Models comparison and conclusion

 

**4. Data Source Description**

The dataset Diamond comes from Kaggle and including the following attributes:
price, carat, cut, color, clarity and the dimension of the diamonds. It contains
53900 records in the raw dataset.

Data source: https://www.kaggle.com/shivam2503/diamonds

 

**II.        Data Inspection and Preprocessing**

In this section, we started to learn the data using virtualization technics and
then preprocessed the data into the proper condition for modeling use.

**1.  Data information**

The following table describes all the variables used in the analysis in this
topic. All of them have the same amount

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/1.png)

**2. Data Inspection**

##### a)     Numerical data

First, we look into the numerical data, including carat, depth, table, price, X,
Y and Z, 7 variables. We initially make 4 histograms for the first four
variables and then generate a 3-D plot for X, Y and Z since the X, Y and Z are
the dimensions of the diamonds.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/2.png)

From the histograms, we can have a general idea for these for variables’
information including their value range and the distribution of data for each
variable.

The following 3-D plot is using variables X, Y and Z. From the plot, we can see
the major points are plotted in the range X(0-10), Y(0-30), Z(0-10) and there
exist strong relationships among X, Y and Z. Also, we can detect some strange
points which are far from the major group. We will deal with these outliers in
the following data preprocessing section.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/3.png)

##### b)     Categorical data

There are three categorical variables in the dataset, including cut, color and
clarity. We are using histograms to count the records and box plots to see the
statistical relations for each of them with the variable price which is the one
we want to predict using the model.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/4.png)

From the table above we can see few people choose “Fair” as the cut type and the
majority choose the “Ideal” as the cut type. From the box plot we can conclude
that the cut selection seems not has strong relationship with the variable
price. The average prices are at the low level for all of the cut selection
though all of them have samples with very high price.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/5.png)

Similar as the variable “cut”. Here we can have the same conclusion that there
are not strong relationships between “color” and “price” form the box plot since
we can see the average level for all the groups are almost at the same level.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/6.png)

Again, for the categorical data “clarity”, as the same results for “cut” and
“color”, the average level are very close and at low level, at the same time,
all subgroups have the highest price at a very high level.

In conclusion, through the data virtualization on each variable including both
numerical and categorical data, we can have a general picture of the
distribution for each variable. For the 3-D plot designed for dimensions X, Y
and Z, we could know they have strong correlations with each other. What’s more,
through the box plots for three categorical variables, we conclude that these
three variables are weakly related with the price, though this conclusion need
to be further verification using the covariance analysis which will be
introduced in the next step.


##### c)     Data covariance

Here we first transformed the categorical data into processable types as
presented in the following section 3(c) and plot a covariance heat matrix for
better understanding on the relationships between these variables.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/7.png)

From the above covariance matrix, we can easily conclude that the dimension
variables X, Y and Z are highly related with each other, accordance with the
results we draw from the previous data inspection part. Furthermore, they have
an extremely strong positive covariance with the price, indicating they are the
key variables in the model to predict the price.

**3. Data preprocessing**

In this step, we first detected and removed all the records contains zero which
are useless records. Next, we detected and removed the outliers. The detail
reasons and steps will be further discussed in this chapter.

Then, for the categorical data, we transformed them into corresponding
processable types for regression modeling use.

##### a)     Remove the records contain zero

First, in our dataset, all data contain zero is meaningless which indicates a
useless record. Then, after detected, there are only totally 20 lines are with
zero, compared with 53,940 records, it is just a very small part. Considering
these two reasons, we removed all these 20 records.

##### b)     Clean the outliers

From the 3D-plot of the z-y-z size, we can conclude that most of the x-y-z are
increased or decreased with certain proportion, in another words which is
mentioned in the previous analysis, they are highly correlated. However, there
are some dots plotted outside the main group. We assume these cases are the
personalized special cases of diamonds in the market and it would not be the
good samples for us to fit the model in this topic. Thus, we seem these samples
as the outliers and we removed them.

Here we showed the comparison between before and after these outliers are
removed.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/8.png)

We can see, before the outliers are removed, some dots are lied outside the main
group, and the whole range for the y and z are (0-60) and (0-30), respectively.
After we clean the data, the range for y and z are (1-10) and (1-7),
respectively. So, the models we trained later with not be impacted by these
abnormal outliers, leading to a higher accuracy for the models.

##### c)     Categorical data transformation

Here, in order to fit the data in the regression model, we are using the typical
methods transferring all categorical data into their orthogonal formation. The
following diagrams show the variables used in the model after transformation.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/9.png)

d)     Data splitting for model training

Before next step we setup the regression models, we split the total data into
two parts for model training and testing use, 75% of the whole data are marked
as training and the 25% data are used for testing. The splitting is randomly
processed, meaning that each record has probability to be classified in either
training or testing group.

**III.      Regression Analysis, ANOVA and Model Checking**

In this section, in general, we are using different linear regression models to
illustrate the relationship between price(Y) and other variables(X). For each
model, price is predicted, ANOVA is used, and results are evaluated through R
square and adjusted R square. Besides, the residual plots and Q-Q plots are
employed to check the assumptions for the regression models.

Specifically, in the OLS (ordinary least squares) regression model part, we are
also using the sequential method (backward elimination) to select the variables
to figure out the final OLS model. And for other linear regression models, we
are continue using the variables selected by OLS model.

In the other linear regression methods part, popular used linear regression
models including Lasso Regression, Ridge Regression, Polynomial Regression and
ElasticNet Regression are used to see which one performs best for this problem.

Finally, a summary table is formed to collect all the results for the decision
maker to refer.

**1. Basic linear regression with sequential method for model selection**

##### a)     OLS model

Here we only show the core formula for the OLS model which is the objective
function for the Ordinary Least Squares method. We fit this model using Python
with the “sklearn” package. And all the same for the following each model.

For the OLS model, the objective function is:

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/20.png)

The OLS model is the basic components for most other linear regression model
including Lasso, Ridge and ElasticNet Regression. The objective function is only
to minimize the summation of the square errors.

##### b)     Sequential eliminating method for screening variables

So as to figure out which variable shall be included in the model and which
shall not, we introduced the backward eliminating method to screen all the
potential variables. Here the method is executed through Python with the
“statsmodels” package. In the process, ANOVA is used to evaluate the importance
of each variable, t test is applied, and p value is calculated accordingly.

From the following two tables we can see the process of the backward
elimination:

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/10.png)

In the step 1, we can have the conclusion that the variable “color_G” and
“cut_Ideal”  are not significant. And, “color_G” is more insignificant than
“cut_Ideal”. So, we eliminated the variable “color_G” in this step.Using the
same method, in the step 2, we eliminated the variable “cut_Ideal”. Here we come
to the final step for the eliminating procedure as shown below:

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/11.png)

From this final step, we first can see the whole model is tested significant
after F test. Then we can see that all the p value for the remaining variables
are less than 0.05. So, all the remaining variables here are showing
significance when we set 5% as the significant level.

After the backward elimination process, we eliminated two variables and totally
24 variables are tested with significance which could be used in the regression
models. Also, from the table we can see the R square and adjusted R square are
both 0.921 which looks pretty good.

Besides the above results and conclusions, we need to notice the warnings in the
above final step table that the smallest eigenvalue is very small, close to
zero, which means there are strong multicollinearity problem in this model. So
as to minimize the impact of the multicollinearity problem, later we are going
to use some other models including LASSO, ridge and ElasticNet regression
methods. These models are more robust to the multicollinearity.

##### c)     Model checking

Here we use the Q-Q plot and the residual plot to see if the model is following
the regression model assumption.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/12.png)

From the Q-Q plot and the residual plot shown above, we can see that the dots
are much likely holding some kind of trend cannot be explained by the OLS model.
Thus, we can conclude that the model normality assumption is not strictly
followed, indicating that this model may not be a good choice for this problem
though the goodness of fit performs well.
 
**2. Other Linear Regression methods**

##### a)     Lasso Regression / Ridge Regression / ElasticNet Regression

As we have mentioned above, the OLS model is not as robust as the Lasso, Ridge
and ElasticNet model when facing the multicollinearity problem. So, here we
introduced these methods and compare their modeling results.

i.         Model description

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/13.png)

The table above listed the main comparison among these four linear regression
methods. In general, the other three are all based on the OLS method. The Ridge
regression and the Lasso regression use their second term to control the
coefficients to make the model robust when there exists strong
multicollinearity. The ElasticNet method is just a combination of the Lasso and
the Ridge regression method.

ii.Goodness of fit

Here we show the results of three methods (Lasso, Ridge and ElasticNet). MSE, S,
R square and adjusted R square are calculated accordingly, and coefficients are
provided to see the difference among each method.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/14.png)

Through the coefficients from the Lasso regression model, we can see variable X5
has coefficient 0. And all the coefficients except the intercept are punished to
be as small as possible. As the result, on the other hand, the intercept is very
large.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/15.png)

In the Ridge regression model, we can see the all the coefficients including the
intercept are punished to be closer to each other than in the OLS and Lasso
model.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/16.png)

From the results shown above, we can conclude that the goodness of fit results
for the Lasso and the Ridge regression method is quite close and a little bit
lower than that in the OLS method. It is understandable since the former two
methods leveraging the coefficients at the cost of some accuracy. Also, it
indicates that the multicollinearity does not have much impacts on the goodness
of fit in this case. However, the ElasticNet method do not show good property of
goodness of fit.

iii.         Model checking

Here we draw the residual plots for these three methods. We could conclude that,
as the same of the conclusion we got for the OLS model, the model assumptions
are not quite well followed. Thus, these models may not suitable in this case.

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/17.png)


##### b)     Polynomial Regression

i.         Model description

Finally, after using OLS, Lasso, Ridge and ElasticNet regression method, we
choose to try the Polynomial regression since the former three methods do not
show great fitness.

In the polynomial regression, here we only take the quadratic case into
consideration due to the limitation of the computational capability. We tried to
do with cubic case, however, we cannot calculate out the feasible solutions.

 ii.         Goodness of fit

After calculation, the R2, adjusted R2 equals to 0.9708.

The mean absolute error is 397.75, the mean square error is 465307.42. Compared
with the results from other models we have used in this topic, it shows great
goodness of fit performance.

iii.         Model checking

The Q-Q plot and the residual plot are shown as below:

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/18.png)

From the plots, we can conclude that the normality assumption is well followed
for most range in the data though there are some unfitness could be detected at
the locations where the price is at the lowest and the highest level.

**3. Regression Summary**

a)     Results comparison

![](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Regression/19.png)

b)     Model selection

Based on the results showed above, finally, the polynomial regression model has
the best performance among all five approaches, from both two aspects. First,
the polynomial model has the highest goodness of fit, the R square and adjusted
R square are much higher than others. Besides, the normality check of the model
shows the polynomial regression holds the closet distribution with the model
normality assumption. 

**IV.       Conclusion**

In this topic, after inspecting and preprocessing the data, we used the
sequential selection method to eliminate the insignificant variables by
comparing their p values with the significant level after testing. We used ANOVA
to evaluate the model performance. Finally, we checked model through residual
analysis. We applied this process on several commonly used linear regression
models. In the end, we compared their results and provided a recommendation on
the model selection upon this dataset.

To accomplish our topic goal, Python are the platform for the coding work.
Package “Numpy” is used to preprocess the data and package “sklearn” and
“statsmodel” are used to do the computation, analysis and virtualization.

**V.        Reference**

[1] Walpole, R. E., Myers, R. H., Myers, S. L., & Ye, K. (2012). Probability &
statistics for engineers & scientists (9th edition.). Boston: Prentice Hall.

 [2] Shruti, L. (2018). Types of Regression and Stats in depth. Retrieved from
<https://www.kaggle.com/shrutimechlearn/types-of-regression-and-stats-in-depth>

 

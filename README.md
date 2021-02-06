# Diamond_price_prediction

***Assess what factors contribute to price of diamonds, and then building a predictive model (regression) to determine dollar value of diamonds***

![banner-img](/images/banner.jpg) 

## Introduction - What determines price of a diamond?

There are guidelines, or the 4 C’s, were established by the Gemological Institute of America and are the basis of diamond value estimation. They include:

![4c.png](/images/4c.png]

## Problem Statement

The dataset is from [here](https://www.kaggle.com/shivam2503/diamonds). We're trying to answer these questions:

- What features of the diamond contribute to the higher price of the Diamond?
- In this analysis, we included several features or characteristics to determine the price of Diamonds in a test dataset.

## Approach

I used and compared three machine learning algorithms to solve this challenge - Linear Regression, Decision Trees and Gradient Boosted Trees. The tree based models were used to assess feature importance. 

### Data Exploration and Cleaning

**Key questions answered in this analysis:**

- Colorless Diamonds (code D-F) generally cost more, is this evident from the dataset?
- Do flawless diamonds (IF) cost more than those with significant inclusions (I1,I2,I3)?
- Do ideal cuts fetch more price than fair ones?
- Are there any correlations present between the features?
- Are there any missing values?

In this process, the data was cleaned, and missing values were treated, where in only x, y, and z had missing values in them which were median imputed. Categorical variables (cut, clarity and color) were encoded using a custom ordinal encoder. Also, data was standardized and was divided 70% training set, 30% to testing set so that the it becomes ready for the next steps.

### Model Building

**Decision Tree**

Tree based models such as decision tree and gradient boosted can handle redundant and irrelevant features well hence keeping all the variables. Using the Decision Tree, we found the following features are most essential and in that order : 

- Depth
- x
- cut
- carat
- y

**Linear Regression**

- The features x, y and z were removed as they are highly correlated with carat. Amongst these 4 columns, carat shows the highest correlations with price.
- Carat contribute the most to price. 1 unit increase in carat will increase the price by $4151.19.
- High values for Depth decreases the value of the diamond. On researching we found that This is because Table and Depth have to be an ideal size to absorb light and refract the light inside to create a sparkle . However, if the Table and Depth of the diamond over the ideal percentage, it will have a poor light reflection capabilities. But that depends on cut as well.
- Clarity, Color and Cut add a positive value to the price as well.
- Regression Equation:

    ![eq](/images/eq.png)

**Gradient Boosted Trees**

- Gradient-boosted trees converts weak learners such as decision trees to strong learner.
- This is a slow algorithm but as we are using spark pipelines, this completes within few seconds for our data set.

### Performance

Based on the overall performance above, we can see that Gradient Boosted Trees has the best performance among these three models, with the highest R squared, and the lowest RMSE which stands for Root Mean Square Error (standard deviation of the residuals). Hence, predictions from Gradient Boosted Trees model are the closest ones to the actual observations.

![overall](/images/overall.png)

### Challenges

- The categorical variables in our dataset,  cut, color, clarity, are ordinal. For instance, color D is better than color E. Hence, we cannot just simply transfer each categories into dummy variables. We  tried using StringIndexer to encode different levels, however, it encoded the best category with the smallest index which reversed our goal. As a result, we built our own function to encode the categorical variables.
- In Linear Regression, the fitness of the Model does not depend solely on R-squared. The residual vs. fitted graph should be monitored as well. In our case, although our regression resulted in high R-squared, our residual vs fitted plot signals heteroscedasticity, suggesting the model can be improved.

# Conclusion

Based on the outputs from our final model, now we know that Carat and Table are the most important features of diamonds, although other features also influence the price.  Now we know there are not only 4C’s affect the price of diamonds, Depth and Table could also have influence on price of diamonds.
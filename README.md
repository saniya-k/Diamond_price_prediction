# Diamond_price_prediction
Dataset load (pyspark) , exploratory analysis of diamonds dataset and model building to predict price of diamonds 

In this analysis, I'm trying to predict :
a) What features of the diamond contribute to the higher price of the Diamond.
b) Price of diamonds in test data

Process : 
1. Dataset was divided into 70% train and 30% test
2. Missing values imputation
3. Only x, y, z have missing values, we changed ‘0’s into ‘null’ and imputed them with median. The minimum value for variable x, y, z was 0, which does not make sense because length, width and depth cannot be zero. This mean that '0' in the table implies missing value. The value '0’ then has been replace with 'null’ and them imputed with medium to fix this issue.
4. Did level encoding for the three categorical variables (cut, color, clarity) since there is an ordinal relationship within each variables.
5. Standardization : All variables after encoding the categorical variables.
6. Model Building : Three models were built and compared to solve the problem in hand
                  : Linear Regression, Decision Tree and Gradient-Boosted Trees.
7. Model Performance :
                    |   Linear Regression |   Decision Tree   | Gradient Boosted Trees
R-Squared           |       0.905         |   0.906           | 0.946
RMSE on Train       |     1229.05         |   1048.66         | 783.93 
RMSE on Test        |     1245.16         |   1232.56         | 929.19 
 

Based on the overall performance above, it can be seen that Gradient Boosted Trees has the best performance among these three models, with the highest R squared, and the lowest RMSE which stands for Root Mean Square Error (standard deviation of the residuals). Hence, predictions from Gradient Boosted Trees model are the closest ones to the actual observations.

8. Conclusion: By the results of the analysis we understand that Carat and Table are the most important features of diamonds, although other features also influence the price.
               Now we know there are not only 4C’s affect the price of diamonds, Depth and Table could also have influence on price of diamonds.

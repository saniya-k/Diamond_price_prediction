# Diamond_price_prediction
Dataset load (pyspark) , exploratory analysis of diamonds dataset and model building to predict price of diamonds 

In this analysis, I'm trying to predict what features of the diamond contribute to the higher price of the Diamond.

Process : 
1. Dataset was divided into 70% train and 30% test
2. Missing values imputation
3. Only x, y, z have missing values, we changed ‘0’s into ‘null’ and imputed them with median. The minimum value for variable x, y, z was 0, which does not make sense because length, width and depth cannot be zero. This mean that '0' in the table implies missing value. The value '0’ then has been replace with 'null’ and them imputed with medium to fix this issue.
4. Did level encoding for the three categorical variables (cut, color, clarity) since there is an ordinal relationship within each variables.
5. Standardization : All variables after encoding the categorical variables.
6. Model Building : Three models were built and compared to solve the problem in hand
                  : Linear Regression, Decision Tree and Gradient-Boosted Trees.

Based on the overall performance above, we can see that Gradient Boosted Trees has the best performance among these three models, with the highest R squared, and the lowest RMSE which stands for Root Mean Square Error (standard deviation of the residuals). Hence, predictions from Gradient Boosted Trees model are the closest ones to the actual observations.
Based on the overall performance above, we can see that Gradient Boosted Trees has the best performance among these three models, with the highest R squared, and the lowest RMSE which stands for Root Mean Square Error (standard deviation of the residuals). Hence, predictions from Gradient Boosted Trees model are the closest ones to the actual observations.
Based on the overall performance above, we can see that Gradient Boosted Trees has the best performance among these three models, with the highest R squared, and the lowest RMSE which stands for Root Mean Square Error (standard deviation of the residuals). Hence, predictions from Gradient Boosted Trees model are the closest ones to the actual observations.


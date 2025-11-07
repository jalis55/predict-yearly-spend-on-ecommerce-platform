
## Project Documentation

### Project Overview
This project aims to build a linear regression model to predict the yearly amount spent by customers of an e-commerce company. The goal is to understand the factors influencing customer spending and to predict future revenue based on customer characteristics.

### Goal
The primary goal of this project is to predict the 'Yearly Amount Spent' for customers based on various features in the dataset.

### Dataset
The dataset used is 'Ecommerce Customers.csv'. It contains information about customers, including their email, address, avatar, average session length, time on the app, time on the website, length of membership, and yearly amount spent.


### Exploratory Data Analysis (EDA) Findings

Based on the initial exploration of the dataset and the generated visualizations, the following key findings were observed:

**Data Overview:**

*   The dataset contains 500 entries with no missing values, as indicated by `df.info()`.
*   There are 8 columns: 'Email', 'Address', 'Avatar', 'Avg. Session Length', 'Time on App', 'Time on Website', 'Length of Membership', and 'Yearly Amount Spent'.
*   Numerical columns ('Avg. Session Length', 'Time on App', 'Time on Website', 'Length of Membership', 'Yearly Amount Spent') are of float64 data type. Categorical columns ('Email', 'Address', 'Avatar') are of object data type.
*   Descriptive statistics (`df.describe()`) provide a summary of the central tendency, dispersion, and shape of the numerical features. For instance, the average yearly amount spent is around 499.31.

**Key Relationships and Patterns:**

*   **Time on Website vs. Yearly Amount Spent:** The joint plot shows a weak positive correlation between 'Time on Website' and 'Yearly Amount Spent'. While there is a slight upward trend, the points are quite scattered, suggesting that time spent on the website alone is not a strong predictor of yearly spending.
*   **Time on App vs. Yearly Amount Spent:** The joint plot reveals a stronger positive correlation between 'Time on App' and 'Yearly Amount Spent' compared to 'Time on Website'. Customers spending more time on the app tend to spend more yearly.
*   **Pairplot:** The pairplot confirms the relationships observed in the joint plots and also highlights potential correlations between other feature pairs. Notably, 'Length of Membership' appears to have a significant positive correlation with 'Yearly Amount Spent'.
*   **Length of Membership vs. Yearly Amount Spent:** The linear model plot clearly demonstrates a strong positive linear relationship between 'Length of Membership' and 'Yearly Amount Spent'. This suggests that the longer a customer has been a member, the more they tend to spend annually.
*   **Other Relationships:** The pairplot also suggests some positive correlations between 'Avg. Session Length' and 'Yearly Amount Spent', and between 'Avg. Session Length' and 'Time on App'.

In summary, the EDA indicates that 'Length of Membership' and 'Time on App' are likely strong predictors of 'Yearly Amount Spent', while 'Time on Website' has a weaker relationship. 'Avg. Session Length' also shows some positive correlation with yearly spending and time on the app.


### Model Training

A Linear Regression model was chosen to predict the 'Yearly Amount Spent' as the exploratory data analysis indicated linear relationships between the target variable and some of the features.

The data was split into features ($\text{X}$) and the target variable ($\text{y}$). The features used for training the model were 'Avg. Session Length', 'Time on App', 'Time on Website', and 'Length of Membership'. The target variable was 'Yearly Amount Spent'.

The dataset was then divided into training and testing sets using `train_test_split` from `sklearn.model_selection`. A `test_size` of 0.3 was used, meaning 30% of the data was allocated to the testing set and the remaining 70% to the training set. A `random_state` of 121 was set to ensure reproducibility of the split.

The `LinearRegression` model was initialized and trained using the training data (`X_train` and `y_train`). The `fit()` method was used to train the model, allowing it to learn the coefficients for each feature that best predict the yearly amount spent.


### Model Evaluation

To assess the performance of the Linear Regression model, several standard regression metrics were used: Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and R-squared.

* ** Mean Absolute Error (MAE):** MAE is the average of the absolute differences between the predicted and actual values. It provides a direct measure of the average magnitude of the errors, without considering their direction.

*   **Mean Squared Error (MSE):** MSE is the average of the squared differences between the predicted and actual values. By squaring the errors, MSE penalizes larger errors more heavily than smaller ones.

*   **Root Mean Squared Error (RMSE):** RMSE is the square root of the MSE. It is in the same units as the target variable, making it easier to interpret than MSE. Like MSE, it gives more weight to larger errors.
*   **R-squared:** R-squared (coefficient of determination) measures the proportion of the variance in the dependent variable (Yearly Amount Spent) that is predictable from the independent variables (features). An R-squared value of 1 indicates that the model perfectly predicts the variance in the target variable, while a value of 0 indicates that the model does not explain any of the variance.

The calculated metric values for this model are:

*   **MAE:** 7.565
*   **MSE:** 86.527
*   **RMSE:** 9.302
*   **R-squared:** 0.9876

**Interpretation of Results:**

The MAE of approximately 7.57 means that, on average, the model's predictions for yearly amount spent are off by about $7.57. The RMSE of approximately 9.30 suggests that the typical error in the model's predictions is around $9.30, giving more weight to larger errors. Both MAE and RMSE are relatively low compared to the range of 'Yearly Amount Spent' values (which go up to around $765), indicating that the model's predictions are quite accurate.

The R-squared value of 0.9876 is very high. This means that approximately 98.76% of the variance in the 'Yearly Amount Spent' can be explained by the features included in the model ('Avg. Session Length', 'Time on App', 'Time on Website', and 'Length of Membership'). This high R-squared value suggests that the model provides an excellent fit to the data.


### Making Predictions on New Data

Once the Linear Regression model is trained, it can be used to predict the 'Yearly Amount Spent' for new, unseen customer data.

The prediction process requires the same features that were used to train the model: 'Avg. Session Length', 'Time on App', 'Time on Website', and 'Length of Membership'. For each new customer data point, the values for these four features are input into the trained model.

The output of the prediction is the estimated 'Yearly Amount Spent' for that specific customer, based on the relationships learned by the model during training.

As demonstrated in the code cell with cell_id `dc865da3`, new random data points were generated for the features ('Avg. Session Length', 'Time on App', 'Time on Website', 'Length of Membership'). The trained `lm` model was then used to predict the 'Yearly Amount Spent' for these new data points, and the results were displayed in a new DataFrame alongside the input features.


## Conclusion

This project successfully built and evaluated a Linear Regression model to predict the yearly amount spent by e-commerce customers. The primary goal was to understand the key drivers of customer spending and develop a predictive model.

The exploratory data analysis revealed that 'Length of Membership' and 'Time on App' had strong positive correlations with 'Yearly Amount Spent', while 'Time on Website' showed a weaker relationship. The Linear Regression model, trained on 'Avg. Session Length', 'Time on App', 'Time on Website', and 'Length of Membership', achieved excellent performance metrics. The high R-squared value of 0.9876 indicates that the model explains a significant portion of the variance in yearly spending. The low MAE (7.565) and RMSE (9.302) suggest that the model's predictions are, on average, close to the actual values. The coefficients of the model indicate that 'Length of Membership' has the largest impact on yearly spending, followed by 'Time on App', 'Avg. Session Length', and then 'Time on Website'.

Potential next steps for this project include:

*   **Exploring other models:** Investigate the performance of other regression algorithms such as polynomial regression, Ridge, Lasso, or tree-based models (e.g., Random Forest, Gradient Boosting) to see if they can provide even better predictive accuracy or offer different insights.
*   **Feature Engineering:** Create new features from existing ones or incorporate external data (e.g., demographic information, seasonal trends, marketing campaign data) to potentially improve the model's predictive power.
*   **Hyperparameter Tuning:** Optimize the hyperparameters of the chosen model(s) to further enhance performance.
*   **A/B Testing:** Design and conduct A/B tests based on the insights gained from the model to evaluate the impact of different strategies (e.g., encouraging more time on the app, loyalty programs) on yearly spending.
*   **Deployment:** If the model performance is deemed satisfactory, deploy the model to make real-time predictions on new customer data for business applications such as targeted marketing or customer segmentation.
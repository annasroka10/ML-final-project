# ML-final-project

## What is the dataset about?

The dataset contains information about people and their medical expenses (insurance charges). It has factors like:

Age (how old the person is)
Sex (gender)
BMI (Body Mass Index)
Children (how many children they have)
Smoker (whether they smoke or not)
Region (where they live)
Charges (the medical cost or insurance charge)
This data is used to predict how much a new person might pay for medical insurance based on their details.

Problem Statement:

What factors impact medical expenses the most?

We want to know which factors, like age or smoking, have the biggest effect on medical costs.

How accurate can we predict medical expenses?

We will build a machine learning model to predict how much someone will pay based on their data (age, smoking, etc.) and see how accurate the predictions are.

Dataset link: https://www.kaggle.com/datasets/rahulvyasm/medical-insurance-cost-prediction/data

#### Let's start this project!
##### 1. Checking for missing data
The dataset contains 2772 entries with no missing values across 7 columns.
##### 2. Preprocessing
 - Converting Categorical Features to Numerical
 - Checking correlation between Dependencies of Medical Charges![Dependencies of Medical Charges](https://github.com/user-attachments/assets/7a28cdf3-0580-43ec-bc04-8874d8462bb2)

The heatmap above shows that the columns sex, children, and region have little to no correlation with medical charges, suggesting that these factors have minimal impact on the charges.

The columns age, bmi, and especially smoker show a stronger correlation with charges. Specifically, smoker has a very strong positive correlation.

- Running some extra barplots to show age vs Charge and Smoker vs charge.
![Age vs Charge](https://github.com/user-attachments/assets/4b873ca1-67de-49e5-a967-775d2380de1c)
![Smoker vs Charge](https://github.com/user-attachments/assets/3e331f37-c3ae-47f2-b110-5ed4975ed081)
From the above we can clearly see that smokers and older people pay more for their medical insurance.

##### 3. Splitting Datasets to Train and Test
In machine learning, particularly in linear regression, splitting the dataset into training and testing sets is essential for evaluating model performance.
The goal is to train the model on one portion of the data (training set) and then test its performance on unseen data (testing set).
Helps to prevent overfitting (where the model memorizes the data instead of learning patterns).
Ensures that the model generalizes well to new, real-world data.

##### 4. Data Normalization
Removing rows with NaN.

##### 5. Linear Regression

We got the following results:

R² Score: 0.74

RMSE: 6319.27

MAE: 4160.25

R² Score (0.74)

The model explains 74% of the variance in the target variable (charges). This indicates a moderately strong fit—not perfect, but the model captures a significant portion of the data's variability.

Root Mean Squared Error (RMSE: 6319.27)

RMSE represents the average prediction error in absolute terms. A high RMSE suggests that, on average, the model’s predictions deviate by about $6,319 from the actual charges. Whether this is acceptable depends on the typical range of charges in your dataset.

Mean Absolute Error (MAE: 4160.25)

MAE is another measure of error, but it doesn’t square differences like RMSE. On average, the model’s predictions are off by about $4,160, which is a relatively large error.

The model captures most of the variance in charges (R² = 0.74), meaning it's fairly predictive. However, the errors (RMSE and MAE) are quite large, suggesting the model may struggle with high variability in charges. We might improve performance by:

Adding more relevant features (e.g., interactions, non-linear transformations)

Trying different models (e.g., Random Forest, Gradient Boosting)

Checking for outliers that might be increasing error.
![Predicted vs Actual Charges](https://github.com/user-attachments/assets/5bb0cc92-87fd-4d9f-b0b2-132351860ed7)
This regression plot (regplot) visualizes the relationship between actual charges (x-axis) and predicted charges (y-axis) for a model. Here are my observations:

General Fit of the Model The red regression line indicates the model’s trend in predictions. The points closely following the line suggest the model is making fairly accurate predictions. However, some noticeable deviations from the line suggest certain areas where predictions are less reliable.
Outliers & Variability Several points far from the regression line (especially on the upper right and lower parts) suggest model errors or high variance in certain predictions. This could indicate outliers or factors the model isn’t capturing well.
Homoscedasticity (Constant Variance) The scatter points appear more dispersed at higher actual charge values. This suggests heteroscedasticity, meaning prediction errors increase for higher charges. The model might struggle to predict high medical charges accurately.
Possible Improvements Feature Engineering: Consider adding more relevant features to capture variability. Transforming Target Variable: Log or Box-Cox transformations might help if the charge values are highly skewed. Using Non-Linear Models: If patterns are non-linear, tree-based models (Random Forest, XGBoost) could improve performance.


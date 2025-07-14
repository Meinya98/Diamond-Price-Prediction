# Diamond Price Prediction
A regression problem to create a model for predicting diamond prices using tree-based models
### 1. Exploratory Data Analysis (EDA)
Workflow:
- Dataset import and basic statistics describing
- Load the dataset 
- Use .info() and .describe() for basic statistics description
- Use .duplicated() to check duplicated data
- Delete index column
\
#### Data exploration (numerical):
- Visualize with a histogram to see skewed features
- Use VarianceThreshold() to select non-quasi-constant features
- Visualize with a heatmap correlation to select moderate to highly correlated features to the target (prices)
- Visualize with a scatterplot to detect and delete outliers
\
#### Data exploration (categorical):
- Merge with the numerical data
### 2. Feature Engineering
Workflow: 
- Use OrdinalEncoder() for categorical data encoding, since the categorical features have order
- Log-transform the prices features to reduce the range and skewness
- Use train_test_split() with stratification to prevent set imbalance
- Use StandardScaler() for scaling
- Variance Inflation Factor was checked, and multiple correlated features were detected, but were not removed due to the small features available
    - Use a tree-based model, because it is more robust to multicollinearity
### 3. Modeling
Workflow:
- Compare basic regression model, choose the highest R-square
- Highest R-square (random forest, XGB, LGBM) were tuned multiple times using GridSearchCV()
- Training was performed using the best hyperparameters for each of the model
- Model was evaluated using multiple metrices, both in log-space and real-space
- Cross-validation was performed
### 4. Deployment ([Streamlit App](https://diamond-price-deployment-qmza86kdxyd2spi9gl9cui.streamlit.app/)) ([Resource Code](https://github.com/Meinya98/Diamond-Price-Deployment))
Workflow:
- Create "app.py" for the Streamlit deployment, initially containing all functions
- Modularize each function for easier evaluation

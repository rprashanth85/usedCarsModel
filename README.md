# usedCarsModel

# Link 
  https://github.com/rprashanth85/usedCarsModel.git

# Overview
  Goal is to find out what factors make a car more or less expensive. Based on the analysis provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car.After understanding, preparing, and modeling your data, write up a basic report that details the primary findings. Based on the report used car dealers will be fine-tuning their inventory.

# Data
  Data for this analysis is from kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing.

# Data Investigation 
  
  1.  Data Description:
      - Checking for mean, standard deviation, minimum, and maximum statistics on numerical columns to identify useful columns for data modeling.
  2.  isNull Check:
      -  Removing rows or columns with excessive null values as they are not useful for training a model.
  3.  Data Duplication:
      - Identifying genuine duplicates.
  4.  Data Inconsistency:
      -  Exploring possibilities to eliminate inconsistent columns or rows.
  5.  Heat Map/Correlation:
      -  Analyzing correlations and relationships between numerical variables to avoid redundancy and highlight significant correlations.
    
# Actions on Data Investigation

  1.  Feature/Row Drop:
       - Original Data Set had data from 1900 to 2022 car make Year. Also based on the 'price' and 'odometer' distribution it is was very clear that log price range from 6 to 13 and log odometer range from 7 to 13 had a good distribution list. If the data is skewed, model created will not provide accurate results. So based on initial analysis filtered the data to above range.
       - After that removed rows with null values in 'Cylinders'. Cylinders is one of the most important features in this data set.
       - Also dropped columns like paint_color, VIN, size and model. I was able to get a pretty good data set. 
  2.  Replacing / Merging Column Values:
       - Imputed values for column 'title_status', 'fuel', 'transmission', 'condition', 'manufacturer', 'type', 'drive'.
  3.  Object to Numeric Conversion:
      - Converted cylinders to a numeric field for faster performance.
  4.  Log Transformation:
      - Converted price and odometer to log values to avoid skew.
    
# Data Visualization

  1.  Libraries Used:
      - Plotly, Seaborn, Matplotlib, Pandas, IPython display, sklearn clusters, model selection, preprocessing, column transformer, cross validation, linear model, feature selection, pipeline, metrics, and inspection.
  2.  Plots used for analysis.
      -  Venn, Bar, Histogram and Stacked Bar Plots to compare drivers.
  3.  Display:
      -	Used display image function where seaborn visualizations were employed.
  4.  Clustering:
      -	Used KMeans and DBSCAN to group rows. As the nuerical features were very less there PCA was not necessary to use find out Principal Components.
  5.  Permutation Importance:
      -	Towards the end created charts to compare the feature importance.

# Chart Analysis and Hypothesis

  1.  # Drive, Transmission, and Cylinders
      **Observation**: Cars with automatic transmission and 4WD drive types dominate the market, particularly those   with 6 or 8 cylinders.
      **Recommendation**: Maintain a strong inventory of cars with automatic transmission and 4WD drive types.            Especially those with 6 or 8 cylinders, as they make up a large portion of the inventory.
  
  2.  # State and Region¶
      **Observation**: Certain states like California (CA) and Florida (FL) have significantly higher car counts compared to other states, reflecting higher market activity in these regions.
      **Recommendation**: Invest more heavily in states like CA and FL by focusing marketing and sales efforts there. Analyze regional preferences to further optimize the types of cars offered in each state.
  3.  # Condition, Fuel Type, and Transmission
      **Observation**: Cars in good condition with gasoline fuel and automatic transmission dominate the dataset.Cars in excellent and like new conditions also command a considerable presence, indicating demand for well-maintained cars.
      **Recommendation**: Maintain a majority of cars in good to excellent condition, focusing on gasoline-fueled, automatic transmission vehicles. Consider expanding the selection of hybrid or electric vehicles to meet emerging market demands.
  5.  # Manufacturer¶
      **Observation**: Luxury brands like Ferrari, Aston Martin, and Tesla have significantly higher average prices, with many mainstream brands like Ford, Chevrolet, and Toyota offering lower-priced vehicles.
      **Recommendation**: Tailor inventory by diversifying between high-end luxury cars and affordable mainstream options. This will allow the dealership to cater to a broader customer base, balancing higher margins from luxury cars with higher sales volume from more affordable options.

# Modeling
  Created a basic linear regression model and all inclusive model(pointed below) to try various combinations of parameters and data set.
  1.  Column Transformer:
      - Used Polynomial Features on Numerical features with various degrees pass as parameters
      - Used OneHotEncoder on Categorical Features
  2.  Sequential Feature Selection
      -  Used Linear Regression with varying features to select
  3.  RFE:
      -	Used Lasso Regression with varying features to select.
  4.  Ridge:
      -	Used Ridge in TransformedTargetRegressor.
  5.  Pipeline:
      -	Used Pipeline to include Step 1- 4.
  6.  GridSearchCV:
      -	Set the param grid for various regressors above and passed to GridSearchCV to select top 5 features.
  7.  Parameters:
      -	Varying parameters for Ridge(alpha), Polynomial Feature(degree), SFE and RFE(features to select).
  8.  Mean Squared Errors:
      -	MSEs were calculated for all three models and used for model comparison.
  9.  Best Models:
      -	From the pipeline selected best estimator and model for further analysis.
  10.  Permutation Importance:
      -	Towards the end created charts to compare the feature importance.

# Evaluation
  Based on the training and test MSEs from different models it is very clear that best model is found with    Ridge parameter alpha: 0.1, applied Polynomial Feature degree: 2 only on numerical columns.
  Further from the Permuation Importance calculated based on the above models shows that 4 features     would contribute to the model (year, odometer, cylinders, fuel).

# Conclusion and Next Steps
  Initially for this analysis I dropped column size. May be including size of the car could result in different MSEs and feature selection. We should try this 

  Mapping the coefficents from the best model to the features shows which feature contributes positively  and which features contributes negatively.

  Apply multiple cross validation techniques and Huber Loss to minimize loss. 

  Apply Mean Absolute Error, Root Squared Mean Error to figure out error rate between training and test data. Also between models.

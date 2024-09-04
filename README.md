# usedCarsModel


# Link 
  https://github.com/rprashanth85/usedCarsModel.git


# Overview

The goal of this analysis is to identify the key factors that influence the pricing of used cars. By understanding these factors, we can provide actionable recommendations to used car dealerships, allowing them to optimize their inventory and pricing strategies based on consumer preferences. This report will guide dealerships in fine-tuning their stock to better meet market demands.


# Data

The dataset, sourced from Kaggle, originally contained information on 3 million used cars. For efficiency and processing speed, a subset of 426,000 cars was used for the analysis.


# Data Investigation

1. Data Description
    Analyzed key statistics (mean, standard deviation, minimum, maximum) of numerical columns to identify useful variables for modeling.

2. Handling Missing Data
    Removed rows/columns with excessive null values to ensure data integrity and model reliability.

3. Data Duplication
    Identified and eliminated any genuine duplicate records.

4. Addressing Data Inconsistencies
    Removed or corrected inconsistent entries to improve data quality.

5. Correlation Analysis
    Used a heatmap to identify correlations between numerical variables, aiming to avoid redundancy and highlight significant relationships.


# Actions on Data Investigation

  1. **Feature/Row Drop**
	    Filtered the data to cars made between 1900 and 2022.
	    Dropped rows with null values in the ‘Cylinders’ column, as it is a critical feature.
	    Excluded columns like paint_color, VIN, size, and model to streamline the dataset.
  2. **Imputation and Merging**
  	  Imputed missing values for ‘title_status’, ‘fuel’, ‘transmission’, ‘condition’, ‘manufacturer’, ‘type’, and ‘drive’ to maintain data completeness.
  3. **Data Conversion**
    	Converted the ‘cylinders’ column to a numeric format for better model performance.
  4. **Log Transformation**
    	Applied log transformation to the ‘price’ and ‘odometer’ columns to correct skewness and ensure a more normal distribution.


# Data Visualization

  1.  **Libraries Used**
       Plotly, Seaborn, Matplotlib, Pandas, and Scikit-learn libraries were utilized for visualization and analysis.
  2.  **Visualization Techniques**
		  Created Venn diagrams, bar charts, histograms, and stacked bar plots for comparative analysis.
	    Seaborn visualizations were employed to explore feature relationships.
  3.  **Clustering**
      Used KMeans and DBSCAN clustering to group data. Since the number of numerical features was limited, PCA was not required.
  4.  **Feature Importance**
      Conducted Permutation Importance analysis to determine the most significant features affecting price.


# Chart Analysis and Recommendations

  1. **Drive, Transmission, and Cylinders**
	Observation: Cars with automatic transmission and 4WD dominate the market, especially those with 6-8 cylinders.
	Recommendation: Prioritize inventory with automatic transmission, 4WD, and 6-8 cylinder vehicles to meet demand.

  2. **State and Region**
	Observation: States like California and Florida have higher car listings, indicating active markets.
	Recommendation: Focus marketing and inventory investments in high-activity states like CA and FL.

  3. **Condition, Fuel Type, and Transmission**
	Observation: Gasoline-fueled cars in good or excellent condition with automatic transmissions are prevalent.
	Recommendation: Maintain a majority of well-maintained, gasoline-fueled cars. Expand the selection of hybrid and electric vehicles to capture emerging trends.

  4. **Manufacturer**
	Observation: Luxury brands (Ferrari, Tesla, etc.) have higher price points, while mainstream brands offer affordable options.
	Recommendation: Balance inventory between luxury and affordable cars to cater to a broad customer base.


# Modeling

   **Model Selection**
    Created several models to explore various feature combinations:
    Column Transformer: Applied Polynomial Features to numerical and OneHotEncoding to categorical features.
    Sequential Feature Selection: Used Linear Regression to select the most impactful features.
    Recursive Feature Elimination (RFE): Applied Lasso Regression to refine feature selection.
    Ridge Regression: Implemented Ridge Regression in a TransformedTargetRegressor.
    Pipeline: Combined the above methods into a pipeline for streamlined modeling.
    GridSearchCV: Tuned parameters for various models and selected the top 5 features.

   **Performance Metrics**
    Calculated Mean Squared Errors (MSE) for all models to assess performance.
    Best performance was achieved with Ridge Regression (alpha: 0.1) and Polynomial Features (degree: 2).

   **Feature Importance**
    The most important features were determined to be year, odometer, cylinders, and fuel type.


# Evaluation
    The best-performing model was Ridge Regression with alpha: 0.1 and Polynomial Features of degree 2 for numerical columns.
    Feature importance analysis revealed the most influential variables were year, odometer, cylinders, and fuel.


# Conclusion and Next Steps
    Future analysis could benefit from including the ‘size’ column, which was initially dropped, to see if it impacts model performance.
    Further experimentation with cross-validation and Huber loss could improve the robustness of the model.
    Exploring additional error metrics such as Mean Absolute Error and Root Mean Squared Error will provide deeper insight into model accuracy.

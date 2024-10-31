# Energy-Consumption-Analysis

Dataset includes Columns: Date, Energy usage(kWh), Lagging Current reactive power (kVarh), Leading Current reactive power(kVarh), tCO2(CO2) (ppm), Lagging Current power factor (%), Leading Current Power factor(%), Number of Seconds from midnight, Week status (Weekend (0) or a Weekday(1)), Day of week (Sunday, Monday... ,Saturday), Load Type (Light Load, Medium Load, Maximum Load)<br />

 
Primary Insights:<br />
The dataset is recorded in the year 2018. The class label is a multi-class classifying the Load Type - Light Load, Medium Load, and Max Load. Here are the primary insights about the dataset -<br />
1. The data is recorded at 15 min intervals daily.<br />
2. No null/missing values<br />
3. Temporal trends are observed, i.e, Energy consumption varied over time, and periods of highest energy consumption are identified, and examined the load distribution patterns.<br />
<br />
Data Analysis:<br />
Exploratory Data Analysis (EDA) is a process of identifying general patterns, and general assumptions in the data. Here are the following primary insights from the data. -<br />
A. Outliers detection - Most of the numerical columns have outliers. The columns Leading_Current_Reactive_Power _ kVarh , and Leading_Current_Power_Factor have 22 % outliers deviating significantly from the overall pattern. These outliers look deviating from the data and not removing them will be helpful for the model to identify the right patterns to predict energy consumption.<br />
B. Identifying important variables - I infer that numerical values describing the Usage kWh, Reactive power, CO2 emissions, and Current power Factor are important columns that will determine the power consumption.<br />
C. Underlying Assumptions and observations - Created informative visualizations like scatter plots to communicate key findings:<br />
• Usage kWh has positive correlation with Lagging_Current_Reactive_Power<br />
• Leading_Current_Power_Factor has negative correlation with Leading_Current_Reactive_Power<br />
• The dataset has imbalance class labels Light Load: 18072, Medium Load: 9696, Maximum Load: 7272 • As expected, the steel factory has lighter loads in the weekends<br />
• The dataset is recorded at 15 min intervals for the year of 2018.<br />
D. The object datatype are converted to numerical/float datatypes for feature engineering and model training.<br />
Data Cleaning is a process of removing empty/null values, and inconsistencies in the data. This data do not have any null values for all the columns.<br />
Feature Engineering & Transformation is a process of transforming and creating new features to improve the model performance.<br />
• High correlation values are removed in the dataset (Lagging_Current_Reactive_Power due to strong correlation with Usage
kWh).<br />
• Transformed Categorical to numerical features with One-hot encoding, and Label encoding. For example, Weekday, Weekend
column, Load_Type and fed them to model training.<br />
• Since the data is a time series data, I have created rolling window features on delta of rows between 15 min interval present in
the data. For example, delta_Leading_Current_Reactive_Power_kVarh_max, delta_Leading_Current_Reactive_Power_kVarh_min, delta_Usage_kWh_max, delta_Usage_kWh_min. The window size was set to 4 to identify the max, and min of all delta within one hour sliding window. This will help to capture the pattern of changing values within an hour. This feature engineering process will help the model to find the right patterns for prediction.<br />
• Irrelevant Categorical features are removed<br />

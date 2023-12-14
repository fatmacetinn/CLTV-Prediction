# CLTV-Prediction
![image](https://github.com/fatmacetinn/CLTV-Prediction/files/13666935/cltv.docx)

Dataset Overview
The dataset consists of historical shopping behaviors of customers who made their most recent purchases in 2020-2021 via OmniChannel (both online and offline shopping). Key data points include:
•	master_id: Unique customer number
•	order_channel: The channel through which the shopping was done (Android, iOS, Desktop, Mobile, Offline)
•	last_order_channel: The channel of the last purchase
•	first_order_date: Date of the first purchase
•	last_order_date: Date of the last purchase
•	order_num_total_ever_online: Total number of online purchases
•	order_num_total_ever_offline: Total number of offline purchases
•	customer_value_total_ever_offline: Total amount paid in offline purchases
•	customer_value_total_ever_online: Total amount paid in online purchases
•	interested_in_categories_12: List of categories shopped in the last 12 months
Data Preparation
•	Load and copy the dataset from flo_data_20K.csv.
•	Define functions outlier_thresholds and replace_with_thresholds for handling outliers.
•	Handle outliers in order_num_total_ever_online, order_num_total_ever_offline, customer_value_total_ever_offline, and customer_value_total_ever_online.
•	Create new variables to represent the total number of purchases and the total expenditure.
•	Convert date columns to datetime type.
Creation of CLTV Data Structure
•	Set the analysis date as two days after the last purchase date in the dataset.
•	Create a new CLTV DataFrame with customer_id, recency_cltv_weekly, T_weekly, frequency, and monetary_cltv_avg.
Building BG/NBD and Gamma-Gamma Models, and Calculating 6-month CLTV
•	Fit the BG/NBD model to predict expected purchases for 3 and 6 months, adding these as exp_sales_3_month and exp_sales_6_month to the CLTV DataFrame.
•	Fit the Gamma-Gamma model to estimate the expected average value and add it as exp_average_value.
•	Calculate 6-month CLTV and add it to the DataFrame. Standardize the CLTV values and create a scaled_cltv variable.
•	Observe the top 20 customers with the highest CLTV.
Segmenting Customers Based on CLTV
•	Segment all customers into four groups based on 6-month standardized CLTV and add the segment names to the dataset as cltv_segment.
•	Provide short-term action recommendations for two selected segments to the management.
Function for the Entire Process
The entire process is encapsulated in a function named create_cltv_df, which takes the original DataFrame as input and returns the CLTV DataFrame with all necessary calculations and segmentations.

![image](https://github.com/fatmacetinn/CLTV-Prediction/assets/142151744/9af75f5d-980c-474d-9e17-653811437692)

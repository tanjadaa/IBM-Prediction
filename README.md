# IBM-Prediction

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/IBM%20Cloud%20Pak.png)


# Data Cleaning Process

Look at your data
To easily find and fix anomalies in your data, click Refine to open the Data Refinery tool. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/dataset.png)

Data Refinery automatically profiles your data to summarize statistics and characteristics of each column. Your first task is to cleanse a column that has multiple strings that mean the same thing. The profile makes it easy to find that anomaly. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/finding%20duplicates.png)

Find a problem
Look at the values in the CREDIT_HISTORY column. Two of the values, "A-Excellent" and "A" have the same meaning. You'll fix this anomaly in the next steps. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/replace%20substring.png)


View your options
With the CREDIT_HISTORY column selected, click Operation to see what you can do to that column. 



Select the Replace substring operation
To replace the string "A-Excellent" with "A", select the Replace substring operation from the Cleanse category. 
The string to replace
The string that you want to replace is "A-Excellent".
The replacement string
The replacement string is "A". 

Now all instances of "A-Excellent" should be replaced with "A". To make sure, check the Profile tab. 

There's one consistent string that means "A" in the CREDIT_HISTORY column. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/removed%20duplicates.png)

Select a column to display
First, look at the distribution of customers across five credit history categories. 

Select the CREDIT_HISTORY column. 

# Visualizing the Data
Select a bar chart
The chart types with blue dots next to their names best fit the data. To see the credit history data in a bar chart, click Bar. 

Look at the distribution
This chart shows the number of customers for each credit history category, from A - E. Most customers are in Category A, which represents the best credit history. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/credit%20history%20bar%20chart.png)

Compare credit categories to missed payments
To show how many customers missed and didn't miss payments for each credit history category, use the Split by function. 

Select MISSED_PAYMENT from the menu. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/split%20by%20missed%20payments.png)

Show only missed payments
Each bar now has two colors: one for how many customers missed payments and one for how many customers didn't miss payments. 

Click Paid to hide the number of customers who paid or didn't miss their payments. Then click next. 

Look at the distribution
You can see that most customers who miss payments are in the the credit history category E. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/category%20E%20highest.png)

🙌🏻  By cleanng and visualizing the data we have discovred the relationship between missed payments and credit history in the data refinery.

# Prediction

Next I started with AutoAI to automatically generate multiple candidate models. ###### Then I deploy the model on data in real-time, as data was received by a web service.

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/RM%20full.png)

AutoAI applies various algorithms, or estimator, to analyze,clean and prepare the raw data for Machine Learning. It automatically detects and categorizes features based on data type, such as categorical or numerical. 

Depending on the categorization, it uses hyper-parameter optimization to determine the best combination of strategies for missing value imputation, feature encoding and feature scaling for your data.

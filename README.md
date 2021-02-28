# IBM Payment Plan Prediction

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/IBM%20Cloud%20Pak.png)

The Utilities Company wants to help their customers avoid missing any payments. The accounts department plans to offer payment plan options to customers who are likely to miss a payment. However, with their existing customer insight tools, the accounts department can identify only 10% of customers who will miss a payment.  Used that data to help predict a higher percentage of customers who are most likely to miss their payments, and how to offer them payment plans.

## Data Cleaning Process

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

## Visualizing the Data
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

## Prediction

Next I started with AutoAI to automatically generate multiple candidate models. ###### Then I deploy the model on data in real-time, as data was received by a web service.

### ABOUT AutoAI - DATA PRE_PROCESSING

AutoAI applies various algorithms, or estimator, to analyze,clean and prepare the raw data for Machine Learning. It automatically detects and categorizes features based on data type, such as categorical or numerical. Depending on the categorization, it uses hyper-parameter optimization to determine the best combination of strategies for missing value imputation, feature encding and feature scaling for the data.
![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/Relationship%20Map.png)

### AUTOMATED MODEL SELECTION

The next step AutoAI automated model selection that matches the data, AutoAI uses a novel approcah that enables testing and ranking candidate algorithms against small subsets of the data, graudally increasing the size of the subset for the most promising algorithms to arrive at the best match. This approach saves time without sacrifising performance. IT enables ranking a large number of candidate algorithms and selecting the best match for the data.

Through our Progress Map, we are able to see the stages of the data and after Model Selection, our data is being split into 2 different Classifiers, XGB Classifier and LGBM Classifier. 

👉🏻 The XGB Classifier, XBGBoost, is an optimized gradient boosting machine learning library. It boosts algorithms through parallel processing, tree-pruning, handling missing values and regularization to avoid overfitting/bias.

👉🏻 The LGBM Classifier, also called LightGBM is a fast, gradient boosting framework that uses tree based learning algorithms. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/progress%20map.png)

Further, throught each algorithm the data set goes through 'Enhancements' including:

  👉🏻 FEATURE ENGINEERING
  
   ▪️ Feature engineering attempts to transform the raw data into the combinatopn of features that best represents the problem to achieve the most accurate prediction. AutoAI uses a unique approach that explores various feature construction choices in a structured, non-exhaustive manner, while progressively maximizing model accuracy using reinforcement learning. This results in an optimized sequence of transofrmations for the data that best match the algorithms of the model selection step.
        
  👉🏻 HYPERPARAMETER OPTIMIZATION
        
   ▪️ A Hyper-Parameter Optimization set refines the best performing model pipelines. AutoAI uses a novel hyper-parameter optimization algorithm optimized for costly function evaluations such as model training and scoring that are typical in machine learning. This approach enales fast convergence to a good solution despite long evaluation times of each iteration.
      

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/RM%20full.png)






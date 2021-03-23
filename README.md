# IBM Payment Plan Prediction

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/IBM%20Cloud%20Pak.png)

From IBM's Cloud Pak site, I have used a sample dataset to address the following scenario: 

The Utilities Company wants to help their customers avoid missing any payments. The accounts department plans to offer payment plan options to customers who are likely to miss a payment. However, with their existing customer insight tools, the accounts department can identify only 10% of customers who will miss a payment.  Used that data to help predict a higher percentage of customers who are most likely to miss their payments, and how to offer them payment plans.

## Data Cleaning Process

First step was to examine the dataset and to easily find and fix anomalies in the data, I used the "Refine" option to open the "Data Refinery tool"

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/dataset.png)

Data Refinery automatically profiles the data to summarize statistics and characteristics of each column. The first task was to cleanse any duplicated in the columns. With the "profile" tab, this makes it easy to find any anomalies. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/finding%20duplicates.png)

Here there are duplicate values in the CREDIT_HISTORY column, "A-Excellent" and "A".

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/replace%20substring.png)

With the CREDIT_HISTORY column selected, duplicates were handled by replacing the substring operation.

Then all instances of "A-Excellent" were replaced with "A". 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/removed%20duplicates.png)
 

## Visualizing the Data

To visualize the distribution I used a bar chart to show the number of customers for each credit history category from A - E. Most customers are in Category A, which represents the best credit history. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/credit%20history%20bar%20chart.png)

To compare credit categories to missed payments I used the Split by function and selected MISSED_PAYMENT from the menu. This displays how many customers missed and didn't miss payments for each credit history category.

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/split%20by%20missed%20payments.png)


Each bar now has two colors: one for how many customers missed payments and one for how many customers didn't miss payments. 

To show only missed payments, "Paid" was deselected to hide the number of customers who paid or didn't miss their payments.


_We can see by the distribution that most customers who miss payments are in the the credit history category E. _

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/category%20E%20highest.png)

🙌🏻 By cleanng and visualizing the data we have discovred the relationship between missed payments and credit history in the data refinery.

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
   
## Results

The 3 Feature Transformers which were applied are Sum, Round and Univariate Feature Selection.

With the Pipeline Leaderboard, Pipeline 4 has a 94.3% accuracy rate and has been deemed the "Top Performer" by the blue star. 

Pipeline 4 uses the combination of: 

   ▪️ XGB Classifier 
   
   ▪️ Hyperparameter optimization (1st)
   
   ▪️ Feature Engineering
   
   ▪️ Hyperparameter optimization (2nd) 
   

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/RM%20full.png)
![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/Pipeline%20Leadership.png)

### Model Evaluation
This Model evaluation shows the model accuracy which allows us to see the accuracy of the pipeline, in this pipeline 4.

The higher the score, the better the model is at predicting and distinguishing between customers who miss their payments and customers who don't.

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/Model%20Evaluation.png)

### Confusion Matrix
The confusion matrix shows numbers and percentages of correct and incorrect classifications.

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/Confusion%20Matrix.png)

### Feature Importance

This shows the relative importance of each feature in predicting the target, based on an averaging of nine different importance measures.

This pipeline is more balanced as it uses two columns as the most important predictors: Overdue_Balance and Credit_History. 

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/Feature%20Importance.png)

### Precision Recall Curve

The Precision vs. Recall Curve chart plots the proportion of outcomes predicted to be positive that are positive, also known as precision, on the vertical axis, against the proportion of positive outcomes that are correctly predicted, also known as recall, sensitivity, probability of detection or true positive rate (TPR), on the horizontal axis, as the threshold for positive classification is varied across the predicted probability range from 1 down to 0. When the threshold is set high, few false positives will occur and precision will be high, while recall will be low. As the threshold is decreased, recall will increase and precision will generally decrease. Although there is generally a trade off between precision and recall, the curve may not be strictly monotonically decreasing. The area under the Prevision vs. Recall curve is generally preferred to the area under the ROC curve as an evaluation statistic for binary classification when the proportions of positive and negative observed instances are highly imbalanced.

![image](https://github.com/tanjadaa/IBM-Prediction/blob/main/Pictures/Precision%20Recall%20Curve.png)


## Conclusion

As a conclusion, we see that utilizing the XGB Classifer along with both the 1st and the 2nd Hyperparameter optimization and Feature Engineering yields the highest precision rate of 94.3% for particular dataset prediction.











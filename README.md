# Prediction of Plate Type from cars being ticketed in NYC 

The NYC Department of Finance collects data on every parking ticket issued in NYC (approximately 10 million per year). This data is made publicly available to aid ticket resolution and guide policymakers. Four files, covering August 2013 to June 2017, are roughly organized by fiscal year (July 1 - June 30). Columns include information about the vehicle ticketed, the ticket issued, location, and time. I would focus on the file in 2015, as the data size is more than 2.7 gigabytes, the largest among all the files. This was an excellent opportunity for me to practice handling big data by Apache Spark other than using R or Pandas. 

How to deal with the data?

I utilized the MLlib in the package PySpark for building machine learning models, whereas, for data preprocessing, the package Pandas was used. The data preprocessing steps include breaking down date-related variables into the year, hour, and minute variables to include more information, removing noninformative attributes, having more than 30% missing values, and having near-zero variance or those that were correlated. For the imputation of the missing values, I performed the multivariate feature imputation method. Depending on the characteristics and the number of classes, both one-hot encoding and label encoding were used for the encoding scheme.

What problem was solved?

This project aimed to forecast the plate type of cars being ticketed in New York City. I performed common machine learning models using MLlib, which stands for Spark's machine learning (ML) library, including Naïve Bayes, logistic regression, random forest, and decision trees. To search for the best model, hyperparameter tuning was utilized in the 5-fold cross-validation. Since there were more than 70 plate types in the data set, I selected the ROC AUC to choose the best approach among the four candidates.

What was the result?

The result indicated that decision trees beat other defendants, with the area under the ROC reaching 0.61 and accuracy reaching 0.75, suggesting that it has a good measure of separability among different cases. The random forest and logistic regression have good prediction capacity as well. In contrast, the Naïve Bayes is not a good choice, indicating that overall, most data preprocessing actions assist models in training. The disadvantage of the Naïve Bayes is that it assumes each feature makes an independent and equal contribution to the outcome. However, judging from the forecast result, this condition is not met in our case because some variables may be more dominant in foretelling the plate type of cars being ticketed in New York City. Besides, tree-based methods do not require normalization or scaling of data. Therefore, they perform well even though many one-hot encoded attributes and attributes have wide ranges in this data set.

What did you learn?

One benefit of Spark is that it allows parallel operation on my computer to execute the program simultaneously. Even with about 4 GB of training data, PySpark enables me to conduct any model tuning faster than using the scikit-learn in Python or caret in R. Yet, the downside of PySpark is that the methods available for multiclass are insufficient. If more approaches are offered, we may find a better one that outperforms the decision trees, such as XGBoost, as AUC can be further increased.

How to improve?

Due to the limit of my hardware, it took me several hours to tune the hyperparameters and do the cross-validation. The next step would be to adjust more hyperparameters by the random search function and conduct the 10-fold cross-validation to acquire a more robust result. To expedite the speed of execution, cloud computing resources can help us.

Appendix

[NYC Parking Tickets](https://www.kaggle.com/new-york-city/nyc-parking-tickets)

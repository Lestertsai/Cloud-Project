# Prediction of Plate Type from cars being ticketed in NYC 

Motivation

Apache Spark is one of the great tools to expedite the speed of big data analysis. Also, one advantage of utilizing Spark is that Spark SQL provides a domain-specific language to manipulate data frames in Python, which I'm using a lot. Hence, it is easy to get along without spending time learning another new language.
 
How to deal with the data?

I utilized the MLlib in the package PySpark for building machine learning models, whereas, for data preprocessing, the package Pandas was used. The data preprocessing steps include breaking down date-related variables into the year, hour, and minute variables to include more information, removing noninformative attributes, having more than 30% missing values, and having near-zero variance or those that were correlated. For the imputation of the missing values, I performed the multivariate feature imputation method. Depending on the characteristics and the number of classes, both one-hot encoding and label encoding were used for the encoding scheme.  
 
What problem was solved?

This project aimed to forecast the plate type of cars being ticketed in New York City. We performed common machine learning models using MLlib, which stands for Spark's machine learning (ML) library, including Naïve Bayes, logistic regression, random forest, and decision trees. To search for the best model, hyperparameter tuning was utilized in the 5-fold cross-validation. Since there were more than 70 plate types in the data set, I selected the ROC AUC to choose the best approach among the four candidates. 
 
What is the result?

The result indicated that decision trees beat other defendants, with the area under the ROC reaching 0.61 and accuracy reaching 0.75, suggesting that it has a good measure of separability among different cases. The random forest and logistic regression have good prediction capacity as well. In contrast, the Naïve Bayes is not a good choice, indicating that most data preprocessing actions assist models in training. The disadvantage of the Naïve Bayes is that it assumes each feature makes an independent and equal contribution to the outcome. However, judging from the forecast result, this condition is not met in our case because some variables may be more dominant in foretelling the plate type of cars being ticketed in New York City. Besides, normalization or scaling of data is not required in the tree-based methods. This is why they perform well even though many one-hot encoded attributes and attributes have wide ranges.
 
What did you learn?

One benefit of Spark is that it allows parallel operation on my computer to execute the program simultaneously. Even with about 4 GB of training data, PySpark enables me to conduct any model tuning faster than using the sikit-learn in Python or caret in R. Yet, the downside of PySpark is that the methods available for multiclass are insufficient. If more approaches are offered, we may find a better one that outperforms the decision trees, such as XGBoost, as AUC can be further increased.
 
How to improve?
 
Due to the limit of my hardware, it took me several hours to tune the hyperparameters and do the cross-validation. The next step would be to adjust more hyperparameters by the random search function and conduct the 10-fold cross-validation to acquire a more robust result. To expedite the speed of execution, cloud computing resources can help us.


Appendix

[NYC Parking Tickets](https://www.kaggle.com/new-york-city/nyc-parking-tickets)

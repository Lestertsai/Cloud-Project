NYC Parking Tickets Issued States Prediction

Motivation

This was a school project where students were required to analyze data either using cloud computing resources or any other tools that could facilitate the speed of processing. We chose Apache Spark as the analytics engine to expedite the data processing other than using R, a language I&#39;m more familiar with but is slower when dealing with data on a large scale. Also, one advantage of utilizing Spark is that Spark SQL provides a domain-specific language to manipulate dataframes in Python which I&#39;m using a lot. Hence, it is easy to get along without spending time learning another new language.

Why builds this project?

Nowadays, the two popular platforms for finding datasets are [Kaggle](https://www.kaggle.com/datasets) and [UCI machine learning repository](https://archive.ics.uci.edu/ml/datasets.php). Though the latter does contain valuable data with interesting questions, we could not preview the distribution or the types of the attributes before downloading the data. Since these factors would heavily impact the quality of prediction and the result of the analysis, it is tedious to examine these details especially when the dataset has hundreds or even thousands of features. Thus, thanks to the preview function of the dataset in Kaggle, it facilitates us in discovering the proper dataset which has no near-variability attribute and other downsides that might negatively affect the result of the analysis. Besides, as my teammates and I have not studied the related field before, we are all interested in playing the data which contains different kinds of variables and millions of cases each year.

How to deal with the data?

To allow more data to be processed at once, I changed the configuration of Spark beforehand. Then, I perform data preprocessing to raise the quality of prediction, which includes

1. Brokedown date-related variables into the year, hour, and minute variables to include more information.
2. Transformed string features into numeric features.
3. Removed attributes having more than 30% missing values.
4. Though this is not recommended, considering that the dataset had more than 4 million cases, we decided to randomly sample half of the dataset to speed up the processing time in case of my computer shut down.
5. Converted categorical variables to dummy variables.
6. Standardized all the features to minimize the impact of different scales among them.

What problem was solved?

The goal of this project was to predict the registration of the States of the cars that have been issued tickets in New York City. We performed multinomial logistic regression using MLlib, which stands for Spark&#39;s machine learning (ML) library. The result indicated that our model had AUC reaching 0.78, which means it has a good measure of separability among different cases. We also performed cross-validation to optimize the hyperparameters of the model.

What did you learn?

One benefit of Spark is that it allows parallel operation on my computer to execute the program simultaneously. This is where R could not outperform Spark when coping with data on a large scale. Yet, the methods for Classification and Regression on Spark are fewer than that on the R package, such as caret. Therefore, it is wise to use R or even Python when comparing different machine learning methods is our aim. Otherwise, if speed is the only consideration, Spark would be the first choice.

How to improve?

When using Spark, pipeline is the process of wrapping each combination of data preprocessing steps to avoid hundreds of messy codes that is difficult to manage. Pipelines enable users to construct sequences of stages to control the machine learning workflow effectively. Due to the limited time we have during the course, this is one useful feature we did not implement in our project. Besides, while the logistic model we performed seems good enough, trying other approaches as well could also improve our understanding of them and figure out whether their performances on the dataset are better than the one we have.

Appendix

[NYC Parking Tickets](https://www.kaggle.com/new-york-city/nyc-parking-tickets)

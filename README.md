# Anomaly-Detection
This repo depicts the techniques I have tried to detect anamolies in a dataset .

# Contributing for Hacktoberfest 2020
To contribute to this repo:

Star it
Fork the repo
Clone it onto your PC.
Create a folder with your github username
Create seperate files for all the issues you are solving and always open an issue which has all details of the process or method you will use to perform anomaly detection and wait till its is assigned (not more than 2-3 hours it will take , we are passionate open source developers )
Open PRs for the issues you are solving. (You can open multiple PRs for different issues by branching).

## Data description :

## Predict Financial crisis 

Given certain parameters related to financial performance of companies. I wanted to detect the companies suffering financial distress by using unsupervised method and then will later compare the labels to check performance of the algorithm.

## Data Dictionary:

First column: Company represents sample companies.

Second column: Time shows different time periods that data belongs to. Time series length varies between 1 to 14 for each company.

Third column: The target variable is denoted by "Financial crisis" where 0 is healthy (0). and 1 is financially unstable (1). 

Fourth column to the last column: The features denoted by x1 to x83, are some financial and non-financial characteristics of the sampled companies. These features belong to the previous time period, which should be used to predict whether the company will be financially distressed or not (classification). Feature x80 is a categorical variable.

For example, company 1 is financially distressed at time 4 but company 2 is still healthy at time 14.

## Approach for detecting Anomalies in dataset

Detecting anomalies is quite important as it can affect your analysis .

## Approach -I 

I started with trying many different algorithm like :

Angle-based Outlier Detector (ABOD)

Cluster-based Local Outlier Factor (CBLOF)

Feature Bagging

Histogram-base Outlier Detection (HBOS)

Isolation Forest

K Nearest Neighbors (KNN)

Average KNN

Out of which **Isolation Forest** gave better results so I thought to use Isolation Forest and further do hyperparameter tuning to it .

## Approach -II

I had approx 3.7% of anomalies in my dataset , I tried using Isolation forest and by tuning it parameter I got about 45 % of recall score .Remember as we have only 3.7% of data which is anomaly so accuracy is not at all a good metric to judge our algorithm so we need to measure performance using confusion metric , recall score or F1 score.

## How Isolation Forests Work

The Isolation Forest algorithm isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature. The logic argument goes: isolating anomaly observations is easier because only a few conditions are needed to separate those cases from the normal observations. On the other hand, isolating normal observations require more conditions. Therefore, an anomaly score can be calculated as the number of conditions required to separate a given observation.

## Approach -III

Autoencoder in deeplearning is mostly used to get rid of redundant data but one more of it's use case is to detect anomaly
I choose Autoencoders, which is a deep learning, unsupervised ML algorithm. "Autoencoding" is a data compression algorithm, which takes the input and going through a compressed representation and gives the reconstructed output.

I have used H2O library to make the autoencoder and I got about 83% of recall score.



## How does autoencoder help us in detecting outliers?

From train set we have removed distressed data or points with 1 as target.But in testing set has both normal and distress transactions in it. The Autoencoder will learn to identify the pattern of the input data. If an anomalous test point does not match the learned pattern, the autoencoder will likely have a high error rate in reconstructing this data, indicating anomalous data. So that we can identify the anomalies of the data. To calculate the error, it uses Mean Squared Error(MSE)








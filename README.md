Problem statement:
In a highly competitive and distressed European market, how does a bank compete succesfully for new clients when mass marketing is too costly to its already thin margins.

Business Objective:
Use the data collected and business intelligence to build a predictive model in targeting potential clients through direct marketing campaings aimed at offering long term deposit applications with good interest rates.

This project aims to use the CRISP-DM model of data mining and analytics to dig into European banking direct marketing data for successfull attempts at getting cliets to subscribe to "long term deposit with good itnerest rates" campaign.
The end result will be a highly accurate predictive model to determine drivers for successfull subscriptions.

During the first phase of the project I analyzed, cleansed, and encoded the data.
Analyzing descriptive statistic helped us to identify which data items I would need to scale and/or transform.

Below is a statistical summary of our data:

    	age	        duration	    campaign	    pdays	        previous	    emp.var.rate	  cons.price.idx	cons.conf.idx	euribor3m	    nr.employed	  contacted_before
count	41188.00000	41188.000000	41188.000000	41188.000000	41188.000000	41188.000000	  41188.000000	  41188.000000	41188.000000	41188.000000  41188.000000
mean	40.02406	  258.285010	  2.567593	    0.221229	    0.172963	    0.081886	      93.575664	      -40.502600	  3.621291	    5167.035911	  0.036783
std	  10.42125	  259.279249	  2.770014	    1.348874	    0.494901	    1.570960	      0.578840	      4.628198	    1.734447	    72.251528	    0.188230
min	  17.00000	  0.000000	    1.000000	    0.000000	    0.000000	    -3.400000	      92.201000	      -50.800000	  0.634000	    4963.600000	  0.000000
25%	  32.00000	  102.000000	  1.000000	    0.000000	    0.000000	    -1.800000	      93.075000	      -42.700000	  1.344000	    5099.100000	  0.000000
50%	  38.00000	  180.000000	  2.000000	    0.000000	    0.000000	    1.100000	      93.749000	      -41.800000	  4.857000	    5191.000000	  0.000000
75%	  47.00000	  319.000000	  3.000000	    0.000000	    0.000000	    1.400000	      93.994000	      -36.400000	  4.961000	    5228.100000	  0.000000
max	  98.00000	  4918.000000	  56.000000	    27.000000	    7.000000	    1.400000	      94.767000	      -26.900000	  5.045000	    5228.100000	  1.0000000

I also determined that some binary categorical data would need to be transformed/encoded into and integer in order for our models to classify them correctly.

After fearture engineering I split the data set into a train and test set. 

After splitting the data I fit a baseline model with a dummy classifier so we would have something to meaure our other models against. The baseline achieved an accuracy of 0.8874

I then created a simple Logistic regresssion model and received an Accuracy score of  : 0.9098.

I then employed KNN, Decision Tree, and SVM models to determine if they were better models for predicting successful deposit subscriptions. 
A summary of the model scores and computing resources (i.e. processing time) are below
                            Train Accuracy  Test Accuracy  ROC AUC  Fit Time (s)
      Model                                                                    
      Logistic Regression          0.9083         0.9098   0.9349        0.1105
      KNN                          0.9288         0.9033   0.8690        0.0240
      Decision Tree                1.0000         0.8908   0.7385        0.0787
      SVM                          0.9076         0.9107   0.9041       32.4843

Overall I believe SVM performed the best however it took the most resources and the longest time to fit.  There are also constraints on the amount of data SVM models can handle.  My next choice would be to employ a Logistic regression model.


Next randomly adjusted several hyperparameters on each model to improve the score.  The results are below:

                     Train Accuracy  Test Accuracy  ROC AUC  Fit Time (s)
Model                                                                    
Logistic Regression          0.9083         0.9102   0.9350        2.1958
KNN                          1.0000         0.9088   0.9209        8.6222
Decision Tree                0.9187         0.9176   0.9405        3.8600
SVM                          0.8988         0.9002   0.9336      556.9222

Logistic regression actually got worst and SVM time to complete increase substantially.

KNN now appears to be the best model.  To prove this I ran 

Lastly, I conducted a best params code to determine the best hyperparameters of each model.

=== Best Hyperparameters ===

Logistic Regression:
  C: 100
  penalty: l2
  solver: liblinear

KNN:
  metric: euclidean
  n_neighbors: 21
  weights: distance

Decision Tree:
  criterion: entropy
  max_depth: 7
  min_samples_leaf: 1
  min_samples_split: 10

SVM:
  C: 1
  gamma: scale
  kernel: linear


      

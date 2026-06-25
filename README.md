Problem statement:
In a highly competitive and distressed European market, how does a bank compete succesfully for new clients when mass marketing is too costly to its already thin margins.

Business Objective:
Use the data collected and business intelligence to build a predictive model in targeting potential clients through direct marketing campaings aimed at offering long term deposit applications with good interest rates.

This project aims to use the CRISP-DM model of data mining and analytics to dig into European banking direct marketing data for successfull attempts at getting cliets to subscribe to "long term deposit with good itnerest rates" campaign.
The end result will be a highly accurate predictive model to determine drivers for successfull subscriptions.

During the first phase of the project I analyzed, cleansed, and encoded the data.
Analyzing descriptive statistic helped us to identify which data items I would need to scale and/or transform.

Below is a statistical summary of our data:

<img width="1072" height="288" alt="image" src="https://github.com/user-attachments/assets/bf78986f-6f49-473f-ac46-401e661c7142" />

I also determined that some binary categorical data would need to be transformed/encoded into and integer in order for our models to classify them correctly.

After fearture engineering I split the data set into a train and test set. 

After splitting the data I fit a baseline model with a dummy classifier so we would have something to meaure our other models against. The baseline achieved an accuracy of 0.8874

I then created a simple Logistic regresssion model and received an Accuracy score of  : 0.9098.

I then employed KNN, Decision Tree, and SVM models to determine if they were better models for predicting successful deposit subscriptions. 
A summary of the model scores and computing resources (i.e. processing time) are below

<img width="644" height="128" alt="image" src="https://github.com/user-attachments/assets/a352c51e-77ff-4a86-90fd-37c4b14d5135" />

                            
  

Overall I believe SVM performed the best however it took the most resources and the longest time to fit.  There are also constraints on the amount of data SVM models can handle.  My next choice would be to employ a Logistic regression model.


Next randomly adjusted several hyperparameters on each model to improve the score.  The results are below:

<img width="611" height="120" alt="image" src="https://github.com/user-attachments/assets/5c0626f7-1501-4311-9550-e08ebb2b59e7" />


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

<img width="818" height="597" alt="image" src="https://github.com/user-attachments/assets/a51e4529-0d49-47a2-a136-294152c412e8" />

Next steps would be to collect new real world data to test our models and to further improve the score.



As for now I wouild recommend that the banks target people that have features with a strong correlation with the highest predictor being call duration.  Features like being employed, Retired/Management, and prior subcribers.




<img width="1043" height="584" alt="image" src="https://github.com/user-attachments/assets/ca3a5f84-7769-47f3-84c7-dc8a25cc369e" />

